---
title: "Need help with Windows 7 Permission Denied error when installing Ubutu 10.10 Desktop"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by dmax1989 on 2011-02-04
Attempting to install Ubuntu 10.10 on a Dell 6410 with Windows 7 Pro.  Just  before completing install Ubuntu Installer displays the following..

An error occured:

Permission denied

For more information, Please see the log file:
Wubi-10.10-rev197.log

Any suggestions is appreciated.:confused:

---

### Post by Rhizoid on 2011-02-04
Did you run Wubi.exe as admin in Win7?

---

### Post by dmax1989 on 2011-02-04
No, I do have admin rights.

---

### Post by Rubi1200 on 2011-02-05
Hi and welcome to the forums dmax1989 :-)

Two things to try:

1. place the wubi.exe and ISO in the same folder and then try running it
2. post the contents of the logfile; new post > post contents > highlight all text > click on # in the toolbar > submit

Thanks.

---

### Post by dmax1989 on 2011-02-05
02-04 23:41 INFO   root: === wubi 10.10 rev197 ===
02-04 23:41 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.10-rev197.log
02-04 23:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
02-04 23:41 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\data
02-04 23:41 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\bin\7z.exe
02-04 23:41 DEBUG  CommonBackend: Fetching basic info...
02-04 23:41 DEBUG  CommonBackend: original_exe=D:\wubi.exe
02-04 23:41 DEBUG  CommonBackend: platform=win32
02-04 23:41 DEBUG  CommonBackend: osname=nt
02-04 23:41 DEBUG  CommonBackend: language=en_US
02-04 23:41 DEBUG  CommonBackend: encoding=cp1252
02-04 23:41 DEBUG  WindowsBackend: arch=amd64
02-04 23:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\data\isolist.ini
02-04 23:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-04 23:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-04 23:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-04 23:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-04 23:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-04 23:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-04 23:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-04 23:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-04 23:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-04 23:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-04 23:41 DEBUG  WindowsBackend: Fetching host info...
02-04 23:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-04 23:41 DEBUG  WindowsBackend: windows version=vista
02-04 23:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
02-04 23:41 DEBUG  WindowsBackend: windows_sp=None
02-04 23:41 DEBUG  WindowsBackend: windows_build=7600
02-04 23:41 DEBUG  WindowsBackend: gmt=-5
02-04 23:41 DEBUG  WindowsBackend: country=US
02-04 23:41 DEBUG  WindowsBackend: timezone=America/New_York
02-04 23:41 DEBUG  WindowsBackend: windows_username=PLASAdmin
02-04 23:41 DEBUG  WindowsBackend: user_full_name=PLASAdmin
02-04 23:41 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-04 23:41 DEBUG  WindowsBackend: windows_language_code=1033
02-04 23:41 DEBUG  WindowsBackend: windows_language=English
02-04 23:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
02-04 23:41 DEBUG  WindowsBackend: bootloader=vista
02-04 23:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 106536.496094 mb free ntfs)
02-04 23:41 DEBUG  WindowsBackend: drive=Drive(C: hd 106536.496094 mb free ntfs)
02-04 23:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-04 23:41 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-04 23:41 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-04 23:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-04 23:41 DEBUG  WindowsBackend: keyboard_id=67699721
02-04 23:41 DEBUG  WindowsBackend: keyboard_layout=us
02-04 23:41 DEBUG  WindowsBackend: keyboard_variant=
02-04 23:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-04 23:41 DEBUG  CommonBackend: locale=en_US.UTF-8
02-04 23:41 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-04 23:41 DEBUG  CommonBackend: Searching ISOs on USB devices
02-04 23:41 DEBUG  CommonBackend: Searching for local CDs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Ubuntu CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Ubuntu CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Ubuntu Netbook CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Kubuntu CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Kubuntu CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Kubuntu Netbook CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Xubuntu CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Xubuntu CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Mythbuntu CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Mythbuntu CD
02-04 23:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 23:41 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
02-04 23:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
02-04 23:41 INFO   Distro: Found a valid CD for Ubuntu: D:\
02-04 23:41 INFO   root: Running the CD menu...
02-04 23:41 DEBUG  WindowsFrontend: __init__...
02-04 23:41 DEBUG  WindowsFrontend: on_init...
02-04 23:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\translations, languages=['en_US', 'en']
02-04 23:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\translations, languages=['en_US', 'en']
02-04 23:42 INFO   root: CD menu finished
02-04 23:42 INFO   root: Already installed, running the uninstaller...
02-04 23:42 INFO   root: Running the uninstaller...
02-04 23:42 INFO   CommonBackend: This is the uninstaller running
02-04 23:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\translations, languages=['en_US', 'en']
02-04 23:42 INFO   root: Received settings
02-04 23:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\translations, languages=['en_US', 'en']
02-04 23:42 DEBUG  TaskList: # Running tasklist...
02-04 23:42 DEBUG  TaskList: ## Running Backup ISO...
02-04 23:42 DEBUG  TaskList: ## Finished Backup ISO
02-04 23:42 DEBUG  TaskList: ## Running Remove bootloader entry...
02-04 23:42 DEBUG  WindowsBackend: Could not find bcd id
02-04 23:42 DEBUG  WindowsBackend: undo_bootini C:
02-04 23:42 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 106536.496094 mb free ntfs)
02-04 23:42 DEBUG  TaskList: ## Finished Remove bootloader entry
02-04 23:42 DEBUG  TaskList: ## Running Remove target dir...
02-04 23:42 DEBUG  CommonBackend: Deleting C:\ubuntu
02-04 23:42 DEBUG  TaskList: ## Finished Remove target dir
02-04 23:42 DEBUG  TaskList: ## Running Remove registry key...
02-04 23:42 DEBUG  TaskList: ## Finished Remove registry key
02-04 23:42 DEBUG  TaskList: # Finished tasklist
02-04 23:42 INFO   root: Almost finished uninstalling
02-04 23:42 INFO   root: Finished uninstallation
02-04 23:42 DEBUG  CommonBackend: Fetching basic info...
02-04 23:42 DEBUG  CommonBackend: original_exe=D:\wubi.exe
02-04 23:42 DEBUG  CommonBackend: platform=win32
02-04 23:42 DEBUG  CommonBackend: osname=nt
02-04 23:42 DEBUG  WindowsBackend: arch=amd64
02-04 23:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\data\isolist.ini
02-04 23:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-04 23:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-04 23:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-04 23:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-04 23:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-04 23:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-04 23:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-04 23:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-04 23:42 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-04 23:42 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-04 23:42 DEBUG  WindowsBackend: Fetching host info...
02-04 23:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-04 23:42 DEBUG  WindowsBackend: windows version=vista
02-04 23:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Enterprise
02-04 23:42 DEBUG  WindowsBackend: windows_sp=None
02-04 23:42 DEBUG  WindowsBackend: windows_build=7600
02-04 23:42 DEBUG  WindowsBackend: gmt=-5
02-04 23:42 DEBUG  WindowsBackend: country=US
02-04 23:42 DEBUG  WindowsBackend: timezone=America/New_York
02-04 23:42 DEBUG  WindowsBackend: windows_username=PLASAdmin
02-04 23:42 DEBUG  WindowsBackend: user_full_name=PLASAdmin
02-04 23:42 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
02-04 23:42 DEBUG  WindowsBackend: windows_language_code=1033
02-04 23:42 DEBUG  WindowsBackend: windows_language=English
02-04 23:42 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 520  @ 2.40GHz
02-04 23:42 DEBUG  WindowsBackend: bootloader=vista
02-04 23:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 107168.605469 mb free ntfs)
02-04 23:42 DEBUG  WindowsBackend: drive=Drive(C: hd 107168.605469 mb free ntfs)
02-04 23:42 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-04 23:42 DEBUG  WindowsBackend: uninstaller_path=None
02-04 23:42 DEBUG  WindowsBackend: previous_target_dir=None
02-04 23:42 DEBUG  WindowsBackend: previous_distro_name=None
02-04 23:42 DEBUG  WindowsBackend: keyboard_id=67699721
02-04 23:42 DEBUG  WindowsBackend: keyboard_layout=us
02-04 23:42 DEBUG  WindowsBackend: keyboard_variant=
02-04 23:42 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-04 23:42 DEBUG  CommonBackend: Searching ISOs on USB devices
02-04 23:42 DEBUG  CommonBackend: Searching for local CDs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Ubuntu CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Ubuntu CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Ubuntu Netbook CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Kubuntu CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Kubuntu CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Kubuntu Netbook CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Xubuntu CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Xubuntu CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Mythbuntu CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp is a valid Mythbuntu CD
02-04 23:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\casper\filesystem.squashfs
02-04 23:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 23:42 INFO   Distro: Found a valid CD for Ubuntu: D:\
02-04 23:42 INFO   root: Running the installer...
02-04 23:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\translations, languages=['en_US', 'en']
02-04 23:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\translations, languages=['en_US', 'en']
02-04 23:43 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=plasadmin
02-04 23:43 INFO   root: Received settings
02-04 23:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\translations, languages=['en_US', 'en']
02-04 23:43 DEBUG  TaskList: # Running tasklist...
02-04 23:43 DEBUG  TaskList: ## Running select_target_dir...
02-04 23:43 INFO   WindowsBackend: Installing into C:\ubuntu
02-04 23:43 DEBUG  TaskList: ## Finished select_target_dir
02-04 23:43 DEBUG  TaskList: ## Running create_dir_structure...
02-04 23:43 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-04 23:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-04 23:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-04 23:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-04 23:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-04 23:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-04 23:43 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-04 23:43 DEBUG  TaskList: ## Finished create_dir_structure
02-04 23:43 DEBUG  TaskList: ## Running uncompress_target_dir...
02-04 23:43 DEBUG  TaskList: ## Finished uncompress_target_dir
02-04 23:43 DEBUG  TaskList: ## Running create_uninstaller...
02-04 23:43 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-04 23:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-04 23:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-04 23:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-04 23:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-04 23:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
02-04 23:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-04 23:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-04 23:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-04 23:43 DEBUG  TaskList: ## Finished create_uninstaller
02-04 23:43 DEBUG  TaskList: ## Running copy_installation_files...
02-04 23:43 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-04 23:43 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\winboot -> C:\ubuntu\winboot
02-04 23:43 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylE945.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-04 23:43 DEBUG  TaskList: ## Finished copy_installation_files
02-04 23:43 DEBUG  TaskList: ## Running get_iso...
02-04 23:43 DEBUG  TaskList: New task copy_file
02-04 23:43 DEBUG  TaskList: ### Running copy_file...
02-04 23:47 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
02-04 23:47 DEBUG  TaskList: # Cancelling tasklist
02-04 23:47 DEBUG  TaskList: New task check_iso
02-04 23:47 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
02-04 23:47 DEBUG  CommonBackend: Searching for local ISO
02-04 23:47 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-04 23:47 DEBUG  TaskList: New task get_metalink
02-04 23:47 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-04 23:47 DEBUG  TaskList: # Cancelling tasklist
02-04 23:47 DEBUG  TaskList: # Finished tasklist
```

```

---

### Post by Mark Phelps on 2011-02-07
OK ... NOT a Wubi expert ... but the "permission denied" entries in the log are to be expected if you do NOT have Admin rights -- as your reply earlier indicated.

Don't think you can install Wubi without admin rights.

So, is this a personal PC (in which case, you SHOULD have admin rights)? Or is this a "work" PC (in which case you most probably will NOT have admin rights).

If it's the latter -- leave it alone!  Many companies have policies that will result in folks being fired for tampering with company-provided equipment.

---

### Post by n.arrow001 on 2011-08-16
i am having a same prob..please give me some solution

---

