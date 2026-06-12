---
title: "Wubi &quot;Error Executing Command&quot;"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by mizkewl on 2012-04-10
I tried to install Ubuntu 11.10. I ran the Wubi.exe and it installed everything, at the very end, it said: 
[B][COLOR=Red]An error occured:

Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe/create/d Ubuntu
/application bootsector
>>retval=1
>>stderr= The boot configuration data store could not be opened.
The system cannot find the file specified.

>>stdout

For more information, please see the log file:
c:\users\MyUser\appdata\local\temp\wubi-11.10-rev245.log[/COLOR][/B]


After that i read several threads about this topic, but i didn't find a solution...

I'll give you some information of my computer:
Windows 7 Home Premium
Service Pack 1
Processor: Celeron Dual-Core
                 CPU T3500
                 2.10GHz 2.09GHz
Ram: 4.00 GB
64-bit Operating System

I hope i will get a solution fast...

-Mizkewl

---

### Post by Rubi1200 on 2012-04-12
Hi and welcome to the forums :-)

Please post the contents of that log file; it may help us determine what is going on.

Thanks.

---

### Post by jadtech on 2012-04-12
i have the same error every time I install wubi on my laptop if you just go to reboot  the install contines no problem at least for me and I have done this install 3 times now each time  I go reboot from the error and the install completes ..

---

### Post by bcbc on 2012-04-12
> **mizkewl said:**
> I tried to install Ubuntu 11.10. I ran the Wubi.exe and it installed everything, at the very end, it said: 
[B][COLOR=Red]An error occured:

Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe/create/d Ubuntu
/application bootsector
>>retval=1
>>stderr= The boot configuration data store could not be opened.
The system cannot find the file specified.

>>stdout

For more information, please see the log file:
c:\users\MyUser\appdata\local\temp\wubi-11.10-rev245.log[/COLOR][/B]


After that i read several threads about this topic, but i didn't find a solution...

I'll give you some information of my computer:
Windows 7 Home Premium
Service Pack 1
Processor: Celeron Dual-Core
                 CPU T3500
                 2.10GHz 2.09GHz
Ram: 4.00 GB
64-bit Operating System

I hope i will get a solution fast...

-Mizkewl
Please review this for a solution:
[http://askubuntu.com/questions/73585/wubi-installer-error](http://askubuntu.com/questions/73585/wubi-installer-error)

---

### Post by mizkewl on 2012-07-26
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Please post the contents of that log file; it may help us determine what is going on.

Thanks.
Here you go:

[COLOR=Red]07-14 00:05 INFO   root: === wubi 11.10 rev245 ===
07-14 00:05 DEBUG  root: Logfile is c:\users\ibo\appdata\local\temp\wubi-11.10-rev245.log
07-14 00:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ibo\\Downloads\\wubi.exe"']
07-14 00:05 DEBUG  CommonBackend: data_dir=C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\data
07-14 00:05 DEBUG  WindowsBackend: 7z=C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\bin\7z.exe
07-14 00:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-14 00:05 DEBUG  CommonBackend: Fetching basic info...
07-14 00:05 DEBUG  CommonBackend: original_exe=C:\Users\Ibo\Downloads\wubi.exe
07-14 00:05 DEBUG  CommonBackend: platform=win32
07-14 00:05 DEBUG  CommonBackend: osname=nt
07-14 00:05 DEBUG  CommonBackend: language=en_IE
07-14 00:05 DEBUG  CommonBackend: encoding=cp1252
07-14 00:05 DEBUG  WindowsBackend: arch=amd64
07-14 00:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\data\isolist.ini
07-14 00:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-14 00:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-14 00:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-14 00:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-14 00:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-14 00:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-14 00:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-14 00:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-14 00:05 DEBUG  WindowsBackend: Fetching host info...
07-14 00:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-14 00:05 DEBUG  WindowsBackend: windows version=vista
07-14 00:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-14 00:05 DEBUG  WindowsBackend: windows_sp=None
07-14 00:05 DEBUG  WindowsBackend: windows_build=7601
07-14 00:05 DEBUG  WindowsBackend: gmt=2
07-14 00:05 DEBUG  WindowsBackend: country=IE
07-14 00:05 DEBUG  WindowsBackend: timezone=Europe/Dublin
07-14 00:05 DEBUG  WindowsBackend: windows_username=Ibo
07-14 00:05 DEBUG  WindowsBackend: user_full_name=Ibo
07-14 00:05 DEBUG  WindowsBackend: user_directory=C:\Users\Ibo
07-14 00:05 DEBUG  WindowsBackend: windows_language_code=1033
07-14 00:05 DEBUG  WindowsBackend: windows_language=English
07-14 00:05 DEBUG  WindowsBackend: processor_name=Celeron(R) Dual-Core CPU       T3500  @ 2.10GHz
07-14 00:05 DEBUG  WindowsBackend: bootloader=vista
07-14 00:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59064.2929688 mb free ntfs)
07-14 00:05 DEBUG  WindowsBackend: drive=Drive(C: hd 59064.2929688 mb free ntfs)
07-14 00:05 DEBUG  WindowsBackend: drive=Drive(D: hd 197357.964844 mb free ntfs)
07-14 00:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-14 00:05 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
07-14 00:05 DEBUG  WindowsBackend: uninstaller_path=F:\ubuntu\uninstall-wubi.exe
07-14 00:05 DEBUG  WindowsBackend: previous_target_dir=F:\ubuntu
07-14 00:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-14 00:05 DEBUG  WindowsBackend: keyboard_id=72488969
07-14 00:05 DEBUG  WindowsBackend: keyboard_layout=gb
07-14 00:05 DEBUG  WindowsBackend: keyboard_variant=
07-14 00:05 DEBUG  CommonBackend: python locale=('en_IE', 'cp1252')
07-14 00:05 DEBUG  CommonBackend: locale=en_IE.UTF-8
07-14 00:05 DEBUG  WindowsBackend: total_memory_mb=3932.87890625
07-14 00:05 DEBUG  CommonBackend: Searching ISOs on USB devices
07-14 00:05 DEBUG  CommonBackend: Searching for local CDs
07-14 00:05 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Ubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Ubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Kubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Kubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Xubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Xubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Mythbuntu CD
07-14 00:05 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Mythbuntu CD
07-14 00:05 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-14 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-14 00:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-14 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-14 00:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
07-14 00:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
07-14 00:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:05 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
07-14 00:05 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:05 INFO   root: Running the installer...
07-14 00:05 DEBUG  WindowsFrontend: __init__...
07-14 00:05 DEBUG  WindowsFrontend: on_init...
07-14 00:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\translations, languages=['en_IE', 'en']
07-14 00:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\translations, languages=['en_IE', 'en']
07-14 00:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ahmed
07-14 00:06 INFO   root: Received settings
07-14 00:06 DEBUG  CommonBackend: Searching for local CD
07-14 00:06 DEBUG  Distro:   checking whether C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp is a valid Ubuntu CD
07-14 00:06 DEBUG  Distro:     does not contain C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\casper\filesystem.squashfs
07-14 00:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-14 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-14 00:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-14 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-14 00:06 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
07-14 00:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
07-14 00:06 DEBUG  CommonBackend: Searching for local ISO
07-14 00:06 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso
07-14 00:06 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso
07-14 00:06 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
07-14 00:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
07-14 00:06 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso
07-14 00:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\translations, languages=['en_US', 'en']
07-14 00:06 DEBUG  TaskList: # Running tasklist...
07-14 00:06 DEBUG  TaskList: ## Running select_target_dir...
07-14 00:06 INFO   WindowsBackend: Installing into C:\ubuntu
07-14 00:06 DEBUG  TaskList: ## Finished select_target_dir
07-14 00:06 DEBUG  TaskList: ## Running create_dir_structure...
07-14 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-14 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-14 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-14 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-14 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-14 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-14 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-14 00:06 DEBUG  TaskList: ## Finished create_dir_structure
07-14 00:06 DEBUG  TaskList: ## Running uncompress_target_dir...
07-14 00:06 DEBUG  TaskList: ## Finished uncompress_target_dir
07-14 00:06 DEBUG  TaskList: ## Running create_uninstaller...
07-14 00:06 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Ibo\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-14 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-14 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-14 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-14 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-14 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
07-14 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-14 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-14 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-14 00:06 DEBUG  TaskList: ## Finished create_uninstaller
07-14 00:06 DEBUG  TaskList: ## Running copy_installation_files...
07-14 00:06 DEBUG  WindowsBackend: Copying C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-14 00:06 DEBUG  WindowsBackend: Copying C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\winboot -> C:\ubuntu\winboot
07-14 00:06 DEBUG  WindowsBackend: Copying C:\Users\Ibo\AppData\Local\Temp\pyl212C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-14 00:06 DEBUG  TaskList: ## Finished copy_installation_files
07-14 00:06 DEBUG  TaskList: ## Running get_iso...
07-14 00:06 DEBUG  CommonBackend: Trying to use ISO C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso
07-14 00:06 DEBUG  TaskList: New task check_iso
07-14 00:06 DEBUG  TaskList: ### Running check_iso...
07-14 00:06 DEBUG  CommonBackend: Checking C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso
07-14 00:06 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso
07-14 00:06 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso
07-14 00:06 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
07-14 00:06 DEBUG  TaskList: New task get_metalink
07-14 00:06 DEBUG  TaskList: #### Running get_metalink...
07-14 00:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink](http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink) > C:\ubuntu\install
07-14 00:06 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink](http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
07-14 00:06 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.metalink) > C:\ubuntu\install
07-14 00:06 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/oneiric-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
07-14 00:06 DEBUG  TaskList: #### Finished get_metalink
07-14 00:06 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso, ignoring
07-14 00:06 DEBUG  TaskList: ### Finished check_iso
07-14 00:06 DEBUG  TaskList: New task copy_file
07-14 00:06 DEBUG  CommonBackend: Copying C:\Users\Ibo\Downloads\ubuntu-11.10-desktop-i386.iso > C:\ubuntu\install\installation.iso
07-14 00:06 DEBUG  TaskList: ### Running copy_file...
07-14 00:06 DEBUG  TaskList: ### Finished copy_file
07-14 00:06 DEBUG  TaskList: ## Finished get_iso
07-14 00:06 DEBUG  TaskList: ## Running extract_kernel...
07-14 00:06 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
07-14 00:06 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
07-14 00:06 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
07-14 00:06 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
07-14 00:06 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-14 00:06 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
07-14 00:06 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = fde150f5c6fd2de66ed7876efbfcc4c7 == fde150f5c6fd2de66ed7876efbfcc4c7
07-14 00:06 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
07-14 00:06 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = d6baee1e11f1d6de6eba6bd43dbde352 == d6baee1e11f1d6de6eba6bd43dbde352
07-14 00:06 DEBUG  TaskList: ## Finished extract_kernel
07-14 00:06 DEBUG  TaskList: ## Running choose_disk_sizes...
07-14 00:06 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
07-14 00:06 DEBUG  TaskList: ## Finished choose_disk_sizes
07-14 00:06 DEBUG  TaskList: ## Running create_preseed...
07-14 00:06 DEBUG  TaskList: ## Finished create_preseed
07-14 00:06 DEBUG  TaskList: ## Running modify_bootloader...
07-14 00:06 DEBUG  TaskList: New task modify_bcd
07-14 00:06 DEBUG  TaskList: ### Running modify_bcd...
07-14 00:06 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 59064.2929688 mb free ntfs)
07-14 00:06 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 689, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
07-14 00:06 DEBUG  TaskList: # Cancelling tasklist
07-14 00:06 DEBUG  TaskList: New task modify_bcd
07-14 00:06 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 689, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


>>stdout=
07-14 00:06 DEBUG  TaskList: New task modify_bcd
07-14 00:06 DEBUG  TaskList: ## Finished modify_bootloader
07-14 00:06 DEBUG  TaskList: # Finished tasklist
[/COLOR]

---

### Post by mizkewl on 2012-07-26
> **jadtech said:**
> i have the same error every time I install wubi on my laptop if you just go to reboot  the install contines no problem at least for me and I have done this install 3 times now each time  I go reboot from the error and the install completes ..
I'll try that. Ill be back in a while.
----------After Trying----------
Didn't work :(
Thanks for trying though.

---

### Post by mizkewl on 2012-07-28
This is what I did.
1. Downloaded Partition Wizard 7
2. Assigned a letter to hidden SYSTEM partition Windows 7 creates.
3. Ran wubi.
4. Was happy for accomplishment.
:)
But thanks for everyone who tried to help! :popcorn:

---

### Post by MADHU I K on 2012-11-23
hey i didn't get what is this partition wizard 7.....
please explain the further steps in detail.....
i too facing the same problem......

---

### Post by bcbc on 2012-11-23
You can either assign a drive letter to the system boot partition - but this is not necessary. You just need to bring it 'online': [http://askubuntu.com/a/73714](http://askubuntu.com/a/73714)

You shouldn't need partition wizard to assign a drive letter either. Probably the Windows Disk Management tool will do it as well.

---

