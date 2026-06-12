---
title: "For Professionals i need your help"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by kareem23 on 2010-08-21
hello ^^, how are yuo guys, my name is kareem, and i'm new here this is my first time here, and i need your help, 

i have downloaded a version of ubuntu: ubuntu-10.04.1-desktop-i386.iso
i work with windows 7 i mounted the iso with ultraiso without purn it in CD, and i i install it with option [COLOR=#000000]install in windows till now every things is natural ^^ but i reboot it i choose ubuntu and it gaves me this black screen with message ==>

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

(initramfs) cp: cannot stat '/custom-installation/initrd-override/*' No such file or directory
mount: mounting /dev/loop1 on //filesystem.squashfs failed: Input/output error
can not mount /dev/loop1 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

and sorry for my language it's poor ^^, 

i hope you find the the way to resolve this problem, and thank you ^^
[/COLOR]

---

### Post by kareem23 on 2010-08-22
plzz guys 37 views and no reply

---

### Post by earthpigg on 2010-08-22
> **kareem23 said:**
> plzz guys 37 views and no reply

hi,

if someone had any solution to your problem, im sure they would have chimed in and offered advice.

i don't have a solution, either, unfortunately. many/most Ubuntu users do not use the windows ubuntu installer (wubi) because of problems similar to yours. with wubi installs, a windows problem can affect the ubuntu install, so it can be difficult to fix. the problem is made worse because long-term Ubuntu users very rarely use wubi, and so don't have experience with fixing it's problems.

to [quote the creator]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/") of wubi:
> Agostino: **Wubi actually wasn’t designed to do long-term installations.** The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by bcbc on 2010-08-22
> **kareem23 said:**
> hello ^^, how are yuo guys, my name is kareem, and i'm new here this is my first time here, and i need your help, 

i have downloaded a version of ubuntu: ubuntu-10.04.1-desktop-i386.iso
i work with windows 7 i mounted the iso with ultraiso without purn it in CD, and i i install it with option [COLOR=#000000]install in windows till now every things is natural ^^ but i reboot it i choose ubuntu and it gaves me this black screen with message ==>

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)

(initramfs) cp: cannot stat '/custom-installation/initrd-override/*' No such file or directory
mount: mounting /dev/loop1 on //filesystem.squashfs failed: Input/output error
can not mount /dev/loop1 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

and sorry for my language it's poor ^^, 

i hope you find the the way to resolve this problem, and thank you ^^
[/COLOR]
You don't need to mount the .iso - just copy it into a folder, then download wubi.exe from [http://wubi-installer.org/](http://wubi-installer.org/) and place it in the same folder, and run it.

I can't say why your install didn't work, but I've done it many times and never had such a problem. I'd retry with the above method and if you still have problems, post back with the details (include the wubi-xxx.log file from the %temp% directory).

---

### Post by Dinahalye on 2010-08-22
my friend is the expert of windows ubuntu

---

### Post by kareem23 on 2010-08-22
hello friends i did what did you said and i extrat it in a folder in c:\ and i downloaded the wubi.exe, and put it in the seem folder but when i install it from wubi it stuck in middle and give me this message :
 
Exception: Cannot download the metalink and therefore the ISO
 
and here is the wubi-10.04.1-rev190.txt ==>
 
08-22 15:29 INFO   root: === wubi 10.04.1 rev190 ===
08-22 15:29 DEBUG  root: Logfile is c:\users\kareem\appdata\local\temp\wubi-10.04.1-rev190.log
08-22 15:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04.1-desktop-i386\\wubi.exe"']
08-22 15:29 DEBUG  CommonBackend: data_dir=C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\data
08-22 15:29 DEBUG  WindowsBackend: 7z=C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\bin\7z.exe
08-22 15:29 DEBUG  CommonBackend: Fetching basic info...
08-22 15:29 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04.1-desktop-i386\wubi.exe
08-22 15:29 DEBUG  CommonBackend: platform=win32
08-22 15:29 DEBUG  CommonBackend: osname=nt
08-22 15:29 DEBUG  CommonBackend: language=fr_FR
08-22 15:29 DEBUG  CommonBackend: encoding=cp1252
08-22 15:29 DEBUG  WindowsBackend: arch=amd64
08-22 15:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\data\isolist.ini
08-22 15:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-22 15:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-22 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-22 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-22 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-22 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-22 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-22 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-22 15:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-22 15:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-22 15:29 DEBUG  WindowsBackend: Fetching host info...
08-22 15:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-22 15:29 DEBUG  WindowsBackend: windows version=vista
08-22 15:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
08-22 15:29 DEBUG  WindowsBackend: windows_sp=None
08-22 15:29 DEBUG  WindowsBackend: windows_build=7600
08-22 15:29 DEBUG  WindowsBackend: gmt=0
08-22 15:29 DEBUG  WindowsBackend: country=FR
08-22 15:29 DEBUG  WindowsBackend: timezone=Europe/Paris
08-22 15:29 DEBUG  WindowsBackend: windows_username=kareem
08-22 15:29 DEBUG  WindowsBackend: user_full_name=kareem
08-22 15:29 DEBUG  WindowsBackend: user_directory=C:\Users\kareem
08-22 15:29 DEBUG  WindowsBackend: windows_language_code=1036
08-22 15:29 DEBUG  WindowsBackend: windows_language=French
08-22 15:29 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 4000+
08-22 15:29 DEBUG  WindowsBackend: bootloader=vista
08-22 15:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 82815.28125 mb free ntfs)
08-22 15:29 DEBUG  WindowsBackend: drive=Drive(C: hd 82815.28125 mb free ntfs)
08-22 15:29 DEBUG  WindowsBackend: drive=Drive(D: hd 39475.0273438 mb free ntfs)
08-22 15:29 DEBUG  WindowsBackend: drive=Drive(E: hd 4486.54296875 mb free ntfs)
08-22 15:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
08-22 15:29 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
08-22 15:29 DEBUG  WindowsBackend: uninstaller_path=None
08-22 15:29 DEBUG  WindowsBackend: previous_target_dir=None
08-22 15:29 DEBUG  WindowsBackend: previous_distro_name=None
08-22 15:29 DEBUG  WindowsBackend: keyboard_id=67896332
08-22 15:29 DEBUG  WindowsBackend: keyboard_layout=fr
08-22 15:29 DEBUG  WindowsBackend: keyboard_variant=
08-22 15:29 DEBUG  CommonBackend: python locale=('fr_FR', 'cp1252')
08-22 15:29 DEBUG  CommonBackend: locale=fr_FR.UTF-8
08-22 15:29 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
08-22 15:29 DEBUG  CommonBackend: Searching ISOs on USB devices
08-22 15:29 DEBUG  CommonBackend: Searching for local CDs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Ubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Kubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 INFO   root: Running the installer...
08-22 15:29 DEBUG  WindowsFrontend: __init__...
08-22 15:29 DEBUG  WindowsFrontend: on_init...
08-22 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\translations, languages=['fr_FR', 'fr']
08-22 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\translations, languages=['fr_FR', 'fr']
08-22 15:29 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=fr_FR, locale=fr_FR.UTF-8, username=kareem
08-22 15:29 INFO   root: Received settings
08-22 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\translations, languages=['fr_FR', 'fr']
08-22 15:29 DEBUG  TaskList: # Running tasklist...
08-22 15:29 DEBUG  TaskList: ## Running select_target_dir...
08-22 15:29 INFO   WindowsBackend: Installing into C:\ubuntu
08-22 15:29 DEBUG  TaskList: ## Finished select_target_dir
08-22 15:29 DEBUG  TaskList: ## Running create_dir_structure...
08-22 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-22 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-22 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-22 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-22 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-22 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-22 15:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-22 15:29 DEBUG  TaskList: ## Finished create_dir_structure
08-22 15:29 DEBUG  TaskList: ## Running uncompress_target_dir...
08-22 15:29 DEBUG  TaskList: ## Finished uncompress_target_dir
08-22 15:29 DEBUG  TaskList: ## Running create_uninstaller...
08-22 15:29 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04.1-desktop-i386\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-22 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-22 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-22 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-22 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-22 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
08-22 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-22 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-22 15:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-22 15:29 DEBUG  TaskList: ## Finished create_uninstaller
08-22 15:29 DEBUG  TaskList: ## Running copy_installation_files...
08-22 15:29 DEBUG  WindowsBackend: Copying C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-22 15:29 DEBUG  WindowsBackend: Copying C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\winboot -> C:\ubuntu\winboot
08-22 15:29 DEBUG  WindowsBackend: Copying C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-22 15:29 DEBUG  TaskList: ## Finished copy_installation_files
08-22 15:29 DEBUG  TaskList: ## Running get_iso...
08-22 15:29 DEBUG  CommonBackend: Searching for local CD
08-22 15:29 DEBUG  Distro:   checking whether C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain C:\Users\kareem\AppData\Local\Temp\pyl2D66.tmp\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-22 15:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-22 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-22 15:29 DEBUG  CommonBackend: Searching for local ISO
08-22 15:29 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-22 15:29 DEBUG  TaskList: New task get_metalink
08-22 15:29 DEBUG  TaskList: ### Running get_metalink...
08-22 15:29 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) > C:\ubuntu\install
08-22 15:29 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
08-22 15:29 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
08-22 15:29 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
08-22 15:29 DEBUG  TaskList: ### Finished get_metalink
08-22 15:29 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-22 15:29 DEBUG  TaskList: # Cancelling tasklist
08-22 15:29 DEBUG  TaskList: # Finished tasklist
08-22 15:29 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO

note : i did the seem this but with internet connect working and it download it self a version of here is what doing now ==>
 
download of ubuntu-10.04.1-desktop-amd64.iso.torrent
 
 
it's not the seem that i have downloaded befor, in fact i have a **AMD** Athlon™ X2 Dual-Core **Processor**
 
and thanks again ^^

---

### Post by bcbc on 2010-08-22
I think you can still use the i386 version. According to this [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) it works on intel and AMD chips.

To force wubi.exe you can add --32bit to the command line... e.g. wubi.exe --32bit.
You have to have internet access to validate the md5sum unless you override this --skipmd5check. But in this case you should check it yourself.

---

### Post by kareem23 on 2010-08-22
sorry bcbc i don't know how to do that i'm just beginner here ^^, can you explain more how to do that ?

---

### Post by bcbc on 2010-08-22
> **kareem23 said:**
> sorry bcbc i don't know how to do that i'm just beginner here ^^, can you explain more how to do that ?

I'm not in windows, but if you've downloaded wubi, just right-click, properties, go to where it shows what it runs: "c:\somepath\wubi.exe" and add the options e.g. "c:\somepath\wubi.exe --32bit --someOtherOption"
Then run it.

Or you can run it from command prompt as well.

---

### Post by kareem23 on 2010-08-22
there is nothing like that in property and i don't know how to run it from command prompt  i had a version 10.04 LTS and it works for me but this 10.04.1 LTS not i don't know why

---

### Post by bcbc on 2010-08-22
> **kareem23 said:**
> there is nothing like that in property and i don't know how to run it from command prompt  i had a version 10.04 LTS and it works for me but this 10.04.1 LTS not i don't know why

right click, create shortcut.
righ click on shortcut, change Target to be ```
C:\somepath\wubi.exe --32bit
```

I did see a report of a bug on 10.04.1 (actually it was a comment within a bug about something else) about not being able to download the metalink. But it didn't reference your original problem. 

All I can suggest is: install the 10.04 and run updates to take you to 10.04.1; and/or file a bug; and/or do a direct partition install.

---

### Post by kareem23 on 2010-08-22
hello again bcbc, you know i downloaded a version of ubuntu AMD64  10.04.1 and i intall it and i had some problems in installation with graphique i resole it and i install it finally, i shoose french to install it but i found my system in english and i want to know how to make it in franch? and thanks for your help again ^^

---

### Post by bcbc on 2010-08-22
> **kareem23 said:**
> hello again bcbc, you know i downloaded a version of ubuntu AMD64  10.04.1 and i intall it and i had some problems in installation with graphique i resole it and i install it finally, i shoose french to install it but i found my system in english and i want to know how to make it in franch? and thanks for your help again ^^

Try this:
```
sudo apt-get install language-pack-fr
```or install through Synaptic (under System, Administration)

Logout, and then at the login screen, select French.

---

### Post by kareem23 on 2010-08-22
*Thank* you so much for all *your help I really* appreciate it. it's useful, i really love this version it's fast and stable ^^

---

### Post by bcbc on 2010-08-23
> **kareem23 said:**
> *Thank* you so much for all *your help I really* appreciate it. it's useful, i really love this version it's fast and stable ^^
You're very welcome :)

Yes 10.04 is really fast. I've been playing with 9.04 today and it's incredibly slow in comparison.

---

