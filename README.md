# NoOneDrive

🌐 **Language:** [English](#english) | [Русский](#русский)

---

<a name="english"></a>
## 🇬🇧 English

A lightweight, native utility for **Windows 10 / 11** that completely removes **Microsoft OneDrive** while safely preserving all user files and restoring standard Windows shell folders.

### Safety Guarantees

- **Your local files are safe:** Before removing OneDrive, the tool automatically moves all local files and folders back to `%USERPROFILE%\Desktop`, `Documents`, `Pictures`, `Music`, and `Videos` (custom folders are placed in `Documents\OneDrive_Local`). File locks are gracefully closed via Windows Restart Manager.
- **Cloud-only files are untouched:** OneDrive online-only placeholders are skipped during file migration—your cloud data stays intact in your Microsoft account.
- **Windows stays intact:** Restores `User Shell Folders`, `Shell Folders`, Known Folder API paths, and localized folder icons (`desktop.ini`), then cleanly restarts `explorer.exe`.

### What It Does (5-Stage Pipeline)

1. **Processes & Service:** Stops OneDrive processes (`OneDrive.exe`, `FileCoAuth.exe`, updaters) and removes `OneDrive Updater Service`.
2. **User Files:** Unregisters Cloud Filter sync roots (`CfUnregisterSyncRoot`) and safely migrates local files back to standard user folders.
3. **Client Removal:** Uninstalls Per-User / Per-Machine `OneDriveSetup.exe`, Store Appx packages (via WinRT `PackageManager`), and Provisioned packages (`dism.exe`).
4. **Shell & Icons:** Removes OneDrive folder GUID overrides and restores default Windows library paths and icons.
5. **Policies & Cleanup:** Sets `DisableFileSyncNGSC = 1` to prevent reinstallation, unpins OneDrive from Explorer, removes startup entries (including `Default\NTUSER.DAT`), scheduled tasks, shortcuts, environment variables, registry traces, and leftover folders.

### Features

- **Scan-first workflow:** Inspects the system and previews everything before making any changes.
- **Pure Win32 / COM / WinRT APIs:** No `cmd.exe` or `powershell.exe` wrappers.
- **Defender Exclusion Toggle:** Built-in button to add/remove the app from Windows Defender exclusions via native WMI.
- **Multi-language UI:** Automatically adapts to English, Russian, and Ukrainian system locales.

### Requirements & Download

- **OS:** Windows 10 / Windows 11 (Administrator privileges required).
- **Download:** Grab the latest `NoOneDrive.exe` from the [Releases](../../releases) page and run it as Administrator.

---

<a name="русский"></a>
## 🇷🇺 Русский

Лёгкая нативная утилита для **Windows 10 / 11**, которая полностью удаляет **Microsoft OneDrive**, бережно сохраняя файлы пользователя и восстанавливая стандартную структуру папок Windows.

### Безопасность для системы и данных

- **Локальные файлы не теряются:** Перед удалением программа автоматически переносит все локальные файлы и папки из OneDrive обратно в `%USERPROFILE%\Desktop`, `Documents`, `Pictures`, `Music` и `Videos` (нестандартные папки переносятся в `Documents\OneDrive_Local`). Блокировки файлов корректно снимаются через Windows Restart Manager.
- **Облачные файлы не затрагиваются:** Файлы-заглушки («Только в облаке») пропускаются — они остаются в безопасности в вашем аккаунте Microsoft на `onedrive.live.com`.
- **Windows работает стабильно:** Программа восстанавливает пути `User Shell Folders` / `Shell Folders`, системные Known Folders и локализованные иконки папок (`desktop.ini`), после чего аккуратно перезапускает Проводник (`explorer.exe`).

### Как работает (5 этапов)

1. **Процессы и служба:** Останавливает процессы OneDrive и удаляет службу `OneDrive Updater Service`.
2. **Файлы пользователя:** Отвязывает корень синхронизации (`CfUnregisterSyncRoot`) и переносит локальные данные в стандартные каталоги пользователя.
3. **Удаление клиента:** Запускает штатную деинсталляцию `OneDriveSetup.exe`, удаляет Store-пакеты (через WinRT `PackageManager`) и Provisioned-пакеты (`dism.exe`).
4. **Shell и иконки:** Очищает переопределения OneDrive GUID и возвращает стандартные пути и значки папок.
5. **Политики и следы:** Включает политику `DisableFileSyncNGSC = 1` против повторной установки, убирает значок из Проводника, очищает автозапуск (включая профиль `Default\NTUSER.DAT`), задачи планировщика, ярлыки, переменные среды, ветки реестра и остаточные папки.

### Особенности

- **Предварительное сканирование:** Сначала проверяет систему и показывает отчёт, ничего не меняя без подтверждения.
- **Прямые Win32 / COM / WinRT вызовы:** Без `cmd.exe` и `powershell.exe`.
- **Исключения Defender:** Встроенная кнопка добавления/удаления программы в исключения Windows Defender через WMI.
- **Локализация:** Автоматическое переключение интерфейса на русский, украинский или английский язык.

### Запуск и скачивание

- **ОС:** Windows 10 / Windows 11 (требуются права администратора).
- **Скачивание:** Загрузите актуальную версию `NoOneDrive.exe` со страницы [Releases](../../releases) и запустите от имени администратора.
