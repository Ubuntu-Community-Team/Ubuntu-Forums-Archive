---
title: "Problem while installing ubuntu with wubi Installer"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by joj0o on 2011-09-14
Hi, I am a new user in Linux, and right now I want to try to install Ubuntu at my laptop.
But I have some problem while installing this software with WUBI installer. 

At the first time, I just run the wubi installer and it was download automatically the ISO file from the internet. and then I have problem (access denied), So I search some solution in google and they said I should download the ISO file first and put it together in same folder with wubi installer. But after I did that, there was still an error coming up during the installation. 

Here, I post the full log :

09-14 16:08 INFO   root: === wubi 11.04 rev211 ===
09-14 16:08 DEBUG  root: Logfile is c:\users\joanito\appdata\local\temp\wubi-11.04-rev211.log
09-14 16:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\test\\wubi.exe"']
09-14 16:08 DEBUG  CommonBackend: data_dir=C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\data
09-14 16:08 DEBUG  WindowsBackend: 7z=C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\bin\7z.exe
09-14 16:08 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-14 16:08 DEBUG  CommonBackend: Fetching basic info...
09-14 16:08 DEBUG  CommonBackend: original_exe=D:\test\wubi.exe
09-14 16:08 DEBUG  CommonBackend: platform=win32
09-14 16:08 DEBUG  CommonBackend: osname=nt
09-14 16:08 DEBUG  CommonBackend: language=en_US
09-14 16:08 DEBUG  CommonBackend: encoding=cp1252
09-14 16:08 DEBUG  WindowsBackend: arch=amd64
09-14 16:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\data\isolist.ini
09-14 16:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-14 16:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-14 16:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-14 16:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-14 16:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-14 16:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-14 16:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-14 16:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-14 16:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-14 16:08 DEBUG  WindowsBackend: Fetching host info...
09-14 16:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-14 16:08 DEBUG  WindowsBackend: windows version=vista
09-14 16:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
09-14 16:08 DEBUG  WindowsBackend: windows_sp=None
09-14 16:08 DEBUG  WindowsBackend: windows_build=7601
09-14 16:08 DEBUG  WindowsBackend: gmt=7
09-14 16:08 DEBUG  WindowsBackend: country=US
09-14 16:08 DEBUG  WindowsBackend: timezone=America/New_York
09-14 16:08 DEBUG  WindowsBackend: windows_username=Joanito
09-14 16:08 DEBUG  WindowsBackend: user_full_name=Joanito
09-14 16:08 DEBUG  WindowsBackend: user_directory=C:\Users\Joanito
09-14 16:08 DEBUG  WindowsBackend: windows_language_code=1033
09-14 16:08 DEBUG  WindowsBackend: windows_language=English
09-14 16:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz
09-14 16:08 DEBUG  WindowsBackend: bootloader=vista
09-14 16:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8485.01953125 mb free ntfs)
09-14 16:08 DEBUG  WindowsBackend: drive=Drive(C: hd 8485.01953125 mb free ntfs)
09-14 16:08 DEBUG  WindowsBackend: drive=Drive(D: hd 63649.7226563 mb free ntfs)
09-14 16:08 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
09-14 16:08 DEBUG  WindowsBackend: drive=Drive(F: hd 102531.035156 mb free ntfs)
09-14 16:08 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
09-14 16:08 DEBUG  WindowsBackend: drive=Drive(Y: hd 9050.07421875 mb free ntfs)
09-14 16:08 DEBUG  WindowsBackend: uninstaller_path=None
09-14 16:08 DEBUG  WindowsBackend: previous_target_dir=None
09-14 16:08 DEBUG  WindowsBackend: previous_distro_name=None
09-14 16:08 DEBUG  WindowsBackend: keyboard_id=67699721
09-14 16:08 DEBUG  WindowsBackend: keyboard_layout=us
09-14 16:08 DEBUG  WindowsBackend: keyboard_variant=
09-14 16:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-14 16:08 DEBUG  CommonBackend: locale=en_US.UTF-8
09-14 16:08 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
09-14 16:08 DEBUG  CommonBackend: Searching ISOs on USB devices
09-14 16:08 DEBUG  CommonBackend: Searching for local CDs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Ubuntu Netbook CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Kubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Kubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Xubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Xubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Mythbuntu CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp is a valid Mythbuntu CD
09-14 16:08 DEBUG  Distro:     does not contain C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-14 16:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-14 16:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-14 16:08 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-14 16:08 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-14 16:08 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
09-14 16:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
09-14 16:08 INFO   Distro: Found a valid CD for Ubuntu: H:\
09-14 16:08 INFO   root: Running the CD menu...
09-14 16:08 DEBUG  WindowsFrontend: __init__...
09-14 16:08 DEBUG  WindowsFrontend: on_init...
09-14 16:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\translations, languages=['en_US', 'en']
09-14 16:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\translations, languages=['en_US', 'en']
09-14 16:08 INFO   root: CD menu finished
09-14 16:08 INFO   root: Running the installer...
09-14 16:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\translations, languages=['en_US', 'en']
09-14 16:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\translations, languages=['en_US', 'en']
09-14 16:08 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=joanito
09-14 16:08 INFO   root: Received settings
09-14 16:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\translations, languages=['en_US', 'en']
09-14 16:08 DEBUG  TaskList: # Running tasklist...
09-14 16:08 DEBUG  TaskList: ## Running select_target_dir...
09-14 16:08 INFO   WindowsBackend: Installing into D:\ubuntu
09-14 16:08 DEBUG  TaskList: ## Finished select_target_dir
09-14 16:08 DEBUG  TaskList: ## Running create_dir_structure...
09-14 16:08 DEBUG  CommonBackend: Creating dir D:\ubuntu
09-14 16:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
09-14 16:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
09-14 16:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
09-14 16:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
09-14 16:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
09-14 16:08 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
09-14 16:08 DEBUG  TaskList: ## Finished create_dir_structure
09-14 16:08 DEBUG  TaskList: ## Running uncompress_target_dir...
09-14 16:08 DEBUG  TaskList: ## Finished uncompress_target_dir
09-14 16:08 DEBUG  TaskList: ## Running create_uninstaller...
09-14 16:08 DEBUG  WindowsBackend: Copying uninstaller D:\test\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
09-14 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
09-14 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
09-14 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-14 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
09-14 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-14 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-14 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-14 16:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-14 16:08 DEBUG  TaskList: ## Finished create_uninstaller
09-14 16:08 DEBUG  TaskList: ## Running copy_installation_files...
09-14 16:08 DEBUG  WindowsBackend: Copying C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
09-14 16:08 DEBUG  WindowsBackend: Copying C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\winboot -> D:\ubuntu\winboot
09-14 16:08 DEBUG  WindowsBackend: Copying C:\Users\Joanito\AppData\Local\Temp\pyl62AE.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
09-14 16:08 DEBUG  TaskList: ## Finished copy_installation_files
09-14 16:08 DEBUG  TaskList: ## Running get_iso...
09-14 16:08 DEBUG  TaskList: New task copy_file
09-14 16:08 DEBUG  TaskList: ### Running copy_file...
09-14 16:09 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
09-14 16:09 DEBUG  TaskList: # Cancelling tasklist
09-14 16:09 DEBUG  TaskList: New task check_iso
09-14 16:09 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
09-14 16:09 DEBUG  CommonBackend: Searching for local ISO
09-14 16:09 DEBUG  Distro:   checking Ubuntu ISO D:\test\ubuntu-11.04-desktop-amd64.iso
09-14 16:09 DEBUG  WindowsBackend:   extracting .disk\info from D:\test\ubuntu-11.04-desktop-amd64.iso
09-14 16:09 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
09-14 16:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
09-14 16:09 INFO   Distro: Found a valid iso for Ubuntu: D:\test\ubuntu-11.04-desktop-amd64.iso
09-14 16:09 DEBUG  CommonBackend: Trying to use ISO D:\test\ubuntu-11.04-desktop-amd64.iso
09-14 16:09 DEBUG  TaskList: New task check_iso
09-14 16:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-14 16:09 DEBUG  TaskList: New task get_metalink
09-14 16:09 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-14 16:09 DEBUG  TaskList: # Cancelling tasklist
09-14 16:09 DEBUG  TaskList: # Finished tasklist


I used my laptop (Dell) 64 bits, and running under windows 7 home basic.
Can anybody help me please?

---

### Post by mörgæs on 2011-09-14
Hi, welcome to the fora.

For Wubi problems, best is to see this thread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by joj0o on 2011-09-16
oh thanks, finally I can fix my problem. :D

---

