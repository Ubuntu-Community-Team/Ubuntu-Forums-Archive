---
title: "Help required while installing ubuntu-10.04-desktop-i386"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by kajal on 2010-05-25
I have executed follwoing steps  :
 
1) download  ubuntu-10.04-desktop-i386 via bittorrent 
2) burn CD 
3) after execute wubi.exe from cd .
4) install it via install inside window 
 
I am getting permission denied error while installing ubuntu via "install inside window"
 
05-25 21:34 INFO   Distro: Found a valid CD for Ubuntu: E:\
05-25 21:34 INFO   root: Running the installer...
05-25 21:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kajal\AppData\Local\Temp\pyl7D69.tmp\translations, languages=['en_IN', 'en']
05-25 21:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kajal\AppData\Local\Temp\pyl7D69.tmp\translations, languages=['en_IN', 'en']
05-25 21:34 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=kajal
05-25 21:34 INFO   root: Received settings
05-25 21:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kajal\AppData\Local\Temp\pyl7D69.tmp\translations, languages=['en_US', 'en']
05-25 21:34 DEBUG  TaskList: # Running tasklist...
05-25 21:34 DEBUG  TaskList: ## Running select_target_dir...
05-25 21:34 INFO   WindowsBackend: Installing into C:\ubuntu
05-25 21:34 DEBUG  TaskList: ## Finished select_target_dir
05-25 21:34 DEBUG  TaskList: ## Running create_dir_structure...
05-25 21:34 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-25 21:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-25 21:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-25 21:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-25 21:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-25 21:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-25 21:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-25 21:34 DEBUG  TaskList: ## Finished create_dir_structure
05-25 21:34 DEBUG  TaskList: ## Running uncompress_target_dir...
05-25 21:34 DEBUG  TaskList: ## Finished uncompress_target_dir
05-25 21:34 DEBUG  TaskList: ## Running create_uninstaller...
05-25 21:34 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-25 21:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-25 21:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-25 21:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-25 21:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-25 21:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-25 21:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-25 21:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-25 21:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-25 21:34 DEBUG  TaskList: ## Finished create_uninstaller
05-25 21:34 DEBUG  TaskList: ## Running copy_installation_files...
05-25 21:34 DEBUG  WindowsBackend: Copying C:\Users\kajal\AppData\Local\Temp\pyl7D69.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-25 21:34 DEBUG  WindowsBackend: Copying C:\Users\kajal\AppData\Local\Temp\pyl7D69.tmp\winboot -> C:\ubuntu\winboot
05-25 21:34 DEBUG  WindowsBackend: Copying C:\Users\kajal\AppData\Local\Temp\pyl7D69.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-25 21:34 DEBUG  TaskList: ## Finished copy_installation_files
05-25 21:34 DEBUG  TaskList: ## Running get_iso...
05-25 21:34 DEBUG  TaskList: New task copy_file
05-25 21:34 DEBUG  TaskList: ### Running copy_file...
05-25 21:44 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
05-25 21:44 DEBUG  TaskList: # Cancelling tasklist
05-25 21:44 DEBUG  TaskList: New task check_iso
05-25 21:44 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
05-25 21:44 DEBUG  CommonBackend: Searching for local ISO
05-25 21:44 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-25 21:44 DEBUG  TaskList: New task get_metalink
05-25 21:44 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-25 21:44 DEBUG  TaskList: # Cancelling tasklist
05-25 21:44 DEBUG  TaskList: # Finished tasklist

---

### Post by dino99 on 2010-05-25
why not a real install or with virtualbox instead of this outdated method ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by rob45 on 2010-05-26
If you are using a firewall make sure you unload it ....shut it down...before installing using wubi.
Wubi works fine.

---

