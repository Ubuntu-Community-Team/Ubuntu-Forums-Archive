---
title: "Empty Desktop with WUBI-pwconv"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by JUKL on 2012-02-22
Hi all,
i installed UBUNTU with WUBI. When I boot with UBUNTU i have the following problem:
It give an error pwconv: "pwconv: failed to change the mode of /etc/passwd- to 0600" but UBUNTO is loaded, after entering the password i have an background picture but can not interact with the computer at all. I can move the mouse, but no icons, nothing. Also i can not shutdown the computer or restart it. Only unplugging helps. 
Any suggestions would be great
Thanks

---

### Post by bcbc on 2012-02-22
Please boot windows and attach the wubi log (it's in the %TEMP% directory). This will show how you installed and what release you are running etc.

PS you can reboot without unplugging using [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#.E2.80.9CREISUB.E2.80.9D_.E2.80.93_safe_reboot")

---

### Post by JUKL on 2012-02-23
Hi, attached log file wubi-11.10-rev245.log

02-21 14:26 INFO   root: === wubi 11.10 rev245 ===
02-21 14:26 DEBUG  root: Logfile is c:\docume~1\klausj\locals~1\temp\wubi-11.10-rev245.log
02-21 14:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="\\\\Picea\\home\\klausj\\docs\\Downloads\\wubi.exe"']
02-21 14:26 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\data
02-21 14:26 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\bin\7z.exe
02-21 14:26 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-21 14:26 DEBUG  CommonBackend: Fetching basic info...
02-21 14:26 DEBUG  CommonBackend: original_exe=\\Picea\home\klausj\docs\Downloads\wubi.exe
02-21 14:26 DEBUG  CommonBackend: platform=win32
02-21 14:26 DEBUG  CommonBackend: osname=nt
02-21 14:26 DEBUG  CommonBackend: language=en_US
02-21 14:26 DEBUG  CommonBackend: encoding=cp1252
02-21 14:26 DEBUG  WindowsBackend: arch=amd64
02-21 14:26 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\data\isolist.ini
02-21 14:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-21 14:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-21 14:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-21 14:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-21 14:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-21 14:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-21 14:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-21 14:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-21 14:26 DEBUG  WindowsBackend: Fetching host info...
02-21 14:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-21 14:26 DEBUG  WindowsBackend: windows version=xp
02-21 14:26 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-21 14:26 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-21 14:26 DEBUG  WindowsBackend: windows_build=2600
02-21 14:26 DEBUG  WindowsBackend: gmt=-8
02-21 14:26 DEBUG  WindowsBackend: country=US
02-21 14:26 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-21 14:26 DEBUG  WindowsBackend: windows_username=klausj
02-21 14:26 DEBUG  WindowsBackend: user_full_name=klausj
02-21 14:26 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\klausj
02-21 14:26 DEBUG  WindowsBackend: windows_language_code=1033
02-21 14:26 DEBUG  WindowsBackend: windows_language=English
02-21 14:26 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-21 14:26 DEBUG  WindowsBackend: bootloader=xp
02-21 14:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 120045.476563 mb free ntfs)
02-21 14:26 DEBUG  WindowsBackend: drive=Drive(C: hd 120045.476563 mb free ntfs)
02-21 14:26 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-21 14:26 DEBUG  WindowsBackend: uninstaller_path=None
02-21 14:26 DEBUG  WindowsBackend: previous_target_dir=None
02-21 14:26 DEBUG  WindowsBackend: previous_distro_name=None
02-21 14:26 DEBUG  WindowsBackend: keyboard_id=67699721
02-21 14:26 DEBUG  WindowsBackend: keyboard_layout=us
02-21 14:26 DEBUG  WindowsBackend: keyboard_variant=
02-21 14:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-21 14:26 DEBUG  CommonBackend: locale=en_US.UTF-8
02-21 14:26 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-21 14:26 DEBUG  CommonBackend: Searching ISOs on USB devices
02-21 14:26 DEBUG  CommonBackend: Searching for local CDs
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Ubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Ubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Kubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Kubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Xubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Xubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Mythbuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Mythbuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 INFO   root: Running the installer...
02-21 14:26 DEBUG  WindowsFrontend: __init__...
02-21 14:26 DEBUG  WindowsFrontend: on_init...
02-21 14:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\translations, languages=['en_US', 'en']
02-21 14:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\translations, languages=['en_US', 'en']
02-21 14:26 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=klausj
02-21 14:26 INFO   root: Received settings
02-21 14:26 DEBUG  CommonBackend: Searching for local CD
02-21 14:26 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Ubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-21 14:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 14:26 DEBUG  CommonBackend: Searching for local ISO
02-21 14:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\translations, languages=['en_US', 'en']
02-21 14:26 DEBUG  TaskList: # Running tasklist...
02-21 14:26 DEBUG  TaskList: ## Running select_target_dir...
02-21 14:26 INFO   WindowsBackend: Installing into C:\ubuntu
02-21 14:26 DEBUG  TaskList: ## Finished select_target_dir
02-21 14:26 DEBUG  TaskList: ## Running create_dir_structure...
02-21 14:26 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-21 14:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-21 14:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-21 14:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-21 14:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-21 14:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-21 14:26 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-21 14:26 DEBUG  TaskList: ## Finished create_dir_structure
02-21 14:26 DEBUG  TaskList: ## Running create_uninstaller...
02-21 14:26 DEBUG  WindowsBackend: Copying uninstaller \\Picea\home\klausj\docs\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-21 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-21 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-21 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-21 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-21 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-21 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-21 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-21 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-21 14:26 DEBUG  TaskList: ## Finished create_uninstaller
02-21 14:26 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-21 14:26 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-21 14:26 DEBUG  TaskList: ## Running get_diskimage...
02-21 14:26 DEBUG  TaskList: New task download
02-21 14:26 DEBUG  TaskList: ### Running download...
02-21 14:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-21 14:26 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-21 14:48 DEBUG  TaskList: ### Finished download
02-21 14:48 DEBUG  downloader: download finished (read 507143012 bytes)
02-21 14:48 DEBUG  TaskList: ## Finished get_diskimage
02-21 14:48 DEBUG  TaskList: ## Running extract_diskimage...
02-21 14:50 DEBUG  TaskList: ## Finished extract_diskimage
02-21 14:50 DEBUG  TaskList: ## Running choose_disk_sizes...
02-21 14:50 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-21 14:50 DEBUG  TaskList: ## Finished choose_disk_sizes
02-21 14:50 DEBUG  TaskList: ## Running expand_diskimage...
02-21 14:52 DEBUG  TaskList: ## Finished expand_diskimage
02-21 14:52 DEBUG  TaskList: ## Running create_swap_diskimage...
02-21 14:52 ERROR  TaskList: Error executing command
>>command=fsutil file createnew C:\ubuntu\disks\swap.disk 268435456
>>retval=1
>>stderr=The FSUTIL utility requires that you have administrative privileges.



>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 468, in create_swap_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=fsutil file createnew C:\ubuntu\disks\swap.disk 268435456
>>retval=1
>>stderr=The FSUTIL utility requires that you have administrative privileges.



>>stdout=
02-21 14:52 DEBUG  TaskList: # Cancelling tasklist
02-21 14:52 DEBUG  TaskList: # Finished tasklist
02-21 14:52 ERROR  root: Error executing command
>>command=fsutil file createnew C:\ubuntu\disks\swap.disk 268435456
>>retval=1
>>stderr=The FSUTIL utility requires that you have administrative privileges.



>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 468, in create_swap_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=fsutil file createnew C:\ubuntu\disks\swap.disk 268435456
>>retval=1
>>stderr=The FSUTIL utility requires that you have administrative privileges.



>>stdout=
02-21 15:04 INFO   root: === wubi 11.10 rev245 ===
02-21 15:04 DEBUG  root: Logfile is c:\docume~1\klausj\locals~1\temp\wubi-11.10-rev245.log
02-21 15:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="\\\\Picea\\home\\klausj\\docs\\Downloads\\wubi(1).exe"']
02-21 15:04 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\data
02-21 15:04 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\bin\7z.exe
02-21 15:04 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-21 15:04 DEBUG  CommonBackend: Fetching basic info...
02-21 15:04 DEBUG  CommonBackend: original_exe=\\Picea\home\klausj\docs\Downloads\wubi(1).exe
02-21 15:04 DEBUG  CommonBackend: platform=win32
02-21 15:04 DEBUG  CommonBackend: osname=nt
02-21 15:04 DEBUG  CommonBackend: language=en_US
02-21 15:04 DEBUG  CommonBackend: encoding=cp1252
02-21 15:04 DEBUG  WindowsBackend: arch=amd64
02-21 15:04 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\data\isolist.ini
02-21 15:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-21 15:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-21 15:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-21 15:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-21 15:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-21 15:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-21 15:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-21 15:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-21 15:04 DEBUG  WindowsBackend: Fetching host info...
02-21 15:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-21 15:04 DEBUG  WindowsBackend: windows version=xp
02-21 15:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-21 15:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-21 15:04 DEBUG  WindowsBackend: windows_build=2600
02-21 15:04 DEBUG  WindowsBackend: gmt=-8
02-21 15:04 DEBUG  WindowsBackend: country=US
02-21 15:04 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-21 15:04 DEBUG  WindowsBackend: windows_username=klausj
02-21 15:04 DEBUG  WindowsBackend: user_full_name=klausj
02-21 15:04 DEBUG  WindowsBackend: user_directory=N:\
02-21 15:04 DEBUG  WindowsBackend: windows_language_code=1033
02-21 15:04 DEBUG  WindowsBackend: windows_language=English
02-21 15:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-21 15:04 DEBUG  WindowsBackend: bootloader=xp
02-21 15:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 115956.066406 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(C: hd 115956.066406 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(N: remote 4528174.74609 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(Q: remote 45952.4648438 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(S: remote 10828056.2813 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(T: remote 101114.554688 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-21 15:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-21 15:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-21 15:04 DEBUG  WindowsBackend: keyboard_id=67699721
02-21 15:04 DEBUG  WindowsBackend: keyboard_layout=us
02-21 15:04 DEBUG  WindowsBackend: keyboard_variant=
02-21 15:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-21 15:04 DEBUG  CommonBackend: locale=en_US.UTF-8
02-21 15:04 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-21 15:04 DEBUG  CommonBackend: Searching ISOs on USB devices
02-21 15:04 DEBUG  CommonBackend: Searching for local CDs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 INFO   root: Already installed, running the uninstaller...
02-21 15:04 INFO   root: Running the uninstaller...
02-21 15:04 INFO   CommonBackend: This is the uninstaller running
02-21 15:04 DEBUG  WindowsFrontend: __init__...
02-21 15:04 DEBUG  WindowsFrontend: on_init...
02-21 15:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\translations, languages=['en_US', 'en']
02-21 15:04 INFO   root: Received settings
02-21 15:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\translations, languages=['en_US', 'en']
02-21 15:04 DEBUG  TaskList: # Running tasklist...
02-21 15:04 DEBUG  TaskList: ## Running Remove bootloader entry...
02-21 15:04 ERROR  WindowsBackend: Cannot find bcdedit
02-21 15:04 DEBUG  WindowsBackend: undo_bootini C:
02-21 15:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 115956.066406 mb free ntfs)
02-21 15:04 DEBUG  TaskList: ## Finished Remove bootloader entry
02-21 15:04 DEBUG  TaskList: ## Running Remove target dir...
02-21 15:04 DEBUG  CommonBackend: Deleting C:\ubuntu
02-21 15:04 DEBUG  TaskList: ## Finished Remove target dir
02-21 15:04 DEBUG  TaskList: ## Running Remove registry key...
02-21 15:04 DEBUG  TaskList: ## Finished Remove registry key
02-21 15:04 DEBUG  TaskList: # Finished tasklist
02-21 15:04 INFO   root: Almost finished uninstalling
02-21 15:04 INFO   root: Finished uninstallation
02-21 15:04 DEBUG  CommonBackend: Fetching basic info...
02-21 15:04 DEBUG  CommonBackend: original_exe=\\Picea\home\klausj\docs\Downloads\wubi(1).exe
02-21 15:04 DEBUG  CommonBackend: platform=win32
02-21 15:04 DEBUG  CommonBackend: osname=nt
02-21 15:04 DEBUG  WindowsBackend: arch=amd64
02-21 15:04 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\data\isolist.ini
02-21 15:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-21 15:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-21 15:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-21 15:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-21 15:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-21 15:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-21 15:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-21 15:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-21 15:04 DEBUG  WindowsBackend: Fetching host info...
02-21 15:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-21 15:04 DEBUG  WindowsBackend: windows version=xp
02-21 15:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-21 15:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-21 15:04 DEBUG  WindowsBackend: windows_build=2600
02-21 15:04 DEBUG  WindowsBackend: gmt=-8
02-21 15:04 DEBUG  WindowsBackend: country=US
02-21 15:04 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-21 15:04 DEBUG  WindowsBackend: windows_username=klausj
02-21 15:04 DEBUG  WindowsBackend: user_full_name=klausj
02-21 15:04 DEBUG  WindowsBackend: user_directory=N:\
02-21 15:04 DEBUG  WindowsBackend: windows_language_code=1033
02-21 15:04 DEBUG  WindowsBackend: windows_language=English
02-21 15:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-21 15:04 DEBUG  WindowsBackend: bootloader=xp
02-21 15:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 120033.21875 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(C: hd 120033.21875 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(N: remote 4528174.74609 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(Q: remote 45952.4648438 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(S: remote 10828060.4063 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: drive=Drive(T: remote 101114.554688 mb free ntfs)
02-21 15:04 DEBUG  WindowsBackend: uninstaller_path=None
02-21 15:04 DEBUG  WindowsBackend: previous_target_dir=None
02-21 15:04 DEBUG  WindowsBackend: previous_distro_name=None
02-21 15:04 DEBUG  WindowsBackend: keyboard_id=67699721
02-21 15:04 DEBUG  WindowsBackend: keyboard_layout=us
02-21 15:04 DEBUG  WindowsBackend: keyboard_variant=
02-21 15:04 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-21 15:04 DEBUG  CommonBackend: Searching ISOs on USB devices
02-21 15:04 DEBUG  CommonBackend: Searching for local CDs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-21 15:04 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:04 INFO   root: Running the installer...
02-21 15:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\translations, languages=['en_US', 'en']
02-21 15:04 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\translations, languages=['en_US', 'en']
02-21 15:05 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=klausj
02-21 15:05 INFO   root: Received settings
02-21 15:05 DEBUG  CommonBackend: Searching for local CD
02-21 15:05 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp is a valid Ubuntu CD
02-21 15:05 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\casper\filesystem.squashfs
02-21 15:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 15:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 15:05 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-21 15:05 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 15:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-21 15:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 15:05 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-21 15:05 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 15:05 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-21 15:05 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 15:05 DEBUG  CommonBackend: Searching for local ISO
02-21 15:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\translations, languages=['en_US', 'en']
02-21 15:05 DEBUG  TaskList: # Running tasklist...
02-21 15:05 DEBUG  TaskList: ## Running select_target_dir...
02-21 15:05 INFO   WindowsBackend: Installing into C:\ubuntu
02-21 15:05 DEBUG  TaskList: ## Finished select_target_dir
02-21 15:05 DEBUG  TaskList: ## Running create_dir_structure...
02-21 15:05 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-21 15:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-21 15:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-21 15:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-21 15:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-21 15:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-21 15:05 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-21 15:05 DEBUG  TaskList: ## Finished create_dir_structure
02-21 15:05 DEBUG  TaskList: ## Running create_uninstaller...
02-21 15:05 DEBUG  WindowsBackend: Copying uninstaller \\Picea\home\klausj\docs\Downloads\wubi(1).exe -> C:\ubuntu\uninstall-wubi.exe
02-21 15:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-21 15:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-21 15:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-21 15:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-21 15:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-21 15:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-21 15:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-21 15:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-21 15:05 DEBUG  TaskList: ## Finished create_uninstaller
02-21 15:05 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-21 15:05 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-21 15:05 DEBUG  TaskList: ## Running get_diskimage...
02-21 15:05 DEBUG  TaskList: New task download
02-21 15:05 DEBUG  TaskList: ### Running download...
02-21 15:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-21 15:05 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-21 15:26 DEBUG  TaskList: ### Finished download
02-21 15:26 DEBUG  downloader: download finished (read 507143012 bytes)
02-21 15:26 DEBUG  TaskList: ## Finished get_diskimage
02-21 15:26 DEBUG  TaskList: ## Running extract_diskimage...
02-21 15:29 DEBUG  TaskList: ## Finished extract_diskimage
02-21 15:29 DEBUG  TaskList: ## Running choose_disk_sizes...
02-21 15:29 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-21 15:29 DEBUG  TaskList: ## Finished choose_disk_sizes
02-21 15:29 DEBUG  TaskList: ## Running expand_diskimage...
02-21 15:34 DEBUG  TaskList: ## Finished expand_diskimage
02-21 15:34 DEBUG  TaskList: ## Running create_swap_diskimage...
02-21 15:34 DEBUG  TaskList: ## Finished create_swap_diskimage
02-21 15:34 DEBUG  TaskList: ## Running modify_bootloader...
02-21 15:34 DEBUG  TaskList: New task modify_bootini
02-21 15:34 DEBUG  TaskList: ### Running modify_bootini...
02-21 15:34 DEBUG  WindowsBackend: modify_bootini C:
02-21 15:34 DEBUG  TaskList: ### Finished modify_bootini
02-21 15:34 DEBUG  TaskList: ## Finished modify_bootloader
02-21 15:34 DEBUG  TaskList: ## Running diskimage_bootloader...
02-21 15:34 DEBUG  WindowsBackend: Copying C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\winboot -> C:\ubuntu\winboot
02-21 15:34 DEBUG  TaskList: ## Finished diskimage_bootloader
02-21 15:34 DEBUG  TaskList: # Finished tasklist
02-21 15:34 INFO   root: Almost finished installing
02-21 15:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl2F.tmp\translations, languages=['en_US', 'en']
02-21 15:36 INFO   root: Finished installation
02-21 15:36 DEBUG  root: application.quit
02-21 15:36 DEBUG  WindowsFrontend: frontend.quit
02-21 15:36 DEBUG  WindowsFrontend: frontend.on_quit
02-21 15:36 DEBUG  root: application.on_quit
02-21 15:36 INFO   root: sys.exit
02-21 16:27 INFO   root: === wubi 11.10 rev245 ===
02-21 16:27 DEBUG  root: Logfile is c:\docume~1\klausj\locals~1\temp\wubi-11.10-rev245.log
02-21 16:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-21 16:27 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\data
02-21 16:27 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\bin\7z.exe
02-21 16:27 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-21 16:27 DEBUG  CommonBackend: Fetching basic info...
02-21 16:27 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-21 16:27 DEBUG  CommonBackend: platform=win32
02-21 16:27 DEBUG  CommonBackend: osname=nt
02-21 16:27 DEBUG  CommonBackend: language=en_US
02-21 16:27 DEBUG  CommonBackend: encoding=cp1252
02-21 16:27 DEBUG  WindowsBackend: arch=amd64
02-21 16:27 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\data\isolist.ini
02-21 16:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-21 16:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-21 16:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-21 16:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-21 16:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-21 16:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-21 16:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-21 16:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-21 16:27 DEBUG  WindowsBackend: Fetching host info...
02-21 16:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-21 16:27 DEBUG  WindowsBackend: windows version=xp
02-21 16:27 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-21 16:27 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-21 16:27 DEBUG  WindowsBackend: windows_build=2600
02-21 16:27 DEBUG  WindowsBackend: gmt=-8
02-21 16:27 DEBUG  WindowsBackend: country=US
02-21 16:27 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-21 16:27 DEBUG  WindowsBackend: windows_username=klausj
02-21 16:27 DEBUG  WindowsBackend: user_full_name=klausj
02-21 16:27 DEBUG  WindowsBackend: user_directory=N:\
02-21 16:27 DEBUG  WindowsBackend: windows_language_code=1033
02-21 16:27 DEBUG  WindowsBackend: windows_language=English
02-21 16:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-21 16:27 DEBUG  WindowsBackend: bootloader=xp
02-21 16:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 116751.433594 mb free ntfs)
02-21 16:27 DEBUG  WindowsBackend: drive=Drive(C: hd 116751.433594 mb free ntfs)
02-21 16:27 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-21 16:27 DEBUG  WindowsBackend: drive=Drive(N: remote 4527976.46094 mb free ntfs)
02-21 16:27 DEBUG  WindowsBackend: drive=Drive(Q: remote 45952.4023438 mb free ntfs)
02-21 16:27 DEBUG  WindowsBackend: drive=Drive(S: remote 10827974.7578 mb free ntfs)
02-21 16:27 DEBUG  WindowsBackend: drive=Drive(T: remote 101115.464844 mb free ntfs)
02-21 16:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-21 16:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-21 16:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-21 16:27 DEBUG  WindowsBackend: keyboard_id=67699721
02-21 16:27 DEBUG  WindowsBackend: keyboard_layout=us
02-21 16:27 DEBUG  WindowsBackend: keyboard_variant=
02-21 16:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-21 16:27 DEBUG  CommonBackend: locale=en_US.UTF-8
02-21 16:27 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-21 16:27 DEBUG  CommonBackend: Searching ISOs on USB devices
02-21 16:27 DEBUG  CommonBackend: Searching for local CDs
02-21 16:27 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-21 16:27 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 16:27 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-21 16:27 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-21 16:27 INFO   root: Running the uninstaller...
02-21 16:27 INFO   CommonBackend: This is the uninstaller running
02-21 16:27 DEBUG  WindowsFrontend: __init__...
02-21 16:27 DEBUG  WindowsFrontend: on_init...
02-21 16:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\translations, languages=['en_US', 'en']
02-21 16:27 INFO   root: Received settings
02-21 16:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\translations, languages=['en_US', 'en']
02-21 16:27 DEBUG  TaskList: # Running tasklist...
02-21 16:27 DEBUG  TaskList: ## Running Remove bootloader entry...
02-21 16:27 ERROR  WindowsBackend: Cannot find bcdedit
02-21 16:27 DEBUG  WindowsBackend: undo_bootini C:
02-21 16:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 116751.433594 mb free ntfs)
02-21 16:27 DEBUG  TaskList: ## Finished Remove bootloader entry
02-21 16:27 DEBUG  TaskList: ## Running Remove target dir...
02-21 16:27 DEBUG  CommonBackend: Deleting C:\ubuntu
02-21 16:27 DEBUG  TaskList: ## Finished Remove target dir
02-21 16:27 DEBUG  TaskList: ## Running Remove registry key...
02-21 16:27 DEBUG  TaskList: ## Finished Remove registry key
02-21 16:27 DEBUG  TaskList: # Finished tasklist
02-21 16:27 INFO   root: Almost finished uninstalling
02-21 16:27 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1C.tmp\translations, languages=['en_US', 'en']
02-21 16:27 INFO   root: Finished uninstallation
02-21 16:27 DEBUG  root: application.quit
02-21 16:27 DEBUG  WindowsFrontend: frontend.quit
02-21 16:27 DEBUG  WindowsFrontend: frontend.on_quit
02-21 16:27 DEBUG  root: application.on_quit
02-21 16:27 INFO   root: sys.exit
02-22 10:45 INFO   root: === wubi 11.10 rev245 ===
02-22 10:45 DEBUG  root: Logfile is c:\docume~1\klausj\locals~1\temp\wubi-11.10-rev245.log
02-22 10:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="\\\\Picea\\home\\klausj\\docs\\Downloads\\wubi.exe"']
02-22 10:45 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\data
02-22 10:45 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\bin\7z.exe
02-22 10:45 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-22 10:45 DEBUG  CommonBackend: Fetching basic info...
02-22 10:45 DEBUG  CommonBackend: original_exe=\\Picea\home\klausj\docs\Downloads\wubi.exe
02-22 10:45 DEBUG  CommonBackend: platform=win32
02-22 10:45 DEBUG  CommonBackend: osname=nt
02-22 10:45 DEBUG  CommonBackend: language=en_US
02-22 10:45 DEBUG  CommonBackend: encoding=cp1252
02-22 10:45 DEBUG  WindowsBackend: arch=amd64
02-22 10:45 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\data\isolist.ini
02-22 10:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-22 10:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-22 10:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-22 10:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-22 10:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-22 10:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-22 10:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-22 10:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-22 10:45 DEBUG  WindowsBackend: Fetching host info...
02-22 10:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-22 10:45 DEBUG  WindowsBackend: windows version=xp
02-22 10:45 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-22 10:45 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-22 10:45 DEBUG  WindowsBackend: windows_build=2600
02-22 10:45 DEBUG  WindowsBackend: gmt=-8
02-22 10:45 DEBUG  WindowsBackend: country=US
02-22 10:45 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-22 10:45 DEBUG  WindowsBackend: windows_username=klausj
02-22 10:45 DEBUG  WindowsBackend: user_full_name=klausj
02-22 10:45 DEBUG  WindowsBackend: user_directory=N:\
02-22 10:45 DEBUG  WindowsBackend: windows_language_code=1033
02-22 10:45 DEBUG  WindowsBackend: windows_language=English
02-22 10:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-22 10:45 DEBUG  WindowsBackend: bootloader=xp
02-22 10:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119800.710938 mb free ntfs)
02-22 10:45 DEBUG  WindowsBackend: drive=Drive(C: hd 119800.710938 mb free ntfs)
02-22 10:45 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-22 10:45 DEBUG  WindowsBackend: drive=Drive(N: remote 4525690.19141 mb free ntfs)
02-22 10:45 DEBUG  WindowsBackend: drive=Drive(Q: remote 7742.83203125 mb free ntfs)
02-22 10:45 DEBUG  WindowsBackend: drive=Drive(S: remote 10824325.8203 mb free ntfs)
02-22 10:45 DEBUG  WindowsBackend: drive=Drive(T: remote 100564.734375 mb free ntfs)
02-22 10:45 DEBUG  WindowsBackend: uninstaller_path=None
02-22 10:45 DEBUG  WindowsBackend: previous_target_dir=None
02-22 10:45 DEBUG  WindowsBackend: previous_distro_name=None
02-22 10:45 DEBUG  WindowsBackend: keyboard_id=67699721
02-22 10:45 DEBUG  WindowsBackend: keyboard_layout=us
02-22 10:45 DEBUG  WindowsBackend: keyboard_variant=
02-22 10:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-22 10:45 DEBUG  CommonBackend: locale=en_US.UTF-8
02-22 10:45 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-22 10:45 DEBUG  CommonBackend: Searching ISOs on USB devices
02-22 10:45 DEBUG  CommonBackend: Searching for local CDs
02-22 10:45 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 10:45 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:45 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 10:45 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:45 INFO   root: Running the installer...
02-22 10:45 DEBUG  WindowsFrontend: __init__...
02-22 10:45 DEBUG  WindowsFrontend: on_init...
02-22 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\translations, languages=['en_US', 'en']
02-22 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\translations, languages=['en_US', 'en']
02-22 10:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=klausj
02-22 10:46 INFO   root: Received settings
02-22 10:46 DEBUG  CommonBackend: Searching for local CD
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  CommonBackend: Searching for local ISO
02-22 10:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1B.tmp\translations, languages=['en_US', 'en']
02-22 10:46 DEBUG  TaskList: # Running tasklist...
02-22 10:46 DEBUG  TaskList: ## Running select_target_dir...
02-22 10:46 INFO   WindowsBackend: Installing into C:\ubuntu
02-22 10:46 DEBUG  TaskList: ## Finished select_target_dir
02-22 10:46 DEBUG  TaskList: ## Running create_dir_structure...
02-22 10:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-22 10:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-22 10:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-22 10:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-22 10:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-22 10:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-22 10:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-22 10:46 DEBUG  TaskList: ## Finished create_dir_structure
02-22 10:46 DEBUG  TaskList: ## Running create_uninstaller...
02-22 10:46 DEBUG  WindowsBackend: Copying uninstaller \\Picea\home\klausj\docs\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-22 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-22 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-22 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-22 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-22 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-22 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-22 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-22 10:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-22 10:46 DEBUG  TaskList: ## Finished create_uninstaller
02-22 10:46 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-22 10:46 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-22 10:46 DEBUG  TaskList: ## Running get_diskimage...
02-22 10:46 DEBUG  TaskList: New task download
02-22 10:46 DEBUG  TaskList: ### Running download...
02-22 10:46 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-22 10:46 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-22 10:46 INFO   WindowsFrontend: Operation cancelled
02-22 10:46 DEBUG  WindowsFrontend: frontend.quit
02-22 10:46 DEBUG  WindowsFrontend: frontend.on_quit
02-22 10:46 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
02-22 10:46 DEBUG  TaskList: # Cancelling tasklist
02-22 10:46 DEBUG  downloader: download finished (read 2146304 bytes)
02-22 10:46 DEBUG  TaskList: ### Finished download
02-22 10:46 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
02-22 10:46 DEBUG  root: application.on_quit
02-22 10:46 DEBUG  root: Forceful exit
02-22 10:46 INFO   root: sys.exit
02-22 10:46 INFO   root: === wubi 11.10 rev245 ===
02-22 10:46 DEBUG  root: Logfile is c:\docume~1\klausj\locals~1\temp\wubi-11.10-rev245.log
02-22 10:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="\\\\Picea\\home\\klausj\\docs\\Downloads\\wubi.exe"']
02-22 10:46 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\data
02-22 10:46 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\bin\7z.exe
02-22 10:46 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-22 10:46 DEBUG  CommonBackend: Fetching basic info...
02-22 10:46 DEBUG  CommonBackend: original_exe=\\Picea\home\klausj\docs\Downloads\wubi.exe
02-22 10:46 DEBUG  CommonBackend: platform=win32
02-22 10:46 DEBUG  CommonBackend: osname=nt
02-22 10:46 DEBUG  CommonBackend: language=en_US
02-22 10:46 DEBUG  CommonBackend: encoding=cp1252
02-22 10:46 DEBUG  WindowsBackend: arch=amd64
02-22 10:46 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\data\isolist.ini
02-22 10:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-22 10:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-22 10:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-22 10:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-22 10:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-22 10:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-22 10:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-22 10:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-22 10:46 DEBUG  WindowsBackend: Fetching host info...
02-22 10:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-22 10:46 DEBUG  WindowsBackend: windows version=xp
02-22 10:46 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-22 10:46 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-22 10:46 DEBUG  WindowsBackend: windows_build=2600
02-22 10:46 DEBUG  WindowsBackend: gmt=-8
02-22 10:46 DEBUG  WindowsBackend: country=US
02-22 10:46 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-22 10:46 DEBUG  WindowsBackend: windows_username=klausj
02-22 10:46 DEBUG  WindowsBackend: user_full_name=klausj
02-22 10:46 DEBUG  WindowsBackend: user_directory=N:\
02-22 10:46 DEBUG  WindowsBackend: windows_language_code=1033
02-22 10:46 DEBUG  WindowsBackend: windows_language=English
02-22 10:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-22 10:46 DEBUG  WindowsBackend: bootloader=xp
02-22 10:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119787.722656 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(C: hd 119787.722656 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(N: remote 4525683.8125 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(Q: remote 7742.83203125 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(S: remote 10824321.0703 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(T: remote 100564.734375 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-22 10:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-22 10:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-22 10:46 DEBUG  WindowsBackend: keyboard_id=67699721
02-22 10:46 DEBUG  WindowsBackend: keyboard_layout=us
02-22 10:46 DEBUG  WindowsBackend: keyboard_variant=
02-22 10:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-22 10:46 DEBUG  CommonBackend: locale=en_US.UTF-8
02-22 10:46 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-22 10:46 DEBUG  CommonBackend: Searching ISOs on USB devices
02-22 10:46 DEBUG  CommonBackend: Searching for local CDs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 INFO   root: Already installed, running the uninstaller...
02-22 10:46 INFO   root: Running the uninstaller...
02-22 10:46 INFO   CommonBackend: This is the uninstaller running
02-22 10:46 DEBUG  WindowsFrontend: __init__...
02-22 10:46 DEBUG  WindowsFrontend: on_init...
02-22 10:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
02-22 10:46 INFO   root: Received settings
02-22 10:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
02-22 10:46 DEBUG  TaskList: # Running tasklist...
02-22 10:46 DEBUG  TaskList: ## Running Remove bootloader entry...
02-22 10:46 ERROR  WindowsBackend: Cannot find bcdedit
02-22 10:46 DEBUG  WindowsBackend: undo_bootini C:
02-22 10:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 119787.722656 mb free ntfs)
02-22 10:46 DEBUG  TaskList: ## Finished Remove bootloader entry
02-22 10:46 DEBUG  TaskList: ## Running Remove target dir...
02-22 10:46 DEBUG  CommonBackend: Deleting C:\ubuntu
02-22 10:46 DEBUG  TaskList: ## Finished Remove target dir
02-22 10:46 DEBUG  TaskList: ## Running Remove registry key...
02-22 10:46 DEBUG  TaskList: ## Finished Remove registry key
02-22 10:46 DEBUG  TaskList: # Finished tasklist
02-22 10:46 INFO   root: Almost finished uninstalling
02-22 10:46 INFO   root: Finished uninstallation
02-22 10:46 DEBUG  CommonBackend: Fetching basic info...
02-22 10:46 DEBUG  CommonBackend: original_exe=\\Picea\home\klausj\docs\Downloads\wubi.exe
02-22 10:46 DEBUG  CommonBackend: platform=win32
02-22 10:46 DEBUG  CommonBackend: osname=nt
02-22 10:46 DEBUG  WindowsBackend: arch=amd64
02-22 10:46 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\data\isolist.ini
02-22 10:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-22 10:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-22 10:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-22 10:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-22 10:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-22 10:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-22 10:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-22 10:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-22 10:46 DEBUG  WindowsBackend: Fetching host info...
02-22 10:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-22 10:46 DEBUG  WindowsBackend: windows version=xp
02-22 10:46 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-22 10:46 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-22 10:46 DEBUG  WindowsBackend: windows_build=2600
02-22 10:46 DEBUG  WindowsBackend: gmt=-8
02-22 10:46 DEBUG  WindowsBackend: country=US
02-22 10:46 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-22 10:46 DEBUG  WindowsBackend: windows_username=klausj
02-22 10:46 DEBUG  WindowsBackend: user_full_name=klausj
02-22 10:46 DEBUG  WindowsBackend: user_directory=N:\
02-22 10:46 DEBUG  WindowsBackend: windows_language_code=1033
02-22 10:46 DEBUG  WindowsBackend: windows_language=English
02-22 10:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-22 10:46 DEBUG  WindowsBackend: bootloader=xp
02-22 10:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119792.105469 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(C: hd 119792.105469 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(N: remote 4525683.8125 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(Q: remote 7742.83203125 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(S: remote 10824322.1094 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: drive=Drive(T: remote 100564.734375 mb free ntfs)
02-22 10:46 DEBUG  WindowsBackend: uninstaller_path=None
02-22 10:46 DEBUG  WindowsBackend: previous_target_dir=None
02-22 10:46 DEBUG  WindowsBackend: previous_distro_name=None
02-22 10:46 DEBUG  WindowsBackend: keyboard_id=67699721
02-22 10:46 DEBUG  WindowsBackend: keyboard_layout=us
02-22 10:46 DEBUG  WindowsBackend: keyboard_variant=
02-22 10:46 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-22 10:46 DEBUG  CommonBackend: Searching ISOs on USB devices
02-22 10:46 DEBUG  CommonBackend: Searching for local CDs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 10:46 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:46 INFO   root: Running the installer...
02-22 10:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
02-22 10:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
02-22 10:47 INFO   WindowsFrontend: Operation cancelled
02-22 10:47 DEBUG  WindowsFrontend: frontend.quit
02-22 10:47 DEBUG  WindowsFrontend: frontend.on_quit
02-22 10:47 DEBUG  root: application.on_quit
02-22 10:47 INFO   root: sys.exit
02-22 10:47 INFO   root: === wubi 11.10 rev245 ===
02-22 10:47 DEBUG  root: Logfile is c:\docume~1\klausj\locals~1\temp\wubi-11.10-rev245.log
02-22 10:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="\\\\Picea\\home\\klausj\\docs\\Downloads\\wubi.exe"']
02-22 10:47 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\data
02-22 10:47 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\bin\7z.exe
02-22 10:47 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-22 10:47 DEBUG  CommonBackend: Fetching basic info...
02-22 10:47 DEBUG  CommonBackend: original_exe=\\Picea\home\klausj\docs\Downloads\wubi.exe
02-22 10:47 DEBUG  CommonBackend: platform=win32
02-22 10:47 DEBUG  CommonBackend: osname=nt
02-22 10:47 DEBUG  CommonBackend: language=en_US
02-22 10:47 DEBUG  CommonBackend: encoding=cp1252
02-22 10:47 DEBUG  WindowsBackend: arch=amd64
02-22 10:47 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\data\isolist.ini
02-22 10:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-22 10:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-22 10:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-22 10:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-22 10:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-22 10:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-22 10:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-22 10:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-22 10:47 DEBUG  WindowsBackend: Fetching host info...
02-22 10:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-22 10:47 DEBUG  WindowsBackend: windows version=xp
02-22 10:47 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-22 10:47 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-22 10:47 DEBUG  WindowsBackend: windows_build=2600
02-22 10:47 DEBUG  WindowsBackend: gmt=-8
02-22 10:47 DEBUG  WindowsBackend: country=US
02-22 10:47 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-22 10:47 DEBUG  WindowsBackend: windows_username=klausj
02-22 10:47 DEBUG  WindowsBackend: user_full_name=klausj
02-22 10:47 DEBUG  WindowsBackend: user_directory=N:\
02-22 10:47 DEBUG  WindowsBackend: windows_language_code=1033
02-22 10:47 DEBUG  WindowsBackend: windows_language=English
02-22 10:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-22 10:47 DEBUG  WindowsBackend: bootloader=xp
02-22 10:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119783.898438 mb free ntfs)
02-22 10:47 DEBUG  WindowsBackend: drive=Drive(C: hd 119783.894531 mb free ntfs)
02-22 10:47 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-22 10:47 DEBUG  WindowsBackend: drive=Drive(N: remote 4525683.9375 mb free ntfs)
02-22 10:47 DEBUG  WindowsBackend: drive=Drive(Q: remote 7742.83203125 mb free ntfs)
02-22 10:47 DEBUG  WindowsBackend: drive=Drive(S: remote 10824323.1094 mb free ntfs)
02-22 10:47 DEBUG  WindowsBackend: drive=Drive(T: remote 100564.734375 mb free ntfs)
02-22 10:47 DEBUG  WindowsBackend: uninstaller_path=None
02-22 10:47 DEBUG  WindowsBackend: previous_target_dir=None
02-22 10:47 DEBUG  WindowsBackend: previous_distro_name=None
02-22 10:47 DEBUG  WindowsBackend: keyboard_id=67699721
02-22 10:47 DEBUG  WindowsBackend: keyboard_layout=us
02-22 10:47 DEBUG  WindowsBackend: keyboard_variant=
02-22 10:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-22 10:47 DEBUG  CommonBackend: locale=en_US.UTF-8
02-22 10:47 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-22 10:47 DEBUG  CommonBackend: Searching ISOs on USB devices
02-22 10:47 DEBUG  CommonBackend: Searching for local CDs
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 INFO   root: Running the installer...
02-22 10:47 DEBUG  WindowsFrontend: __init__...
02-22 10:47 DEBUG  WindowsFrontend: on_init...
02-22 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
02-22 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
02-22 10:47 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=klausj
02-22 10:47 INFO   root: Received settings
02-22 10:47 DEBUG  CommonBackend: Searching for local CD
02-22 10:47 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 10:47 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 10:47 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 10:47 DEBUG  CommonBackend: Searching for local ISO
02-22 10:47 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
02-22 10:47 DEBUG  TaskList: # Running tasklist...
02-22 10:47 DEBUG  TaskList: ## Running select_target_dir...
02-22 10:47 INFO   WindowsBackend: Installing into C:\ubuntu
02-22 10:47 DEBUG  TaskList: ## Finished select_target_dir
02-22 10:47 DEBUG  TaskList: ## Running create_dir_structure...
02-22 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-22 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-22 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-22 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-22 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-22 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-22 10:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-22 10:47 DEBUG  TaskList: ## Finished create_dir_structure
02-22 10:47 DEBUG  TaskList: ## Running create_uninstaller...
02-22 10:47 DEBUG  WindowsBackend: Copying uninstaller \\Picea\home\klausj\docs\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-22 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-22 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-22 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-22 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-22 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-22 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-22 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-22 10:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-22 10:47 DEBUG  TaskList: ## Finished create_uninstaller
02-22 10:47 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-22 10:47 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-22 10:47 DEBUG  TaskList: ## Running get_diskimage...
02-22 10:47 DEBUG  TaskList: New task download
02-22 10:47 DEBUG  TaskList: ### Running download...
02-22 10:47 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-22 10:47 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-22 11:09 DEBUG  TaskList: ### Finished download
02-22 11:09 DEBUG  downloader: download finished (read 507143012 bytes)
02-22 11:09 DEBUG  TaskList: ## Finished get_diskimage
02-22 11:09 DEBUG  TaskList: ## Running extract_diskimage...
02-22 11:10 DEBUG  TaskList: ## Finished extract_diskimage
02-22 11:10 DEBUG  TaskList: ## Running choose_disk_sizes...
02-22 11:10 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-22 11:10 DEBUG  TaskList: ## Finished choose_disk_sizes
02-22 11:10 DEBUG  TaskList: ## Running expand_diskimage...
02-22 11:13 DEBUG  TaskList: ## Finished expand_diskimage
02-22 11:13 DEBUG  TaskList: ## Running create_swap_diskimage...
02-22 11:13 DEBUG  TaskList: ## Finished create_swap_diskimage
02-22 11:13 DEBUG  TaskList: ## Running modify_bootloader...
02-22 11:13 DEBUG  TaskList: New task modify_bootini
02-22 11:13 DEBUG  TaskList: ### Running modify_bootini...
02-22 11:13 DEBUG  WindowsBackend: modify_bootini C:
02-22 11:13 DEBUG  TaskList: ### Finished modify_bootini
02-22 11:13 DEBUG  TaskList: ## Finished modify_bootloader
02-22 11:13 DEBUG  TaskList: ## Running diskimage_bootloader...
02-22 11:13 DEBUG  WindowsBackend: Copying C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\winboot -> C:\ubuntu\winboot
02-22 11:13 DEBUG  TaskList: ## Finished diskimage_bootloader
02-22 11:13 DEBUG  TaskList: # Finished tasklist
02-22 11:13 INFO   root: Almost finished installing
02-22 11:13 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['en_US', 'en']
02-22 11:32 INFO   root: Finished installation
02-22 11:32 INFO   root: Rebooting
02-22 11:32 DEBUG  TaskList: # Running tasklist...
02-22 11:32 DEBUG  TaskList: ## Running reboot...
02-22 11:32 DEBUG  TaskList: ## Finished reboot
02-22 11:32 DEBUG  TaskList: # Finished tasklist
02-22 11:32 DEBUG  root: application.quit
02-22 11:32 DEBUG  WindowsFrontend: frontend.quit
02-22 11:32 DEBUG  WindowsFrontend: frontend.on_quit
02-22 11:32 DEBUG  root: application.on_quit
02-22 11:32 INFO   root: sys.exit
02-22 12:23 INFO   root: === wubi 11.10 rev245 ===
02-22 12:23 DEBUG  root: Logfile is c:\docume~1\klausj\locals~1\temp\wubi-11.10-rev245.log
02-22 12:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-22 12:23 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\data
02-22 12:23 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\bin\7z.exe
02-22 12:23 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-22 12:23 DEBUG  CommonBackend: Fetching basic info...
02-22 12:23 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-22 12:23 DEBUG  CommonBackend: platform=win32
02-22 12:23 DEBUG  CommonBackend: osname=nt
02-22 12:23 DEBUG  CommonBackend: language=en_US
02-22 12:23 DEBUG  CommonBackend: encoding=cp1252
02-22 12:23 DEBUG  WindowsBackend: arch=amd64
02-22 12:23 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\data\isolist.ini
02-22 12:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-22 12:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-22 12:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-22 12:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-22 12:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-22 12:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-22 12:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-22 12:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-22 12:23 DEBUG  WindowsBackend: Fetching host info...
02-22 12:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-22 12:23 DEBUG  WindowsBackend: windows version=xp
02-22 12:23 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-22 12:23 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-22 12:23 DEBUG  WindowsBackend: windows_build=2600
02-22 12:23 DEBUG  WindowsBackend: gmt=-8
02-22 12:23 DEBUG  WindowsBackend: country=US
02-22 12:23 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-22 12:23 DEBUG  WindowsBackend: windows_username=klausj
02-22 12:23 DEBUG  WindowsBackend: user_full_name=klausj
02-22 12:23 DEBUG  WindowsBackend: user_directory=N:\
02-22 12:23 DEBUG  WindowsBackend: windows_language_code=1033
02-22 12:23 DEBUG  WindowsBackend: windows_language=English
02-22 12:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-22 12:23 DEBUG  WindowsBackend: bootloader=xp
02-22 12:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 116424.988281 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(C: hd 116424.988281 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(N: remote 4525504.59766 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(Q: remote 7746.29296875 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(S: remote 10823188.4141 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(T: remote 100562.707031 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-22 12:23 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-22 12:23 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-22 12:23 DEBUG  WindowsBackend: keyboard_id=67699721
02-22 12:23 DEBUG  WindowsBackend: keyboard_layout=us
02-22 12:23 DEBUG  WindowsBackend: keyboard_variant=
02-22 12:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-22 12:23 DEBUG  CommonBackend: locale=en_US.UTF-8
02-22 12:23 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-22 12:23 DEBUG  CommonBackend: Searching ISOs on USB devices
02-22 12:23 DEBUG  CommonBackend: Searching for local CDs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 INFO   root: Running the uninstaller...
02-22 12:23 INFO   CommonBackend: This is the uninstaller running
02-22 12:23 DEBUG  WindowsFrontend: __init__...
02-22 12:23 DEBUG  WindowsFrontend: on_init...
02-22 12:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
02-22 12:23 INFO   root: Received settings
02-22 12:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
02-22 12:23 DEBUG  TaskList: # Running tasklist...
02-22 12:23 DEBUG  TaskList: ## Running Remove bootloader entry...
02-22 12:23 ERROR  WindowsBackend: Cannot find bcdedit
02-22 12:23 DEBUG  WindowsBackend: undo_bootini C:
02-22 12:23 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 116424.988281 mb free ntfs)
02-22 12:23 DEBUG  TaskList: ## Finished Remove bootloader entry
02-22 12:23 DEBUG  TaskList: ## Running Remove target dir...
02-22 12:23 DEBUG  CommonBackend: Deleting C:\ubuntu
02-22 12:23 DEBUG  TaskList: ## Finished Remove target dir
02-22 12:23 DEBUG  TaskList: ## Running Remove registry key...
02-22 12:23 DEBUG  TaskList: ## Finished Remove registry key
02-22 12:23 DEBUG  TaskList: # Finished tasklist
02-22 12:23 INFO   root: Almost finished uninstalling
02-22 12:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
02-22 12:23 INFO   root: Finished uninstallation
02-22 12:23 DEBUG  root: application.quit
02-22 12:23 DEBUG  WindowsFrontend: frontend.quit
02-22 12:23 DEBUG  WindowsFrontend: frontend.on_quit
02-22 12:23 DEBUG  root: application.on_quit
02-22 12:23 INFO   root: sys.exit
02-22 12:23 INFO   root: === wubi 11.10 rev245 ===
02-22 12:23 DEBUG  root: Logfile is c:\docume~1\klausj\locals~1\temp\wubi-11.10-rev245.log
02-22 12:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="\\\\Picea\\home\\klausj\\docs\\Downloads\\wubi.exe"']
02-22 12:23 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\data
02-22 12:23 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\bin\7z.exe
02-22 12:23 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-22 12:23 DEBUG  CommonBackend: Fetching basic info...
02-22 12:23 DEBUG  CommonBackend: original_exe=\\Picea\home\klausj\docs\Downloads\wubi.exe
02-22 12:23 DEBUG  CommonBackend: platform=win32
02-22 12:23 DEBUG  CommonBackend: osname=nt
02-22 12:23 DEBUG  CommonBackend: language=en_US
02-22 12:23 DEBUG  CommonBackend: encoding=cp1252
02-22 12:23 DEBUG  WindowsBackend: arch=amd64
02-22 12:23 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\data\isolist.ini
02-22 12:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-22 12:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-22 12:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-22 12:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-22 12:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-22 12:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-22 12:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-22 12:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-22 12:23 DEBUG  WindowsBackend: Fetching host info...
02-22 12:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-22 12:23 DEBUG  WindowsBackend: windows version=xp
02-22 12:23 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-22 12:23 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-22 12:23 DEBUG  WindowsBackend: windows_build=2600
02-22 12:23 DEBUG  WindowsBackend: gmt=-8
02-22 12:23 DEBUG  WindowsBackend: country=US
02-22 12:23 DEBUG  WindowsBackend: timezone=America/Los_Angeles
02-22 12:23 DEBUG  WindowsBackend: windows_username=klausj
02-22 12:23 DEBUG  WindowsBackend: user_full_name=klausj
02-22 12:23 DEBUG  WindowsBackend: user_directory=N:\
02-22 12:23 DEBUG  WindowsBackend: windows_language_code=1033
02-22 12:23 DEBUG  WindowsBackend: windows_language=English
02-22 12:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU           @ 2.66GHz
02-22 12:23 DEBUG  WindowsBackend: bootloader=xp
02-22 12:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 119628.394531 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(C: hd 119628.394531 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(N: remote 4525504.59766 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(Q: remote 7746.29296875 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(S: remote 10823189.0391 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: drive=Drive(T: remote 100562.707031 mb free ntfs)
02-22 12:23 DEBUG  WindowsBackend: uninstaller_path=None
02-22 12:23 DEBUG  WindowsBackend: previous_target_dir=None
02-22 12:23 DEBUG  WindowsBackend: previous_distro_name=None
02-22 12:23 DEBUG  WindowsBackend: keyboard_id=67699721
02-22 12:23 DEBUG  WindowsBackend: keyboard_layout=us
02-22 12:23 DEBUG  WindowsBackend: keyboard_variant=
02-22 12:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-22 12:23 DEBUG  CommonBackend: locale=en_US.UTF-8
02-22 12:23 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-22 12:23 DEBUG  CommonBackend: Searching ISOs on USB devices
02-22 12:23 DEBUG  CommonBackend: Searching for local CDs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-22 12:23 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:23 INFO   root: Running the installer...
02-22 12:23 DEBUG  WindowsFrontend: __init__...
02-22 12:23 DEBUG  WindowsFrontend: on_init...
02-22 12:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\translations, languages=['en_US', 'en']
02-22 12:23 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\translations, languages=['en_US', 'en']
02-22 12:24 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=klausj
02-22 12:24 INFO   root: Received settings
02-22 12:24 DEBUG  CommonBackend: Searching for local CD
02-22 12:24 DEBUG  Distro:   checking whether C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp is a valid Ubuntu CD
02-22 12:24 DEBUG  Distro:     does not contain C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\casper\filesystem.squashfs
02-22 12:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-22 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-22 12:24 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-22 12:24 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-22 12:24 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
02-22 12:24 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
02-22 12:24 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-22 12:24 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-22 12:24 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-22 12:24 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-22 12:24 DEBUG  CommonBackend: Searching for local ISO
02-22 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\translations, languages=['en_US', 'en']
02-22 12:24 DEBUG  TaskList: # Running tasklist...
02-22 12:24 DEBUG  TaskList: ## Running select_target_dir...
02-22 12:24 INFO   WindowsBackend: Installing into C:\ubuntu
02-22 12:24 DEBUG  TaskList: ## Finished select_target_dir
02-22 12:24 DEBUG  TaskList: ## Running create_dir_structure...
02-22 12:24 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-22 12:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-22 12:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-22 12:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-22 12:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-22 12:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-22 12:24 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-22 12:24 DEBUG  TaskList: ## Finished create_dir_structure
02-22 12:24 DEBUG  TaskList: ## Running create_uninstaller...
02-22 12:24 DEBUG  WindowsBackend: Copying uninstaller \\Picea\home\klausj\docs\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-22 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-22 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-22 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-22 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-22 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-22 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-22 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-22 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-22 12:24 DEBUG  TaskList: ## Finished create_uninstaller
02-22 12:24 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-22 12:24 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-22 12:24 DEBUG  TaskList: ## Running get_diskimage...
02-22 12:24 DEBUG  TaskList: New task download
02-22 12:24 DEBUG  TaskList: ### Running download...
02-22 12:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-22 12:24 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-22 12:47 DEBUG  TaskList: ### Finished download
02-22 12:47 DEBUG  downloader: download finished (read 507143012 bytes)
02-22 12:47 DEBUG  TaskList: ## Finished get_diskimage
02-22 12:47 DEBUG  TaskList: ## Running extract_diskimage...
02-22 12:48 DEBUG  TaskList: ## Finished extract_diskimage
02-22 12:48 DEBUG  TaskList: ## Running choose_disk_sizes...
02-22 12:48 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-22 12:48 DEBUG  TaskList: ## Finished choose_disk_sizes
02-22 12:48 DEBUG  TaskList: ## Running expand_diskimage...
02-22 12:50 DEBUG  TaskList: ## Finished expand_diskimage
02-22 12:50 DEBUG  TaskList: ## Running create_swap_diskimage...
02-22 12:50 DEBUG  TaskList: ## Finished create_swap_diskimage
02-22 12:50 DEBUG  TaskList: ## Running modify_bootloader...
02-22 12:50 DEBUG  TaskList: New task modify_bootini
02-22 12:50 DEBUG  TaskList: ### Running modify_bootini...
02-22 12:50 DEBUG  WindowsBackend: modify_bootini C:
02-22 12:50 DEBUG  TaskList: ### Finished modify_bootini
02-22 12:50 DEBUG  TaskList: ## Finished modify_bootloader
02-22 12:50 DEBUG  TaskList: ## Running diskimage_bootloader...
02-22 12:50 DEBUG  WindowsBackend: Copying C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\winboot -> C:\ubuntu\winboot
02-22 12:50 DEBUG  TaskList: ## Finished diskimage_bootloader
02-22 12:50 DEBUG  TaskList: # Finished tasklist
02-22 12:50 INFO   root: Almost finished installing
02-22 12:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\klausj\LOCALS~1\Temp\pylE.tmp\translations, languages=['en_US', 'en']
02-22 12:52 INFO   root: Finished installation
02-22 12:52 INFO   root: Rebooting
02-22 12:52 DEBUG  TaskList: # Running tasklist...
02-22 12:52 DEBUG  TaskList: ## Running reboot...
02-22 12:52 DEBUG  TaskList: ## Finished reboot
02-22 12:52 DEBUG  TaskList: # Finished tasklist
02-22 12:52 DEBUG  root: application.quit
02-22 12:52 DEBUG  WindowsFrontend: frontend.quit
02-22 12:52 DEBUG  WindowsFrontend: frontend.on_quit
02-22 12:52 DEBUG  root: application.on_quit

---

### Post by bcbc on 2012-02-23
What brand/model is the laptop?

When you boot Ubuntu does it give you a grub menu first, or does it boot right away with a bunch of text on the screen?

When it boots can you hit Ctrl+Alt+F1 to get to a command prompt and login?

---

### Post by JUKL on 2012-02-23
[B][FONT=&quot]
[/FONT][/B][FONT=&quot] [/FONT]
  [CENTER][CENTER][FONT=&quot]    [/FONT][/CENTER][/CENTER]
  [FONT=&quot]What brand/model is the laptop?[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Dell Precision 390[/FONT]
  [FONT=&quot]
When you boot Ubuntu does it give you a grub menu first, or does it boot right away with a bunch of text on the screen?[/FONT]
  [FONT=&quot]Yes I can get it, and I can choose between two Ubuntu (one recovery), and two windows options[/FONT]
[FONT=&quot]I can come to the login, after that it breaks down
[/FONT]
  [FONT=&quot]
When it boots can you hit Ctrl+Alt+F1 to get to a command prompt and login?[/FONT]
  [FONT=&quot]No it does not work.[/FONT]

---

### Post by JUKL on 2012-02-23
Ok, i have the problem. It's the video card, it works when i choose the UBUNTU 2D when i log in, the UBUNTU option produces the mess.
An other driver for the video card should work?
Sorry for the false alarm.

---

### Post by bcbc on 2012-02-23
It should recognize whether 3D is unsupported and automatically switch to 2D rather than 'break'. 

What graphics card do you have? If there is another driver available it should prompt you (a little 'additional-drivers' appindicator on the top right) or you can press the super (windows) key and run 'additional-drivers' yourself.

---

### Post by JUKL on 2012-02-23
I could fix the 3D problem. It was an issue of the NVIDA Quasro FX 3400/4400 card.
But installing the driver worked.
Thanks

---

