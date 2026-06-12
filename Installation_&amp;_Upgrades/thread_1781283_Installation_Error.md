---
title: "Installation Error"
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by kushal24 on 2011-06-13
While installing UBUNTU i got an error towards the end sayin
"[B]Cannot download the metalink and therefore the ISO
For more information,please see the logfile : C:\Users\Kushal\AppData\Local\Temp [/B] "

---

### Post by CyberMatrix on 2011-06-13
I think this error you must installing Ubuntu inside windows..if that  correct it might be due to faulty extraction problem in temp folder.
whenever installer tries to install something it needs files to be extracted in order to proceed for next installation..try to use **CCleaner** and clean you system if still persist then try well see if some else post something useful than mine one...good luck mate..

---

### Post by Rubi1200 on 2011-06-13
Hi and welcome to the forums kushal24 :)

Place the wubi.exe and downloaded Desktop ISO image in the same folder and then run the executable again.

Make sure the versions match:

> For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) 

For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) 

For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)If this doesn't work for you, then please post the contents of the wubi log:
Go to Start > Run and enter %temp% to open the temp folder then copy and paste the contents of the error log here.

---

### Post by bitswap on 2011-06-13
I have the same problem. I had the downloaded 11.04 then burned to cd, and selected 2nd option, got about 80% through when error occured. Here is the temp log: 

06-10 15:28 INFO   root: === wubi 11.04 rev211 ===
06-10 15:28 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
06-10 15:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
06-10 15:28 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\data
06-10 15:28 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\bin\7z.exe
06-10 15:28 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users.WINNT\Start Menu\Programs\Startup
06-10 15:28 DEBUG  CommonBackend: Fetching basic info...
06-10 15:28 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-10 15:28 DEBUG  CommonBackend: platform=win32
06-10 15:28 DEBUG  CommonBackend: osname=nt
06-10 15:28 DEBUG  CommonBackend: language=en_US
06-10 15:28 DEBUG  CommonBackend: encoding=cp1252
06-10 15:28 DEBUG  WindowsBackend: arch=amd64
06-10 15:28 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\data\isolist.ini
06-10 15:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-10 15:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-10 15:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-10 15:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-10 15:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-10 15:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-10 15:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-10 15:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-10 15:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-10 15:28 DEBUG  WindowsBackend: Fetching host info...
06-10 15:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-10 15:28 DEBUG  WindowsBackend: windows version=2000
06-10 15:28 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
06-10 15:28 DEBUG  WindowsBackend: windows_sp=Service Pack 4
06-10 15:28 DEBUG  WindowsBackend: windows_build=2195
06-10 15:28 DEBUG  WindowsBackend: gmt=-5
06-10 15:28 DEBUG  WindowsBackend: country=US
06-10 15:28 DEBUG  WindowsBackend: timezone=America/New_York
06-10 15:28 DEBUG  WindowsBackend: windows_username=Administrator
06-10 15:28 DEBUG  WindowsBackend: user_full_name=Administrator
06-10 15:28 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
06-10 15:28 DEBUG  WindowsBackend: windows_language_code=1033
06-10 15:28 DEBUG  WindowsBackend: windows_language=English
06-10 15:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
06-10 15:28 DEBUG  WindowsBackend: bootloader=xp
06-10 15:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122659.070313 mb free ntfs)
06-10 15:28 DEBUG  WindowsBackend: drive=Drive(C: hd 122659.070313 mb free ntfs)
06-10 15:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-10 15:28 DEBUG  WindowsBackend: drive=Drive(E: hd 99181.515625 mb free ntfs)
06-10 15:28 DEBUG  WindowsBackend: drive=Drive(F: hd 74111.2109375 mb free ntfs)
06-10 15:28 DEBUG  WindowsBackend: drive=Drive(G: hd 9558.34375 mb free ntfs)
06-10 15:28 DEBUG  WindowsBackend: uninstaller_path=None
06-10 15:28 DEBUG  WindowsBackend: previous_target_dir=None
06-10 15:28 DEBUG  WindowsBackend: previous_distro_name=None
06-10 15:28 DEBUG  WindowsBackend: keyboard_id=67699721
06-10 15:28 DEBUG  WindowsBackend: keyboard_layout=us
06-10 15:28 DEBUG  WindowsBackend: keyboard_variant=
06-10 15:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-10 15:28 DEBUG  CommonBackend: locale=en_US.UTF-8
06-10 15:28 DEBUG  WindowsBackend: total_memory_mb=2046.23046875
06-10 15:28 DEBUG  CommonBackend: Searching ISOs on USB devices
06-10 15:28 DEBUG  CommonBackend: Searching for local CDs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu Netbook CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
06-10 15:28 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
06-10 15:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 15:28 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
06-10 15:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
06-10 15:28 INFO   Distro: Found a valid CD for Ubuntu: D:\
06-10 15:28 INFO   root: Running the CD menu...
06-10 15:28 DEBUG  WindowsFrontend: __init__...
06-10 15:28 DEBUG  WindowsFrontend: on_init...
06-10 15:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
06-10 15:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
06-10 15:30 INFO   root: CD menu finished
06-10 15:30 INFO   root: Rebooting
06-10 15:30 DEBUG  TaskList: # Running tasklist...
06-10 15:30 DEBUG  TaskList: ## Running reboot...
06-10 15:30 ERROR  TaskList: [Errno 2] The system cannot find the file specified
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 136, in reboot
  File "\lib\wubi\backends\common\utils.py", line 54, in run_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 701, in _execute_child
WindowsError: [Errno 2] The system cannot find the file specified
06-10 15:30 DEBUG  TaskList: # Cancelling tasklist
06-10 15:30 DEBUG  TaskList: # Finished tasklist
06-10 15:30 DEBUG  root: application.quit
06-10 15:30 DEBUG  WindowsFrontend: frontend.quit
06-10 15:30 DEBUG  WindowsFrontend: frontend.on_quit
06-10 15:30 DEBUG  root: application.on_quit
06-10 15:30 INFO   root: sys.exit
06-10 19:08 INFO   root: === wubi 11.04 rev211 ===
06-10 19:08 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
06-10 19:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
06-10 19:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\data
06-10 19:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
06-10 19:08 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users.WINNT\Start Menu\Programs\Startup
06-10 19:08 DEBUG  CommonBackend: Fetching basic info...
06-10 19:08 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-10 19:08 DEBUG  CommonBackend: platform=win32
06-10 19:08 DEBUG  CommonBackend: osname=nt
06-10 19:08 DEBUG  CommonBackend: language=en_US
06-10 19:08 DEBUG  CommonBackend: encoding=cp1252
06-10 19:08 DEBUG  WindowsBackend: arch=amd64
06-10 19:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
06-10 19:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-10 19:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-10 19:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-10 19:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-10 19:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-10 19:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-10 19:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-10 19:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-10 19:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-10 19:08 DEBUG  WindowsBackend: Fetching host info...
06-10 19:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-10 19:08 DEBUG  WindowsBackend: windows version=2000
06-10 19:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
06-10 19:08 DEBUG  WindowsBackend: windows_sp=Service Pack 4
06-10 19:08 DEBUG  WindowsBackend: windows_build=2195
06-10 19:08 DEBUG  WindowsBackend: gmt=-5
06-10 19:08 DEBUG  WindowsBackend: country=US
06-10 19:08 DEBUG  WindowsBackend: timezone=America/New_York
06-10 19:08 DEBUG  WindowsBackend: windows_username=Administrator
06-10 19:08 DEBUG  WindowsBackend: user_full_name=Administrator
06-10 19:08 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
06-10 19:08 DEBUG  WindowsBackend: windows_language_code=1033
06-10 19:08 DEBUG  WindowsBackend: windows_language=English
06-10 19:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
06-10 19:08 DEBUG  WindowsBackend: bootloader=xp
06-10 19:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122660.515625 mb free ntfs)
06-10 19:08 DEBUG  WindowsBackend: drive=Drive(C: hd 122660.515625 mb free ntfs)
06-10 19:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-10 19:08 DEBUG  WindowsBackend: drive=Drive(E: hd 99181.515625 mb free ntfs)
06-10 19:08 DEBUG  WindowsBackend: drive=Drive(F: hd 74111.2109375 mb free ntfs)
06-10 19:08 DEBUG  WindowsBackend: drive=Drive(G: hd 9558.34375 mb free ntfs)
06-10 19:08 DEBUG  WindowsBackend: uninstaller_path=None
06-10 19:08 DEBUG  WindowsBackend: previous_target_dir=None
06-10 19:08 DEBUG  WindowsBackend: previous_distro_name=None
06-10 19:08 DEBUG  WindowsBackend: keyboard_id=67699721
06-10 19:08 DEBUG  WindowsBackend: keyboard_layout=us
06-10 19:08 DEBUG  WindowsBackend: keyboard_variant=
06-10 19:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-10 19:08 DEBUG  CommonBackend: locale=en_US.UTF-8
06-10 19:08 DEBUG  WindowsBackend: total_memory_mb=2046.23046875
06-10 19:08 DEBUG  CommonBackend: Searching ISOs on USB devices
06-10 19:08 DEBUG  CommonBackend: Searching for local CDs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
06-10 19:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
06-10 19:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:08 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
06-10 19:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
06-10 19:08 INFO   Distro: Found a valid CD for Ubuntu: D:\
06-10 19:08 INFO   root: Running the CD menu...
06-10 19:08 DEBUG  WindowsFrontend: __init__...
06-10 19:08 DEBUG  WindowsFrontend: on_init...
06-10 19:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
06-10 19:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
06-10 19:08 INFO   root: CD menu finished
06-10 19:08 INFO   root: Running the installer...
06-10 19:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
06-10 19:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
06-10 19:10 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
06-10 19:10 INFO   root: Received settings
06-10 19:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
06-10 19:10 DEBUG  TaskList: # Running tasklist...
06-10 19:10 DEBUG  TaskList: ## Running select_target_dir...
06-10 19:10 INFO   WindowsBackend: Installing into G:\ubuntu
06-10 19:10 DEBUG  TaskList: ## Finished select_target_dir
06-10 19:10 DEBUG  TaskList: ## Running create_dir_structure...
06-10 19:10 DEBUG  CommonBackend: Creating dir G:\ubuntu
06-10 19:10 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
06-10 19:10 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
06-10 19:10 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
06-10 19:10 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
06-10 19:10 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
06-10 19:10 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
06-10 19:10 DEBUG  TaskList: ## Finished create_dir_structure
06-10 19:10 DEBUG  TaskList: ## Running uncompress_target_dir...
06-10 19:10 DEBUG  TaskList: ## Finished uncompress_target_dir
06-10 19:10 DEBUG  TaskList: ## Running create_uninstaller...
06-10 19:10 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
06-10 19:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
06-10 19:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
06-10 19:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-10 19:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
06-10 19:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
06-10 19:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-10 19:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-10 19:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-10 19:10 DEBUG  TaskList: ## Finished create_uninstaller
06-10 19:10 DEBUG  TaskList: ## Running copy_installation_files...
06-10 19:10 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
06-10 19:10 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\winboot -> G:\ubuntu\winboot
06-10 19:10 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
06-10 19:10 DEBUG  TaskList: ## Finished copy_installation_files
06-10 19:10 DEBUG  TaskList: ## Running get_iso...
06-10 19:10 DEBUG  TaskList: New task copy_file
06-10 19:10 DEBUG  TaskList: ### Running copy_file...
06-10 19:14 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
06-10 19:14 DEBUG  TaskList: # Cancelling tasklist
06-10 19:14 DEBUG  TaskList: New task check_iso
06-10 19:14 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
06-10 19:14 DEBUG  CommonBackend: Searching for local ISO
06-10 19:14 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-10 19:14 DEBUG  TaskList: New task get_metalink
06-10 19:14 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-10 19:14 DEBUG  TaskList: # Cancelling tasklist
06-10 19:14 DEBUG  TaskList: # Finished tasklist
06-10 19:37 INFO   root: === wubi 11.04 rev211 ===
06-10 19:37 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
06-10 19:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Administrator\\My Documents\\Downloads\\wubi.exe"']
06-10 19:37 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data
06-10 19:37 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
06-10 19:37 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users.WINNT\Start Menu\Programs\Startup
06-10 19:37 DEBUG  CommonBackend: Fetching basic info...
06-10 19:37 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\My Documents\Downloads\wubi.exe
06-10 19:37 DEBUG  CommonBackend: platform=win32
06-10 19:37 DEBUG  CommonBackend: osname=nt
06-10 19:37 DEBUG  CommonBackend: language=en_US
06-10 19:37 DEBUG  CommonBackend: encoding=cp1252
06-10 19:37 DEBUG  WindowsBackend: arch=amd64
06-10 19:37 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
06-10 19:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-10 19:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-10 19:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-10 19:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-10 19:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-10 19:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-10 19:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-10 19:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-10 19:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-10 19:37 DEBUG  WindowsBackend: Fetching host info...
06-10 19:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-10 19:37 DEBUG  WindowsBackend: windows version=2000
06-10 19:37 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
06-10 19:37 DEBUG  WindowsBackend: windows_sp=Service Pack 4
06-10 19:37 DEBUG  WindowsBackend: windows_build=2195
06-10 19:37 DEBUG  WindowsBackend: gmt=-5
06-10 19:37 DEBUG  WindowsBackend: country=US
06-10 19:37 DEBUG  WindowsBackend: timezone=America/New_York
06-10 19:37 DEBUG  WindowsBackend: windows_username=Administrator
06-10 19:37 DEBUG  WindowsBackend: user_full_name=Administrator
06-10 19:37 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
06-10 19:37 DEBUG  WindowsBackend: windows_language_code=1033
06-10 19:37 DEBUG  WindowsBackend: windows_language=English
06-10 19:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
06-10 19:37 DEBUG  WindowsBackend: bootloader=xp
06-10 19:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122656.351563 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(C: hd 122656.351563 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(E: hd 99181.515625 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(F: hd 74111.2109375 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(G: hd 8916.6796875 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
06-10 19:37 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
06-10 19:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-10 19:37 DEBUG  WindowsBackend: keyboard_id=67699721
06-10 19:37 DEBUG  WindowsBackend: keyboard_layout=us
06-10 19:37 DEBUG  WindowsBackend: keyboard_variant=
06-10 19:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-10 19:37 DEBUG  CommonBackend: locale=en_US.UTF-8
06-10 19:37 DEBUG  WindowsBackend: total_memory_mb=2046.23046875
06-10 19:37 DEBUG  CommonBackend: Searching ISOs on USB devices
06-10 19:37 DEBUG  CommonBackend: Searching for local CDs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 INFO   root: Already installed, running the uninstaller...
06-10 19:37 INFO   root: Running the uninstaller...
06-10 19:37 INFO   CommonBackend: This is the uninstaller running
06-10 19:37 DEBUG  WindowsFrontend: __init__...
06-10 19:37 DEBUG  WindowsFrontend: on_init...
06-10 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
06-10 19:37 INFO   root: Received settings
06-10 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
06-10 19:37 DEBUG  TaskList: # Running tasklist...
06-10 19:37 DEBUG  TaskList: ## Running Backup ISO...
06-10 19:37 DEBUG  TaskList: ## Finished Backup ISO
06-10 19:37 DEBUG  TaskList: ## Running Remove bootloader entry...
06-10 19:37 ERROR  WindowsBackend: Cannot find bcdedit
06-10 19:37 DEBUG  WindowsBackend: undo_bootini C:
06-10 19:37 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 122656.351563 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: undo_bootini E:
06-10 19:37 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 99181.515625 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: undo_bootini F:
06-10 19:37 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 74111.2109375 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: undo_bootini G:
06-10 19:37 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 8916.6796875 mb free ntfs)
06-10 19:37 DEBUG  TaskList: ## Finished Remove bootloader entry
06-10 19:37 DEBUG  TaskList: ## Running Remove target dir...
06-10 19:37 DEBUG  CommonBackend: Deleting G:\ubuntu
06-10 19:37 DEBUG  TaskList: ## Finished Remove target dir
06-10 19:37 DEBUG  TaskList: ## Running Remove registry key...
06-10 19:37 DEBUG  TaskList: ## Finished Remove registry key
06-10 19:37 DEBUG  TaskList: # Finished tasklist
06-10 19:37 INFO   root: Almost finished uninstalling
06-10 19:37 INFO   root: Finished uninstallation
06-10 19:37 DEBUG  CommonBackend: Fetching basic info...
06-10 19:37 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\My Documents\Downloads\wubi.exe
06-10 19:37 DEBUG  CommonBackend: platform=win32
06-10 19:37 DEBUG  CommonBackend: osname=nt
06-10 19:37 DEBUG  WindowsBackend: arch=amd64
06-10 19:37 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
06-10 19:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-10 19:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-10 19:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-10 19:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-10 19:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-10 19:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-10 19:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-10 19:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-10 19:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-10 19:37 DEBUG  WindowsBackend: Fetching host info...
06-10 19:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-10 19:37 DEBUG  WindowsBackend: windows version=2000
06-10 19:37 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
06-10 19:37 DEBUG  WindowsBackend: windows_sp=Service Pack 4
06-10 19:37 DEBUG  WindowsBackend: windows_build=2195
06-10 19:37 DEBUG  WindowsBackend: gmt=-5
06-10 19:37 DEBUG  WindowsBackend: country=US
06-10 19:37 DEBUG  WindowsBackend: timezone=America/New_York
06-10 19:37 DEBUG  WindowsBackend: windows_username=Administrator
06-10 19:37 DEBUG  WindowsBackend: user_full_name=Administrator
06-10 19:37 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
06-10 19:37 DEBUG  WindowsBackend: windows_language_code=1033
06-10 19:37 DEBUG  WindowsBackend: windows_language=English
06-10 19:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
06-10 19:37 DEBUG  WindowsBackend: bootloader=xp
06-10 19:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122654.65625 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(C: hd 122654.65625 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(E: hd 99181.515625 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(F: hd 74111.2109375 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: drive=Drive(G: hd 9558.32421875 mb free ntfs)
06-10 19:37 DEBUG  WindowsBackend: uninstaller_path=None
06-10 19:37 DEBUG  WindowsBackend: previous_target_dir=None
06-10 19:37 DEBUG  WindowsBackend: previous_distro_name=None
06-10 19:37 DEBUG  WindowsBackend: keyboard_id=67699721
06-10 19:37 DEBUG  WindowsBackend: keyboard_layout=us
06-10 19:37 DEBUG  WindowsBackend: keyboard_variant=
06-10 19:37 DEBUG  WindowsBackend: total_memory_mb=2046.23046875
06-10 19:37 DEBUG  CommonBackend: Searching ISOs on USB devices
06-10 19:37 DEBUG  CommonBackend: Searching for local CDs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 INFO   root: Running the installer...
06-10 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
06-10 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
06-10 19:37 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
06-10 19:37 INFO   root: Received settings
06-10 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
06-10 19:37 DEBUG  TaskList: # Running tasklist...
06-10 19:37 DEBUG  TaskList: ## Running select_target_dir...
06-10 19:37 INFO   WindowsBackend: Installing into G:\ubuntu
06-10 19:37 DEBUG  TaskList: ## Finished select_target_dir
06-10 19:37 DEBUG  TaskList: ## Running create_dir_structure...
06-10 19:37 DEBUG  CommonBackend: Creating dir G:\ubuntu
06-10 19:37 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
06-10 19:37 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
06-10 19:37 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
06-10 19:37 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
06-10 19:37 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
06-10 19:37 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
06-10 19:37 DEBUG  TaskList: ## Finished create_dir_structure
06-10 19:37 DEBUG  TaskList: ## Running uncompress_target_dir...
06-10 19:37 DEBUG  TaskList: ## Finished uncompress_target_dir
06-10 19:37 DEBUG  TaskList: ## Running create_uninstaller...
06-10 19:37 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Administrator\My Documents\Downloads\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
06-10 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
06-10 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
06-10 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-10 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
06-10 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
06-10 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-10 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-10 19:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-10 19:37 DEBUG  TaskList: ## Finished create_uninstaller
06-10 19:37 DEBUG  TaskList: ## Running copy_installation_files...
06-10 19:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
06-10 19:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\winboot -> G:\ubuntu\winboot
06-10 19:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
06-10 19:37 DEBUG  TaskList: ## Finished copy_installation_files
06-10 19:37 DEBUG  TaskList: ## Running get_iso...
06-10 19:37 DEBUG  CommonBackend: Searching for local CD
06-10 19:37 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:37 DEBUG  CommonBackend: Searching for local ISO
06-10 19:37 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-10 19:37 DEBUG  TaskList: New task get_metalink
06-10 19:37 DEBUG  TaskList: ### Running get_metalink...
06-10 19:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > G:\ubuntu\install
06-10 19:37 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
06-10 19:37 DEBUG  downloader: download finished (read 28363 bytes)
06-10 19:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > G:\ubuntu\install
06-10 19:37 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
06-10 19:37 DEBUG  downloader: download finished (read 874 bytes)
06-10 19:37 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > G:\ubuntu\install
06-10 19:37 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
06-10 19:37 DEBUG  downloader: download finished (read 198 bytes)
06-10 19:37 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-10 19:37 INFO   saplog: Checking block bindings..
06-10 19:37 INFO   saplog: Key verified successfully.
06-10 19:37 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

06-10 19:37 DEBUG  TaskList: ### Finished get_metalink
06-10 19:37 DEBUG  TaskList: New task download
06-10 19:37 DEBUG  TaskList: ### Running download...
06-10 19:37 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 19:38 INFO   WindowsFrontend: Operation cancelled
06-10 19:38 DEBUG  WindowsFrontend: frontend.quit
06-10 19:38 DEBUG  WindowsFrontend: frontend.on_quit
06-10 19:38 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
06-10 19:38 DEBUG  TaskList: # Cancelling tasklist
06-10 19:38 DEBUG  TaskList: ### Finished download
06-10 19:38 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
06-10 19:38 DEBUG  root: application.on_quit
06-10 19:38 DEBUG  root: Forceful exit
06-10 19:38 INFO   root: sys.exit
06-10 19:38 INFO   root: === wubi 11.04 rev211 ===
06-10 19:38 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
06-10 19:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
06-10 19:38 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\data
06-10 19:38 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\bin\7z.exe
06-10 19:38 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users.WINNT\Start Menu\Programs\Startup
06-10 19:38 DEBUG  CommonBackend: Fetching basic info...
06-10 19:38 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
06-10 19:38 DEBUG  CommonBackend: platform=win32
06-10 19:38 DEBUG  CommonBackend: osname=nt
06-10 19:38 DEBUG  CommonBackend: language=en_US
06-10 19:38 DEBUG  CommonBackend: encoding=cp1252
06-10 19:38 DEBUG  WindowsBackend: arch=amd64
06-10 19:38 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\data\isolist.ini
06-10 19:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-10 19:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-10 19:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-10 19:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-10 19:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-10 19:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-10 19:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-10 19:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-10 19:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-10 19:38 DEBUG  WindowsBackend: Fetching host info...
06-10 19:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-10 19:38 DEBUG  WindowsBackend: windows version=2000
06-10 19:38 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
06-10 19:38 DEBUG  WindowsBackend: windows_sp=Service Pack 4
06-10 19:38 DEBUG  WindowsBackend: windows_build=2195
06-10 19:38 DEBUG  WindowsBackend: gmt=-5
06-10 19:38 DEBUG  WindowsBackend: country=US
06-10 19:38 DEBUG  WindowsBackend: timezone=America/New_York
06-10 19:38 DEBUG  WindowsBackend: windows_username=Administrator
06-10 19:38 DEBUG  WindowsBackend: user_full_name=Administrator
06-10 19:38 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
06-10 19:38 DEBUG  WindowsBackend: windows_language_code=1033
06-10 19:38 DEBUG  WindowsBackend: windows_language=English
06-10 19:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
06-10 19:38 DEBUG  WindowsBackend: bootloader=xp
06-10 19:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122647.78125 mb free ntfs)
06-10 19:38 DEBUG  WindowsBackend: drive=Drive(C: hd 122647.78125 mb free ntfs)
06-10 19:38 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-10 19:38 DEBUG  WindowsBackend: drive=Drive(E: hd 99181.515625 mb free ntfs)
06-10 19:38 DEBUG  WindowsBackend: drive=Drive(F: hd 74111.2109375 mb free ntfs)
06-10 19:38 DEBUG  WindowsBackend: drive=Drive(G: hd 9553.64453125 mb free ntfs)
06-10 19:38 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
06-10 19:38 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
06-10 19:38 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-10 19:38 DEBUG  WindowsBackend: keyboard_id=67699721
06-10 19:38 DEBUG  WindowsBackend: keyboard_layout=us
06-10 19:38 DEBUG  WindowsBackend: keyboard_variant=
06-10 19:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-10 19:38 DEBUG  CommonBackend: locale=en_US.UTF-8
06-10 19:38 DEBUG  WindowsBackend: total_memory_mb=2046.23046875
06-10 19:38 DEBUG  CommonBackend: Searching ISOs on USB devices
06-10 19:38 DEBUG  CommonBackend: Searching for local CDs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu Netbook CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-10 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:38 INFO   root: Running the uninstaller...
06-10 19:38 INFO   CommonBackend: This is the uninstaller running
06-10 19:38 DEBUG  WindowsFrontend: __init__...
06-10 19:38 DEBUG  WindowsFrontend: on_init...
06-10 19:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\translations, languages=['en_US', 'en']
06-10 19:38 INFO   root: Received settings
06-10 19:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\translations, languages=['en_US', 'en']
06-10 19:38 DEBUG  TaskList: # Running tasklist...
06-10 19:38 DEBUG  TaskList: ## Running Backup ISO...
06-10 19:38 DEBUG  TaskList: ## Finished Backup ISO
06-10 19:38 DEBUG  TaskList: ## Running Remove bootloader entry...
06-10 19:38 ERROR  WindowsBackend: Cannot find bcdedit
06-10 19:38 DEBUG  WindowsBackend: undo_bootini C:
06-10 19:38 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 122647.78125 mb free ntfs)
06-10 19:38 DEBUG  WindowsBackend: undo_bootini E:
06-10 19:38 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 99181.515625 mb free ntfs)
06-10 19:38 DEBUG  WindowsBackend: undo_bootini F:
06-10 19:38 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 74111.2109375 mb free ntfs)
06-10 19:38 DEBUG  WindowsBackend: undo_bootini G:
06-10 19:38 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 9553.64453125 mb free ntfs)
06-10 19:38 DEBUG  TaskList: ## Finished Remove bootloader entry
06-10 19:38 DEBUG  TaskList: ## Running Remove target dir...
06-10 19:38 DEBUG  CommonBackend: Deleting G:\ubuntu
06-10 19:38 DEBUG  TaskList: ## Finished Remove target dir
06-10 19:38 DEBUG  TaskList: ## Running Remove registry key...
06-10 19:38 DEBUG  TaskList: ## Finished Remove registry key
06-10 19:38 DEBUG  TaskList: # Finished tasklist
06-10 19:38 INFO   root: Almost finished uninstalling
06-10 19:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl5.tmp\translations, languages=['en_US', 'en']
06-10 19:38 INFO   root: Finished uninstallation
06-10 19:38 DEBUG  root: application.quit
06-10 19:38 DEBUG  WindowsFrontend: frontend.quit
06-10 19:38 DEBUG  WindowsFrontend: frontend.on_quit
06-10 19:38 DEBUG  root: application.on_quit
06-10 19:38 INFO   root: sys.exit
06-10 19:51 INFO   root: === wubi 11.04 rev211 ===
06-10 19:51 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
06-10 19:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Administrator\\My Documents\\Downloads\\wubi.exe"']
06-10 19:51 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\data
06-10 19:51 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\bin\7z.exe
06-10 19:51 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users.WINNT\Start Menu\Programs\Startup
06-10 19:51 DEBUG  CommonBackend: Fetching basic info...
06-10 19:51 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\My Documents\Downloads\wubi.exe
06-10 19:51 DEBUG  CommonBackend: platform=win32
06-10 19:51 DEBUG  CommonBackend: osname=nt
06-10 19:51 DEBUG  CommonBackend: language=en_US
06-10 19:51 DEBUG  CommonBackend: encoding=cp1252
06-10 19:51 DEBUG  WindowsBackend: arch=amd64
06-10 19:51 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\data\isolist.ini
06-10 19:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-10 19:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-10 19:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-10 19:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-10 19:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-10 19:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-10 19:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-10 19:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-10 19:51 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-10 19:51 DEBUG  WindowsBackend: Fetching host info...
06-10 19:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-10 19:51 DEBUG  WindowsBackend: windows version=2000
06-10 19:51 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
06-10 19:51 DEBUG  WindowsBackend: windows_sp=Service Pack 4
06-10 19:51 DEBUG  WindowsBackend: windows_build=2195
06-10 19:51 DEBUG  WindowsBackend: gmt=-5
06-10 19:51 DEBUG  WindowsBackend: country=US
06-10 19:51 DEBUG  WindowsBackend: timezone=America/New_York
06-10 19:51 DEBUG  WindowsBackend: windows_username=Administrator
06-10 19:51 DEBUG  WindowsBackend: user_full_name=Administrator
06-10 19:51 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
06-10 19:51 DEBUG  WindowsBackend: windows_language_code=1033
06-10 19:51 DEBUG  WindowsBackend: windows_language=English
06-10 19:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
06-10 19:51 DEBUG  WindowsBackend: bootloader=xp
06-10 19:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122660.324219 mb free ntfs)
06-10 19:51 DEBUG  WindowsBackend: drive=Drive(C: hd 122660.324219 mb free ntfs)
06-10 19:51 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-10 19:51 DEBUG  WindowsBackend: drive=Drive(E: hd 99181.515625 mb free ntfs)
06-10 19:51 DEBUG  WindowsBackend: drive=Drive(F: hd 74111.2109375 mb free ntfs)
06-10 19:51 DEBUG  WindowsBackend: drive=Drive(G: hd 9558.32421875 mb free ntfs)
06-10 19:51 DEBUG  WindowsBackend: uninstaller_path=None
06-10 19:51 DEBUG  WindowsBackend: previous_target_dir=None
06-10 19:51 DEBUG  WindowsBackend: previous_distro_name=None
06-10 19:51 DEBUG  WindowsBackend: keyboard_id=67699721
06-10 19:51 DEBUG  WindowsBackend: keyboard_layout=us
06-10 19:51 DEBUG  WindowsBackend: keyboard_variant=
06-10 19:51 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-10 19:51 DEBUG  CommonBackend: locale=en_US.UTF-8
06-10 19:51 DEBUG  WindowsBackend: total_memory_mb=2046.23046875
06-10 19:51 DEBUG  CommonBackend: Searching ISOs on USB devices
06-10 19:51 DEBUG  CommonBackend: Searching for local CDs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu Netbook CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 INFO   root: Running the installer...
06-10 19:51 DEBUG  WindowsFrontend: __init__...
06-10 19:51 DEBUG  WindowsFrontend: on_init...
06-10 19:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
06-10 19:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
06-10 19:51 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
06-10 19:51 INFO   root: Received settings
06-10 19:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
06-10 19:51 DEBUG  TaskList: # Running tasklist...
06-10 19:51 DEBUG  TaskList: ## Running select_target_dir...
06-10 19:51 INFO   WindowsBackend: Installing into G:\ubuntu
06-10 19:51 DEBUG  TaskList: ## Finished select_target_dir
06-10 19:51 DEBUG  TaskList: ## Running create_dir_structure...
06-10 19:51 DEBUG  CommonBackend: Creating dir G:\ubuntu
06-10 19:51 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
06-10 19:51 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
06-10 19:51 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
06-10 19:51 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
06-10 19:51 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
06-10 19:51 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
06-10 19:51 DEBUG  TaskList: ## Finished create_dir_structure
06-10 19:51 DEBUG  TaskList: ## Running uncompress_target_dir...
06-10 19:51 DEBUG  TaskList: ## Finished uncompress_target_dir
06-10 19:51 DEBUG  TaskList: ## Running create_uninstaller...
06-10 19:51 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Administrator\My Documents\Downloads\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
06-10 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
06-10 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
06-10 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-10 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
06-10 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
06-10 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-10 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-10 19:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-10 19:51 DEBUG  TaskList: ## Finished create_uninstaller
06-10 19:51 DEBUG  TaskList: ## Running copy_installation_files...
06-10 19:51 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
06-10 19:51 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\winboot -> G:\ubuntu\winboot
06-10 19:51 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
06-10 19:51 DEBUG  TaskList: ## Finished copy_installation_files
06-10 19:51 DEBUG  TaskList: ## Running get_iso...
06-10 19:51 DEBUG  CommonBackend: Searching for local CD
06-10 19:51 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-10 19:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-10 19:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-10 19:51 DEBUG  CommonBackend: Searching for local ISO
06-10 19:51 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-10 19:51 DEBUG  TaskList: New task get_metalink
06-10 19:51 DEBUG  TaskList: ### Running get_metalink...
06-10 19:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > G:\ubuntu\install
06-10 19:51 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
06-10 19:51 DEBUG  downloader: download finished (read 28363 bytes)
06-10 19:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > G:\ubuntu\install
06-10 19:51 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
06-10 19:51 DEBUG  downloader: download finished (read 874 bytes)
06-10 19:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > G:\ubuntu\install
06-10 19:51 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
06-10 19:51 DEBUG  downloader: download finished (read 198 bytes)
06-10 19:51 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-10 19:51 INFO   saplog: Checking block bindings..
06-10 19:51 INFO   saplog: Key verified successfully.
06-10 19:51 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

06-10 19:51 DEBUG  TaskList: ### Finished get_metalink
06-10 19:51 DEBUG  TaskList: New task download
06-10 19:51 DEBUG  TaskList: ### Running download...
06-10 19:51 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  TaskList: ### Finished download
06-10 22:42 DEBUG  TaskList: New task check_iso
06-10 22:42 DEBUG  TaskList: ### Running check_iso...
06-10 22:42 DEBUG  CommonBackend: Checking G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
06-10 22:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
06-10 22:42 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  TaskList: New task get_file_md5
06-10 22:42 DEBUG  TaskList: #### Running get_file_md5...
06-10 22:42 DEBUG  TaskList: #### Finished get_file_md5
06-10 22:42 DEBUG  TaskList: ### Finished check_iso
06-10 22:42 DEBUG  TaskList: ## Finished get_iso
06-10 22:42 DEBUG  TaskList: ## Running extract_kernel...
06-10 22:42 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
06-10 22:42 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
06-10 22:42 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
06-10 22:42 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
06-10 22:42 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
06-10 22:42 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
06-10 22:42 DEBUG  TaskList: ## Finished extract_kernel
06-10 22:42 DEBUG  TaskList: ## Running choose_disk_sizes...
06-10 22:42 DEBUG  WindowsBackend: total size=6000
  root=5744
  swap=256
  home=0
  usr=0
06-10 22:42 DEBUG  TaskList: ## Finished choose_disk_sizes
06-10 22:42 DEBUG  TaskList: ## Running create_preseed...
06-10 22:42 DEBUG  TaskList: ## Finished create_preseed
06-10 22:42 DEBUG  TaskList: ## Running modify_bootloader...
06-10 22:42 DEBUG  TaskList: New task modify_bootini
06-10 22:42 DEBUG  TaskList: ### Running modify_bootini...
06-10 22:42 DEBUG  WindowsBackend: modify_bootini C:
06-10 22:42 DEBUG  TaskList: ### Finished modify_bootini
06-10 22:42 DEBUG  TaskList: New task modify_bootini
06-10 22:42 DEBUG  TaskList: ### Running modify_bootini...
06-10 22:42 DEBUG  WindowsBackend: modify_bootini E:
06-10 22:42 DEBUG  WindowsBackend: Could not find boot.ini E:\boot.ini
06-10 22:42 DEBUG  TaskList: ### Finished modify_bootini
06-10 22:42 DEBUG  TaskList: New task modify_bootini
06-10 22:42 DEBUG  TaskList: ### Running modify_bootini...
06-10 22:42 DEBUG  WindowsBackend: modify_bootini F:
06-10 22:42 DEBUG  WindowsBackend: Could not find boot.ini F:\boot.ini
06-10 22:42 DEBUG  TaskList: ### Finished modify_bootini
06-10 22:42 DEBUG  TaskList: New task modify_bootini
06-10 22:42 DEBUG  TaskList: ### Running modify_bootini...
06-10 22:42 DEBUG  WindowsBackend: modify_bootini G:
06-10 22:42 DEBUG  WindowsBackend: Could not find boot.ini G:\boot.ini
06-10 22:42 DEBUG  TaskList: ### Finished modify_bootini
06-10 22:42 DEBUG  TaskList: ## Finished modify_bootloader
06-10 22:42 DEBUG  TaskList: ## Running modify_grub_configuration...
06-10 22:42 DEBUG  TaskList: ## Finished modify_grub_configuration
06-10 22:42 DEBUG  TaskList: ## Running create_virtual_disks...
06-10 22:42 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\root.disk of 5744MB
06-10 22:42 DEBUG  Virtualdisk: Could not load SetFileValidData.
06-10 22:52 DEBUG  Virtualdisk:  Creating virtual disk G:\ubuntu\disks\swap.disk of 256MB
06-10 22:52 DEBUG  Virtualdisk: Could not load SetFileValidData.
06-10 22:52 DEBUG  TaskList: ## Finished create_virtual_disks
06-10 22:52 DEBUG  TaskList: ## Running uncompress_files...
06-10 22:52 DEBUG  WindowsBackend: compact G:\ubuntu\install\boot /U /A /F
06-10 22:52 DEBUG  WindowsBackend: compact G:\ubuntu\install\boot\*.* /U /A /F
06-10 22:52 DEBUG  TaskList: ## Finished uncompress_files
06-10 22:52 DEBUG  TaskList: ## Running eject_cd...
06-10 22:52 DEBUG  TaskList: ## Finished eject_cd
06-10 22:52 DEBUG  TaskList: # Finished tasklist
06-10 22:52 INFO   root: Almost finished installing
06-10 22:52 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl12.tmp\translations, languages=['en_US', 'en']
06-10 23:06 INFO   root: Finished installation
06-10 23:06 DEBUG  root: application.quit
06-10 23:06 DEBUG  WindowsFrontend: frontend.quit
06-10 23:06 DEBUG  WindowsFrontend: frontend.on_quit
06-10 23:06 DEBUG  root: application.on_quit
06-10 23:06 INFO   root: sys.exit
06-12 12:48 INFO   root: === wubi 11.04 rev211 ===
06-12 12:48 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
06-12 12:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
06-12 12:48 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data
06-12 12:48 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
06-12 12:48 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users.WINNT\Start Menu\Programs\Startup
06-12 12:48 DEBUG  CommonBackend: Fetching basic info...
06-12 12:48 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
06-12 12:48 DEBUG  CommonBackend: platform=win32
06-12 12:48 DEBUG  CommonBackend: osname=nt
06-12 12:48 DEBUG  CommonBackend: language=en_US
06-12 12:48 DEBUG  CommonBackend: encoding=cp1252
06-12 12:48 DEBUG  WindowsBackend: arch=amd64
06-12 12:48 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
06-12 12:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-12 12:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-12 12:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-12 12:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-12 12:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-12 12:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-12 12:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-12 12:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-12 12:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-12 12:48 DEBUG  WindowsBackend: Fetching host info...
06-12 12:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-12 12:48 DEBUG  WindowsBackend: windows version=2000
06-12 12:48 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
06-12 12:48 DEBUG  WindowsBackend: windows_sp=Service Pack 4
06-12 12:48 DEBUG  WindowsBackend: windows_build=2195
06-12 12:48 DEBUG  WindowsBackend: gmt=-5
06-12 12:48 DEBUG  WindowsBackend: country=US
06-12 12:48 DEBUG  WindowsBackend: timezone=America/New_York
06-12 12:48 DEBUG  WindowsBackend: windows_username=Administrator
06-12 12:48 DEBUG  WindowsBackend: user_full_name=Administrator
06-12 12:48 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
06-12 12:48 DEBUG  WindowsBackend: windows_language_code=1033
06-12 12:48 DEBUG  WindowsBackend: windows_language=English
06-12 12:48 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
06-12 12:48 DEBUG  WindowsBackend: bootloader=xp
06-12 12:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 123227.027344 mb free ntfs)
06-12 12:48 DEBUG  WindowsBackend: drive=Drive(C: hd 123227.027344 mb free ntfs)
06-12 12:48 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-12 12:48 DEBUG  WindowsBackend: drive=Drive(E: hd 99181.515625 mb free ntfs)
06-12 12:48 DEBUG  WindowsBackend: drive=Drive(F: hd 67163.703125 mb free ntfs)
06-12 12:48 DEBUG  WindowsBackend: drive=Drive(G: hd 2609.33203125 mb free ntfs)
06-12 12:48 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
06-12 12:48 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
06-12 12:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-12 12:48 DEBUG  WindowsBackend: keyboard_id=67699721
06-12 12:48 DEBUG  WindowsBackend: keyboard_layout=us
06-12 12:48 DEBUG  WindowsBackend: keyboard_variant=
06-12 12:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-12 12:48 DEBUG  CommonBackend: locale=en_US.UTF-8
06-12 12:48 DEBUG  WindowsBackend: total_memory_mb=2046.23046875
06-12 12:48 DEBUG  CommonBackend: Searching ISOs on USB devices
06-12 12:48 DEBUG  CommonBackend: Searching for local CDs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-12 12:48 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-12 12:48 INFO   root: Running the uninstaller...
06-12 12:48 INFO   CommonBackend: This is the uninstaller running
06-12 12:48 DEBUG  WindowsFrontend: __init__...
06-12 12:48 DEBUG  WindowsFrontend: on_init...
06-12 12:48 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
06-12 12:48 INFO   root: Received settings
06-12 12:48 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
06-12 12:48 DEBUG  TaskList: # Running tasklist...
06-12 12:48 DEBUG  TaskList: ## Running Backup ISO...
06-12 12:48 DEBUG  TaskList: ## Finished Backup ISO
06-12 12:48 DEBUG  TaskList: ## Running Remove bootloader entry...
06-12 12:48 ERROR  WindowsBackend: Cannot find bcdedit
06-12 12:48 DEBUG  WindowsBackend: undo_bootini C:
06-12 12:48 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 123227.027344 mb free ntfs)
06-12 12:48 DEBUG  WindowsBackend: undo_bootini E:
06-12 12:48 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 99181.515625 mb free ntfs)
06-12 12:48 DEBUG  WindowsBackend: undo_bootini F:
06-12 12:48 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 67163.703125 mb free ntfs)
06-12 12:48 DEBUG  WindowsBackend: undo_bootini G:
06-12 12:48 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 2609.33203125 mb free ntfs)
06-12 12:48 DEBUG  TaskList: ## Finished Remove bootloader entry
06-12 12:48 DEBUG  TaskList: ## Running Remove target dir...
06-12 12:48 DEBUG  CommonBackend: Deleting G:\ubuntu
06-12 12:48 DEBUG  TaskList: ## Finished Remove target dir
06-12 12:48 DEBUG  TaskList: ## Running Remove registry key...
06-12 12:48 DEBUG  TaskList: ## Finished Remove registry key
06-12 12:48 DEBUG  TaskList: # Finished tasklist
06-12 12:48 INFO   root: Almost finished uninstalling
06-12 12:48 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
06-12 12:48 INFO   root: Finished uninstallation
06-12 12:48 DEBUG  root: application.quit
06-12 12:48 DEBUG  WindowsFrontend: frontend.quit
06-12 12:48 DEBUG  WindowsFrontend: frontend.on_quit
06-12 12:48 DEBUG  root: application.on_quit
06-12 12:48 INFO   root: sys.exit
06-13 12:23 INFO   root: === wubi 11.04 rev211 ===
06-13 12:23 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
06-13 12:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
06-13 12:23 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\data
06-13 12:23 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\bin\7z.exe
06-13 12:23 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users.WINNT\Start Menu\Programs\Startup
06-13 12:23 DEBUG  CommonBackend: Fetching basic info...
06-13 12:23 DEBUG  CommonBackend: original_exe=D:\wubi.exe
06-13 12:23 DEBUG  CommonBackend: platform=win32
06-13 12:23 DEBUG  CommonBackend: osname=nt
06-13 12:23 DEBUG  CommonBackend: language=en_US
06-13 12:23 DEBUG  CommonBackend: encoding=cp1252
06-13 12:23 DEBUG  WindowsBackend: arch=amd64
06-13 12:23 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\data\isolist.ini
06-13 12:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-13 12:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-13 12:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-13 12:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-13 12:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-13 12:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-13 12:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-13 12:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-13 12:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-13 12:23 DEBUG  WindowsBackend: Fetching host info...
06-13 12:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-13 12:23 DEBUG  WindowsBackend: windows version=2000
06-13 12:23 DEBUG  WindowsBackend: windows_version2=Microsoft Windows 2000
06-13 12:23 DEBUG  WindowsBackend: windows_sp=Service Pack 4
06-13 12:23 DEBUG  WindowsBackend: windows_build=2195
06-13 12:23 DEBUG  WindowsBackend: gmt=-5
06-13 12:23 DEBUG  WindowsBackend: country=US
06-13 12:23 DEBUG  WindowsBackend: timezone=America/New_York
06-13 12:23 DEBUG  WindowsBackend: windows_username=Administrator
06-13 12:23 DEBUG  WindowsBackend: user_full_name=Administrator
06-13 12:23 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
06-13 12:23 DEBUG  WindowsBackend: windows_language_code=1033
06-13 12:23 DEBUG  WindowsBackend: windows_language=English
06-13 12:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7400  @ 2.80GHz
06-13 12:23 DEBUG  WindowsBackend: bootloader=xp
06-13 12:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 123193.128906 mb free ntfs)
06-13 12:23 DEBUG  WindowsBackend: drive=Drive(C: hd 123193.128906 mb free ntfs)
06-13 12:23 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
06-13 12:23 DEBUG  WindowsBackend: drive=Drive(E: hd 99181.515625 mb free ntfs)
06-13 12:23 DEBUG  WindowsBackend: drive=Drive(F: hd 74111.3671875 mb free ntfs)
06-13 12:23 DEBUG  WindowsBackend: drive=Drive(G: hd 9407.91796875 mb free ntfs)
06-13 12:23 DEBUG  WindowsBackend: uninstaller_path=None
06-13 12:23 DEBUG  WindowsBackend: previous_target_dir=None
06-13 12:23 DEBUG  WindowsBackend: previous_distro_name=None
06-13 12:23 DEBUG  WindowsBackend: keyboard_id=67699721
06-13 12:23 DEBUG  WindowsBackend: keyboard_layout=us
06-13 12:23 DEBUG  WindowsBackend: keyboard_variant=
06-13 12:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-13 12:23 DEBUG  CommonBackend: locale=en_US.UTF-8
06-13 12:23 DEBUG  WindowsBackend: total_memory_mb=2046.23046875
06-13 12:23 DEBUG  CommonBackend: Searching ISOs on USB devices
06-13 12:23 DEBUG  CommonBackend: Searching for local CDs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Ubuntu CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Ubuntu CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Ubuntu Netbook CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Kubuntu CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Kubuntu CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Xubuntu CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Xubuntu CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Mythbuntu CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp is a valid Mythbuntu CD
06-13 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\casper\filesystem.squashfs
06-13 12:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-13 12:23 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
06-13 12:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
06-13 12:23 INFO   Distro: Found a valid CD for Ubuntu: D:\
06-13 12:23 INFO   root: Running the CD menu...
06-13 12:23 DEBUG  WindowsFrontend: __init__...
06-13 12:23 DEBUG  WindowsFrontend: on_init...
06-13 12:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\translations, languages=['en_US', 'en']
06-13 12:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\translations, languages=['en_US', 'en']
06-13 12:24 INFO   root: CD menu finished
06-13 12:24 INFO   root: Running the installer...
06-13 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\translations, languages=['en_US', 'en']
06-13 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\translations, languages=['en_US', 'en']
06-13 12:25 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
06-13 12:25 INFO   root: Received settings
06-13 12:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\translations, languages=['en_US', 'en']
06-13 12:25 DEBUG  TaskList: # Running tasklist...
06-13 12:25 DEBUG  TaskList: ## Running select_target_dir...
06-13 12:25 INFO   WindowsBackend: Installing into F:\ubuntu
06-13 12:25 DEBUG  TaskList: ## Finished select_target_dir
06-13 12:25 DEBUG  TaskList: ## Running create_dir_structure...
06-13 12:25 DEBUG  CommonBackend: Creating dir F:\ubuntu
06-13 12:25 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks
06-13 12:25 DEBUG  CommonBackend: Creating dir F:\ubuntu\install
06-13 12:25 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot
06-13 12:25 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot
06-13 12:25 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot\grub
06-13 12:25 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot\grub
06-13 12:25 DEBUG  TaskList: ## Finished create_dir_structure
06-13 12:25 DEBUG  TaskList: ## Running uncompress_target_dir...
06-13 12:25 DEBUG  TaskList: ## Finished uncompress_target_dir
06-13 12:25 DEBUG  TaskList: ## Running create_uninstaller...
06-13 12:25 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> F:\ubuntu\uninstall-wubi.exe
06-13 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString F:\ubuntu\uninstall-wubi.exe
06-13 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir F:\ubuntu
06-13 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-13 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon F:\ubuntu\Ubuntu.ico
06-13 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
06-13 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-13 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-13 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-13 12:25 DEBUG  TaskList: ## Finished create_uninstaller
06-13 12:25 DEBUG  TaskList: ## Running copy_installation_files...
06-13 12:25 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\data\custom-installation -> F:\ubuntu\install\custom-installation
06-13 12:25 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\winboot -> F:\ubuntu\winboot
06-13 12:25 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4F.tmp\data\images\Ubuntu.ico -> F:\ubuntu\Ubuntu.ico
06-13 12:25 DEBUG  TaskList: ## Finished copy_installation_files
06-13 12:25 DEBUG  TaskList: ## Running get_iso...
06-13 12:25 DEBUG  TaskList: New task copy_file
06-13 12:25 DEBUG  TaskList: ### Running copy_file...
06-13 12:29 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
06-13 12:29 DEBUG  TaskList: # Cancelling tasklist
06-13 12:29 DEBUG  TaskList: New task check_iso
06-13 12:29 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
06-13 12:29 DEBUG  CommonBackend: Searching for local ISO
06-13 12:29 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-13 12:29 DEBUG  TaskList: New task get_metalink
06-13 12:29 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-13 12:29 DEBUG  TaskList: # Cancelling tasklist
06-13 12:29 DEBUG  TaskList: # Finished tasklist

---

### Post by Rubi1200 on 2011-06-13
Hi and welcome to the forums bitswap :-)

I suggest you download the wubi.exe for this version and place that together with the ISO image in the same folder. Then run the executable.

For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

Hopefully, that should solve the problem.



Thanks.

---

### Post by bitswap on 2011-06-13
It sounds like the wubi that comes with the installation iso is defective. How do I know the link you provided to wubi is the right corrected version? And I don't recall an option when running the wubi to pick a particular iso. When I ran the wubi standalone before, it went out and downloaded a new iso. I had the iso stored on a flashdrive, and it didn't give me a choice of where to load from.

---

### Post by Rubi1200 on 2011-06-15
You can check the integrity of the files:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Unless there is some problem we are not aware of, placing the wubi.exe and the correct downloaded ISO image in the same folder should resolve 99% of problems like these.

---

