---
title: "ERROR: No Root File System is Defined"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by Preston Durbin on 2010-10-17
I'm trying to install Ubuntu 10.04 LST but it keeps giving me the error listing in the title when I try to partition. 
Does anyone have a solution?

---

### Post by coffeecat on 2010-10-17
That sounds as though you have selected the manual (advanced) option at the partitioning stage of the installer and have failed to select a partition for the root filesystem. Is this right that you are getting the error in the manual partitioning stage of the installer? If not, you need to give more details.

Are you trying to install to pre-existing partitions or did you run Gparted in the live session to set up your partitions before starting the installer?

Just in case you don't know this, the shorthand for the root partition is '/' and you must select a partition formatted with a Linux filesystem for this in the manual option before you can proceed.

---

### Post by Preston Durbin on 2010-10-17
I haven't ran gParted Live. I run the installer from within Ubuntu and it gets to step four (Choosing a Partition) and no matter what i do it gives the same error.

---

### Post by Rubi1200 on 2010-10-17
Please post a screenshot of the installer when you get to this stage so we can get a better idea of what you see.

Also, run this command from the LiveCD and post the output:

```
sudo fdisk -l
```

Thanks.

---

### Post by Preston Durbin on 2010-10-17
10-17 10:56 DEBUG  TaskList: New task get_metalink
10-17 10:56 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-17 10:56 DEBUG  TaskList: # Cancelling tasklist
10-17 10:56 DEBUG  TaskList: # Finished tasklist

This is what i see

---

### Post by Rubi1200 on 2010-10-18
It appears you are trying to install using Wubi; is this correct?

Are you connected to the Internet during the installation process?

---

### Post by Preston Durbin on 2010-10-18
Uh... yeah, ive been on this forum the whole time i try installing

---

### Post by Preston Durbin on 2010-10-18
now i got this... but my installer made it further into the installation

10-18 08:27 INFO   root: === wubi 10.04.1 rev190 ===
10-18 08:27 DEBUG  root: Logfile is c:\users\user\appdata\local\temp\wubi-10.04.1-rev190.log
10-18 08:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
10-18 08:27 DEBUG  CommonBackend: data_dir=C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\data
10-18 08:27 DEBUG  WindowsBackend: 7z=C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\bin\7z.exe
10-18 08:27 DEBUG  CommonBackend: Fetching basic info...
10-18 08:27 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-18 08:27 DEBUG  CommonBackend: platform=win32
10-18 08:27 DEBUG  CommonBackend: osname=nt
10-18 08:27 DEBUG  CommonBackend: language=en_US
10-18 08:27 DEBUG  CommonBackend: encoding=cp1252
10-18 08:27 DEBUG  WindowsBackend: arch=amd64
10-18 08:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\data\isolist.ini
10-18 08:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 08:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 08:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 08:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 08:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 08:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 08:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 08:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 08:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-18 08:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 08:27 DEBUG  WindowsBackend: Fetching host info...
10-18 08:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 08:27 DEBUG  WindowsBackend: windows version=vista
10-18 08:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-18 08:27 DEBUG  WindowsBackend: windows_sp=None
10-18 08:27 DEBUG  WindowsBackend: windows_build=7600
10-18 08:27 DEBUG  WindowsBackend: gmt=-7
10-18 08:27 DEBUG  WindowsBackend: country=US
10-18 08:27 DEBUG  WindowsBackend: timezone=America/Denver
10-18 08:27 DEBUG  WindowsBackend: windows_username=USer
10-18 08:27 DEBUG  WindowsBackend: user_full_name=USer
10-18 08:27 DEBUG  WindowsBackend: user_directory=C:\Users\USer
10-18 08:27 DEBUG  WindowsBackend: windows_language_code=1033
10-18 08:27 DEBUG  WindowsBackend: windows_language=English
10-18 08:27 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) CPU          900  @ 2.20GHz
10-18 08:27 DEBUG  WindowsBackend: bootloader=vista
10-18 08:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 121375.378906 mb free ntfs)
10-18 08:27 DEBUG  WindowsBackend: drive=Drive(C: hd 121375.378906 mb free ntfs)
10-18 08:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-18 08:27 DEBUG  WindowsBackend: uninstaller_path=None
10-18 08:27 DEBUG  WindowsBackend: previous_target_dir=None
10-18 08:27 DEBUG  WindowsBackend: previous_distro_name=None
10-18 08:27 DEBUG  WindowsBackend: keyboard_id=67699721
10-18 08:27 DEBUG  WindowsBackend: keyboard_layout=us
10-18 08:27 DEBUG  WindowsBackend: keyboard_variant=
10-18 08:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-18 08:27 DEBUG  CommonBackend: locale=en_US.UTF-8
10-18 08:27 DEBUG  WindowsBackend: total_memory_mb=3000.93359375
10-18 08:27 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 08:27 DEBUG  CommonBackend: Searching for local CDs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Ubuntu CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Ubuntu CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Ubuntu Netbook CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Kubuntu CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Kubuntu CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Kubuntu Netbook CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Xubuntu CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Xubuntu CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Mythbuntu CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether C:\Users\USer\AppData\Local\Temp\pylFA66.tmp is a valid Mythbuntu CD
10-18 08:27 DEBUG  Distro:     does not contain C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\casper\filesystem.squashfs
10-18 08:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 08:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.1 LTS "Lucid Lynx" - Release i386 (20100816.1)
10-18 08:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.1', 'build': '20100816.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
10-18 08:28 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-18 08:28 INFO   root: Running the CD menu...
10-18 08:28 DEBUG  WindowsFrontend: __init__...
10-18 08:28 DEBUG  WindowsFrontend: on_init...
10-18 08:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\translations, languages=['en_US', 'en']
10-18 08:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\translations, languages=['en_US', 'en']
10-18 08:28 INFO   root: CD menu finished
10-18 08:28 INFO   root: Running the installer...
10-18 08:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\translations, languages=['en_US', 'en']
10-18 08:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\translations, languages=['en_US', 'en']
10-18 08:28 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=preston
10-18 08:28 INFO   root: Received settings
10-18 08:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\translations, languages=['en_US', 'en']
10-18 08:28 DEBUG  TaskList: # Running tasklist...
10-18 08:28 DEBUG  TaskList: ## Running select_target_dir...
10-18 08:28 INFO   WindowsBackend: Installing into C:\ubuntu
10-18 08:28 DEBUG  TaskList: ## Finished select_target_dir
10-18 08:28 DEBUG  TaskList: ## Running create_dir_structure...
10-18 08:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-18 08:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-18 08:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-18 08:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-18 08:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-18 08:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-18 08:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-18 08:28 DEBUG  TaskList: ## Finished create_dir_structure
10-18 08:28 DEBUG  TaskList: ## Running uncompress_target_dir...
10-18 08:28 DEBUG  TaskList: ## Finished uncompress_target_dir
10-18 08:28 DEBUG  TaskList: ## Running create_uninstaller...
10-18 08:28 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-18 08:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-18 08:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-18 08:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-18 08:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-18 08:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
10-18 08:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-18 08:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-18 08:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-18 08:28 DEBUG  TaskList: ## Finished create_uninstaller
10-18 08:28 DEBUG  TaskList: ## Running copy_installation_files...
10-18 08:28 DEBUG  WindowsBackend: Copying C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-18 08:28 DEBUG  WindowsBackend: Copying C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\winboot -> C:\ubuntu\winboot
10-18 08:28 DEBUG  WindowsBackend: Copying C:\Users\USer\AppData\Local\Temp\pylFA66.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-18 08:28 DEBUG  TaskList: ## Finished copy_installation_files
10-18 08:28 DEBUG  TaskList: ## Running get_iso...
10-18 08:28 DEBUG  TaskList: New task copy_file
10-18 08:28 DEBUG  TaskList: ### Running copy_file...
10-18 08:31 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
10-18 08:31 DEBUG  TaskList: # Cancelling tasklist
10-18 08:31 DEBUG  TaskList: New task check_iso
10-18 08:31 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
10-18 08:31 DEBUG  CommonBackend: Searching for local ISO
10-18 08:31 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-18 08:31 DEBUG  TaskList: New task get_metalink
10-18 08:31 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-18 08:31 DEBUG  TaskList: # Cancelling tasklist
10-18 08:31 DEBUG  TaskList: # Finished tasklist

---

### Post by Preston Durbin on 2010-10-18
Thx for the help everyone but i did it finally. Instead of using Wubi i just did everything manually

---

