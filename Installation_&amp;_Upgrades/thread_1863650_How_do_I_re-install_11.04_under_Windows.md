---
title: "How do I re-install 11.04 under Windows?"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by MonocleMike2 on 2011-10-18
I don't have working removable media so I download under Windows.  I am happy to uninstall and re-format the partition but when I want to download it offers me 11.10.  How do I select 11.04?
-------------------------------------------------------------------------------------------------------------------------------
Jump to the end to see the post by bcbc.
He gives the link

[http://releases.ubuntu.com/11.04/wubi.exe](http://releases.ubuntu.com/11.04/wubi.exe)

IT WORKS

---

### Post by hansdown on 2011-10-18
Hi, MonocleMike2.

Try this link.

[http://linux.softpedia.com/progDownload/Ubuntu-Natty-Narwhal-Download-62881.html](http://linux.softpedia.com/progDownload/Ubuntu-Natty-Narwhal-Download-62881.html)

Choose 32bit, or 64bit, depending, on your needs.

---

### Post by MonocleMike2 on 2011-10-18
Thanks for your help but sorry I don't know how to use the ISO image :-(  I cannot write to a DVD and I don't have a big enough USB stick.  I have to use the wubi installer and download from the web into that.  Can I download the ISO image to my hard disk and then install from that?  Or must I go to the shops and buy a 2GB stick?

---

### Post by hansdown on 2011-10-18
Try this.

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Hope it helps.

---

### Post by MonocleMike2 on 2011-10-18
Sadly it only offers 11.10 and 10.04 Long Term Support.  I am trying again to write a CD but if that doesn't work I'll have to buy a new stick!

---

### Post by Elfy on 2011-10-18
[http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/)

---

### Post by hansdown on 2011-10-18
> **forestpiskie said:**
> [http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/)

Thank you, forestpiskie.

---

### Post by MonocleMike2 on 2011-10-18
I have downloaded the ISO image.  Checked it with winMd5S and have discovered UNetbootin from [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
and used their option to save an installation set onto the hard disk. 
I rebooted and it has come up in 11.04 - hurrah!   I have done the whole thing with neither writable CD nor USB stick! :p
Now to do the hard part and get it properly installed and fully working again.

Thank you ubuntu.com/community and forestpixie:popcorn:

---

### Post by MonocleMike2 on 2011-10-18
TOTAL FAILURE!!  

It just will not install as it gets this problem
[http://ubuntuforums.org/archive/index.php/t-1645214.html](http://ubuntuforums.org/archive/index.php/t-1645214.html)
and I cannot get through the solution offered.

I am off to buy a USB stick which is probably a safer and better solution anyway.  I can then re-install whenever and wherever I like.

---

### Post by hansdown on 2011-10-18
Hope it all works, MonocleMike2.

---

### Post by MonocleMike2 on 2011-10-18
FAILURE AGAIN! 
I am at my wits end. I drove 45km to get the stick and have spent 4 hours loading the stick and then installing from it. It was ever so nearly finished and I get this
[http://ubuntuforums.org/showthread.php?t=1773743](http://ubuntuforums.org/showthread.php?t=1773743)
The solution there is to do it from CD and I can't.
There's no restart option and no update option. If I try all over again I have no confidence it will work having read the thread.
 
Defeat is staring me in the face and laughing at me. What shall I try now?
 
I'll just go and download the log file and add it into this post.  *** Further progress! - Skip to my next post ***
```

10-05 20:11 INFO   root: === wubi 11.04 rev211 ===
10-05 20:11 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
10-05 20:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Administrator\\Local Settings\\Temporary Internet Files\\Content.IE5\\N939HN06\\wubi[1].exe"']
10-05 20:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\data
10-05 20:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\bin\7z.exe
10-05 20:11 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
10-05 20:11 DEBUG  CommonBackend: Fetching basic info...
10-05 20:11 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\N939HN06\wubi[1].exe
10-05 20:11 DEBUG  CommonBackend: platform=win32
10-05 20:11 DEBUG  CommonBackend: osname=nt
10-05 20:11 DEBUG  CommonBackend: language=en_GB
10-05 20:11 DEBUG  CommonBackend: encoding=cp1252
10-05 20:11 DEBUG  WindowsBackend: arch=i386
10-05 20:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
10-05 20:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 20:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 20:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 20:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 20:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 20:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 20:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 20:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 20:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-05 20:11 DEBUG  WindowsBackend: Fetching host info...
10-05 20:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 20:11 DEBUG  WindowsBackend: windows version=xp
10-05 20:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 20:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-05 20:11 DEBUG  WindowsBackend: windows_build=2600
10-05 20:11 DEBUG  WindowsBackend: gmt=1
10-05 20:11 DEBUG  WindowsBackend: country=GB
10-05 20:11 DEBUG  WindowsBackend: timezone=Europe/London
10-05 20:11 DEBUG  WindowsBackend: windows_username=Administrator
10-05 20:11 DEBUG  WindowsBackend: user_full_name=Administrator
10-05 20:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-05 20:11 DEBUG  WindowsBackend: windows_language_code=1033
10-05 20:11 DEBUG  WindowsBackend: windows_language=English
10-05 20:11 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-05 20:11 DEBUG  WindowsBackend: bootloader=xp
10-05 20:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8858.88574219 mb free ntfs)
10-05 20:11 DEBUG  WindowsBackend: drive=Drive(C: hd 8858.88574219 mb free ntfs)
10-05 20:11 DEBUG  WindowsBackend: drive=Drive(D: hd 19067.234375 mb free fat32)
10-05 20:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-05 20:11 DEBUG  WindowsBackend: uninstaller_path=None
10-05 20:11 DEBUG  WindowsBackend: previous_target_dir=None
10-05 20:11 DEBUG  WindowsBackend: previous_distro_name=None
10-05 20:11 DEBUG  WindowsBackend: keyboard_id=134809609
10-05 20:11 DEBUG  WindowsBackend: keyboard_layout=gb
10-05 20:11 DEBUG  WindowsBackend: keyboard_variant=
10-05 20:11 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-05 20:11 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-05 20:11 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-05 20:11 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 20:11 DEBUG  CommonBackend: Searching for local CDs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu Netbook CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 INFO   root: Running the installer...
10-05 20:11 DEBUG  WindowsFrontend: __init__...
10-05 20:11 DEBUG  WindowsFrontend: on_init...
10-05 20:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_GB', 'en']
10-05 20:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_GB', 'en']
10-05 20:11 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=mike
10-05 20:11 INFO   root: Received settings
10-05 20:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_GB', 'en']
10-05 20:11 DEBUG  TaskList: # Running tasklist...
10-05 20:11 DEBUG  TaskList: ## Running select_target_dir...
10-05 20:11 INFO   WindowsBackend: Installing into D:\ubuntu
10-05 20:11 DEBUG  TaskList: ## Finished select_target_dir
10-05 20:11 DEBUG  TaskList: ## Running create_dir_structure...
10-05 20:11 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-05 20:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-05 20:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-05 20:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-05 20:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-05 20:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-05 20:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-05 20:11 DEBUG  TaskList: ## Finished create_dir_structure
10-05 20:11 DEBUG  TaskList: ## Running uncompress_target_dir...
10-05 20:11 DEBUG  TaskList: ## Finished uncompress_target_dir
10-05 20:11 DEBUG  TaskList: ## Running create_uninstaller...
10-05 20:11 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\N939HN06\wubi[1].exe -> D:\ubuntu\uninstall-wubi.exe
10-05 20:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-05 20:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-05 20:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-05 20:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-05 20:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
10-05 20:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-05 20:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-05 20:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-05 20:11 DEBUG  TaskList: ## Finished create_uninstaller
10-05 20:11 DEBUG  TaskList: ## Running copy_installation_files...
10-05 20:11 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-05 20:11 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\winboot -> D:\ubuntu\winboot
10-05 20:11 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-05 20:11 DEBUG  TaskList: ## Finished copy_installation_files
10-05 20:11 DEBUG  TaskList: ## Running get_iso...
10-05 20:11 DEBUG  CommonBackend: Searching for local CD
10-05 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:11 DEBUG  CommonBackend: Searching for local ISO
10-05 20:11 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-05 20:11 DEBUG  TaskList: New task get_metalink
10-05 20:11 DEBUG  TaskList: ### Running get_metalink...
10-05 20:11 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > D:\ubuntu\install
10-05 20:11 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
10-05 20:11 DEBUG  downloader: download finished (read 28158 bytes)
10-05 20:11 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > D:\ubuntu\install
10-05 20:11 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
10-05 20:11 DEBUG  downloader: download finished (read 874 bytes)
10-05 20:11 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
10-05 20:11 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-05 20:11 DEBUG  downloader: download finished (read 198 bytes)
10-05 20:11 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-05 20:11 INFO   saplog: Checking block bindings..
10-05 20:11 INFO   saplog: Key verified successfully.
10-05 20:11 DEBUG  CommonBackend: metalink md5sums:
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
10-05 20:11 DEBUG  TaskList: ### Finished get_metalink
10-05 20:11 DEBUG  TaskList: New task download
10-05 20:11 DEBUG  TaskList: ### Running download...
10-05 20:11 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-05 20:17 INFO   WindowsFrontend: Operation cancelled
10-05 20:18 DEBUG  WindowsFrontend: frontend.quit
10-05 20:18 DEBUG  WindowsFrontend: frontend.on_quit
10-05 20:18 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
10-05 20:18 DEBUG  TaskList: # Cancelling tasklist
10-05 20:18 DEBUG  TaskList: ### Finished download
10-05 20:18 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
10-05 20:18 DEBUG  root: application.on_quit
10-05 20:18 DEBUG  root: Forceful exit
10-05 20:18 INFO   root: sys.exit
10-05 20:20 INFO   root: === wubi 11.04 rev211 ===
10-05 20:20 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
10-05 20:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Administrator\\Local Settings\\Temporary Internet Files\\Content.IE5\\OUNN4SGV\\wubi[1].exe"']
10-05 20:20 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\data
10-05 20:20 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
10-05 20:20 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
10-05 20:20 DEBUG  CommonBackend: Fetching basic info...
10-05 20:20 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\OUNN4SGV\wubi[1].exe
10-05 20:20 DEBUG  CommonBackend: platform=win32
10-05 20:20 DEBUG  CommonBackend: osname=nt
10-05 20:20 DEBUG  CommonBackend: language=en_GB
10-05 20:20 DEBUG  CommonBackend: encoding=cp1252
10-05 20:20 DEBUG  WindowsBackend: arch=i386
10-05 20:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
10-05 20:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 20:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 20:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 20:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 20:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 20:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 20:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 20:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 20:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-05 20:20 DEBUG  WindowsBackend: Fetching host info...
10-05 20:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 20:20 DEBUG  WindowsBackend: windows version=xp
10-05 20:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 20:20 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-05 20:20 DEBUG  WindowsBackend: windows_build=2600
10-05 20:20 DEBUG  WindowsBackend: gmt=1
10-05 20:20 DEBUG  WindowsBackend: country=GB
10-05 20:20 DEBUG  WindowsBackend: timezone=Europe/London
10-05 20:20 DEBUG  WindowsBackend: windows_username=Administrator
10-05 20:20 DEBUG  WindowsBackend: user_full_name=Administrator
10-05 20:20 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-05 20:20 DEBUG  WindowsBackend: windows_language_code=1033
10-05 20:20 DEBUG  WindowsBackend: windows_language=English
10-05 20:20 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-05 20:20 DEBUG  WindowsBackend: bootloader=xp
10-05 20:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8854.45263672 mb free ntfs)
10-05 20:20 DEBUG  WindowsBackend: drive=Drive(C: hd 8854.45263672 mb free ntfs)
10-05 20:20 DEBUG  WindowsBackend: drive=Drive(D: hd 19008.21875 mb free fat32)
10-05 20:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-05 20:20 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-05 20:20 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-05 20:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-05 20:20 DEBUG  WindowsBackend: keyboard_id=134809609
10-05 20:20 DEBUG  WindowsBackend: keyboard_layout=gb
10-05 20:20 DEBUG  WindowsBackend: keyboard_variant=
10-05 20:20 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-05 20:20 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-05 20:20 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-05 20:20 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 20:20 DEBUG  CommonBackend: Searching for local CDs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu Netbook CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 INFO   root: Already installed, running the uninstaller...
10-05 20:20 INFO   root: Running the uninstaller...
10-05 20:20 INFO   CommonBackend: This is the uninstaller running
10-05 20:20 DEBUG  WindowsFrontend: __init__...
10-05 20:20 DEBUG  WindowsFrontend: on_init...
10-05 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_GB', 'en']
10-05 20:20 INFO   root: Received settings
10-05 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_GB', 'en']
10-05 20:20 DEBUG  TaskList: # Running tasklist...
10-05 20:20 DEBUG  TaskList: ## Running Backup ISO...
10-05 20:20 DEBUG  TaskList: ## Finished Backup ISO
10-05 20:20 DEBUG  TaskList: ## Running Remove bootloader entry....
10-05 20:20 ERROR  WindowsBackend: Cannot find bcdedit
10-05 20:20 DEBUG  WindowsBackend: undo_bootini C:
10-05 20:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8854.45263672 mb free ntfs)
10-05 20:20 DEBUG  WindowsBackend: undo_bootini D:
10-05 20:20 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 19008.21875 mb free fat32)
10-05 20:20 DEBUG  TaskList: ## Finished Remove bootloader entry.
10-05 20:20 DEBUG  TaskList: ## Running Remove target dir....
10-05 20:20 DEBUG  CommonBackend: Deleting D:\ubuntu
10-05 20:20 DEBUG  TaskList: ## Finished Remove target dir.
10-05 20:20 DEBUG  TaskList: ## Running Remove registry key....
10-05 20:20 DEBUG  TaskList: ## Finished Remove registry key.
10-05 20:20 DEBUG  TaskList: # Finished tasklist
10-05 20:20 INFO   root: Almost finished uninstalling
10-05 20:20 INFO   root: Finished uninstallation
10-05 20:20 DEBUG  CommonBackend: Fetching basic info...
10-05 20:20 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\OUNN4SGV\wubi[1].exe
10-05 20:20 DEBUG  CommonBackend: platform=win32
10-05 20:20 DEBUG  CommonBackend: osname=nt
10-05 20:20 DEBUG  WindowsBackend: arch=i386
10-05 20:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
10-05 20:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 20:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 20:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 20:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 20:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 20:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 20:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 20:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 20:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-05 20:20 DEBUG  WindowsBackend: Fetching host info...
10-05 20:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 20:20 DEBUG  WindowsBackend: windows version=xp
10-05 20:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 20:20 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-05 20:20 DEBUG  WindowsBackend: windows_build=2600
10-05 20:20 DEBUG  WindowsBackend: gmt=1
10-05 20:20 DEBUG  WindowsBackend: country=GB
10-05 20:20 DEBUG  WindowsBackend: timezone=Europe/London
10-05 20:20 DEBUG  WindowsBackend: windows_username=Administrator
10-05 20:20 DEBUG  WindowsBackend: user_full_name=Administrator
10-05 20:20 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-05 20:20 DEBUG  WindowsBackend: windows_language_code=1033
10-05 20:20 DEBUG  WindowsBackend: windows_language=English
10-05 20:20 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-05 20:20 DEBUG  WindowsBackend: bootloader=xp
10-05 20:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8854.36230469 mb free ntfs)
10-05 20:20 DEBUG  WindowsBackend: drive=Drive(C: hd 8854.36230469 mb free ntfs)
10-05 20:20 DEBUG  WindowsBackend: drive=Drive(D: hd 19067.21875 mb free fat32)
10-05 20:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-05 20:20 DEBUG  WindowsBackend: uninstaller_path=None
10-05 20:20 DEBUG  WindowsBackend: previous_target_dir=None
10-05 20:20 DEBUG  WindowsBackend: previous_distro_name=None
10-05 20:20 DEBUG  WindowsBackend: keyboard_id=134809609
10-05 20:20 DEBUG  WindowsBackend: keyboard_layout=gb
10-05 20:20 DEBUG  WindowsBackend: keyboard_variant=
10-05 20:20 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-05 20:20 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 20:20 DEBUG  CommonBackend: Searching for local CDs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu Netbook CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 INFO   root: Running the installer...
10-05 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_GB', 'en']
10-05 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_GB', 'en']
10-05 20:20 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=mike
10-05 20:20 INFO   root: Received settings
10-05 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_GB', 'en']
10-05 20:20 DEBUG  TaskList: # Running tasklist...
10-05 20:20 DEBUG  TaskList: ## Running select_target_dir...
10-05 20:20 INFO   WindowsBackend: Installing into D:\ubuntu
10-05 20:20 DEBUG  TaskList: ## Finished select_target_dir
10-05 20:20 DEBUG  TaskList: ## Running create_dir_structure...
10-05 20:20 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-05 20:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-05 20:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-05 20:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-05 20:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-05 20:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-05 20:20 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-05 20:20 DEBUG  TaskList: ## Finished create_dir_structure
10-05 20:20 DEBUG  TaskList: ## Running uncompress_target_dir...
10-05 20:20 DEBUG  TaskList: ## Finished uncompress_target_dir
10-05 20:20 DEBUG  TaskList: ## Running create_uninstaller...
10-05 20:20 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\OUNN4SGV\wubi[1].exe -> D:\ubuntu\uninstall-wubi.exe
10-05 20:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-05 20:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-05 20:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-05 20:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-05 20:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
10-05 20:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-05 20:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-05 20:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-05 20:20 DEBUG  TaskList: ## Finished create_uninstaller
10-05 20:20 DEBUG  TaskList: ## Running copy_installation_files...
10-05 20:20 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-05 20:20 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\winboot -> D:\ubuntu\winboot
10-05 20:20 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-05 20:20 DEBUG  TaskList: ## Finished copy_installation_files
10-05 20:20 DEBUG  TaskList: ## Running get_iso...
10-05 20:20 DEBUG  CommonBackend: Searching for local CD
10-05 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:20 DEBUG  CommonBackend: Searching for local ISO
10-05 20:21 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-05 20:21 DEBUG  TaskList: New task get_metalink
10-05 20:21 DEBUG  TaskList: ### Running get_metalink...
10-05 20:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > D:\ubuntu\install
10-05 20:21 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
10-05 20:21 DEBUG  downloader: download finished (read 28158 bytes)
10-05 20:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > D:\ubuntu\install
10-05 20:21 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
10-05 20:21 DEBUG  downloader: download finished (read 874 bytes)
10-05 20:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
10-05 20:21 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-05 20:21 DEBUG  downloader: download finished (read 198 bytes)
10-05 20:21 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-05 20:21 INFO   saplog: Checking block bindings..
10-05 20:21 INFO   saplog: Key verified successfully.
10-05 20:21 DEBUG  CommonBackend: metalink md5sums:
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
10-05 20:21 DEBUG  TaskList: ### Finished get_metalink
10-05 20:21 DEBUG  TaskList: New task download
10-05 20:21 DEBUG  TaskList: ### Running download...
10-05 20:21 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-05 20:36 INFO   root: === wubi 11.04 rev211 ===
10-05 20:36 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
10-05 20:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Administrator\\Local Settings\\Temporary Internet Files\\Content.IE5\\N939HN06\\wubi[2].exe"']
10-05 20:36 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\data
10-05 20:36 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\bin\7z.exe
10-05 20:36 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
10-05 20:36 DEBUG  CommonBackend: Fetching basic info...
10-05 20:36 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\N939HN06\wubi[2].exe
10-05 20:36 DEBUG  CommonBackend: platform=win32
10-05 20:36 DEBUG  CommonBackend: osname=nt
10-05 20:36 DEBUG  CommonBackend: language=en_GB
10-05 20:36 DEBUG  CommonBackend: encoding=cp1252
10-05 20:36 DEBUG  WindowsBackend: arch=i386
10-05 20:36 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\data\isolist.ini
10-05 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 20:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-05 20:36 DEBUG  WindowsBackend: Fetching host info...
10-05 20:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 20:36 DEBUG  WindowsBackend: windows version=xp
10-05 20:36 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 20:36 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-05 20:36 DEBUG  WindowsBackend: windows_build=2600
10-05 20:36 DEBUG  WindowsBackend: gmt=1
10-05 20:36 DEBUG  WindowsBackend: country=GB
10-05 20:36 DEBUG  WindowsBackend: timezone=Europe/London
10-05 20:36 DEBUG  WindowsBackend: windows_username=Administrator
10-05 20:36 DEBUG  WindowsBackend: user_full_name=Administrator
10-05 20:36 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-05 20:36 DEBUG  WindowsBackend: windows_language_code=1033
10-05 20:36 DEBUG  WindowsBackend: windows_language=English
10-05 20:36 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-05 20:36 DEBUG  WindowsBackend: bootloader=xp
10-05 20:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8845.00830078 mb free ntfs)
10-05 20:36 DEBUG  WindowsBackend: drive=Drive(C: hd 8845.00830078 mb free ntfs)
10-05 20:36 DEBUG  WindowsBackend: drive=Drive(D: hd 18997.7734375 mb free ntfs)
10-05 20:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-05 20:36 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-05 20:36 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-05 20:36 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-05 20:36 DEBUG  WindowsBackend: keyboard_id=134809609
10-05 20:36 DEBUG  WindowsBackend: keyboard_layout=gb
10-05 20:36 DEBUG  WindowsBackend: keyboard_variant=
10-05 20:36 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-05 20:36 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-05 20:36 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-05 20:36 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 20:36 DEBUG  CommonBackend: Searching for local CDs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Ubuntu Netbook CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Kubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Kubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Xubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Xubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Mythbuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Mythbuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 INFO   root: Running the installer...
10-05 20:36 DEBUG  WindowsFrontend: __init__...
10-05 20:36 DEBUG  WindowsFrontend: on_init...
10-05 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\translations, languages=['en_GB', 'en']
10-05 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\translations, languages=['en_GB', 'en']
10-05 20:36 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=mike
10-05 20:36 INFO   root: Received settings
10-05 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\translations, languages=['en_GB', 'en']
10-05 20:36 DEBUG  TaskList: # Running tasklist...
10-05 20:36 DEBUG  TaskList: ## Running select_target_dir...
10-05 20:36 INFO   WindowsBackend: Installing into D:\ubuntu
10-05 20:36 DEBUG  TaskList: ## Finished select_target_dir
10-05 20:36 DEBUG  TaskList: ## Running create_dir_structure...
10-05 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-05 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-05 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-05 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-05 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-05 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-05 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-05 20:36 DEBUG  TaskList: ## Finished create_dir_structure
10-05 20:36 DEBUG  TaskList: ## Running uncompress_target_dir...
10-05 20:36 DEBUG  TaskList: ## Finished uncompress_target_dir
10-05 20:36 DEBUG  TaskList: ## Running create_uninstaller...
10-05 20:36 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\N939HN06\wubi[2].exe -> D:\ubuntu\uninstall-wubi.exe
10-05 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-05 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-05 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-05 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-05 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
10-05 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-05 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-05 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-05 20:36 DEBUG  TaskList: ## Finished create_uninstaller
10-05 20:36 DEBUG  TaskList: ## Running copy_installation_files...
10-05 20:36 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-05 20:36 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\winboot -> D:\ubuntu\winboot
10-05 20:36 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-05 20:36 DEBUG  TaskList: ## Finished copy_installation_files
10-05 20:36 DEBUG  TaskList: ## Running get_iso...
10-05 20:36 DEBUG  CommonBackend: Searching for local CD
10-05 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl29.tmp\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 20:36 DEBUG  CommonBackend: Searching for local ISO
10-05 20:36 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-05 20:36 DEBUG  TaskList: New task get_metalink
10-05 20:36 DEBUG  TaskList: ### Running get_metalink...
10-05 20:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > D:\ubuntu\install
10-05 20:36 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
10-05 20:36 DEBUG  downloader: download finished (read 28158 bytes)
10-05 20:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > D:\ubuntu\install
10-05 20:36 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
10-05 20:36 DEBUG  downloader: download finished (read 874 bytes)
10-05 20:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
10-05 20:36 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-05 20:36 DEBUG  downloader: download finished (read 198 bytes)
10-05 20:36 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-05 20:36 INFO   saplog: Checking block bindings..
10-05 20:36 INFO   saplog: Key verified successfully.
10-05 20:36 DEBUG  CommonBackend: metalink md5sums:
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
10-05 20:36 DEBUG  TaskList: ### Finished get_metalink
10-05 20:36 DEBUG  TaskList: New task download
10-05 20:36 DEBUG  TaskList: ### Running download...
10-05 20:36 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-05 21:03 INFO   WindowsFrontend: Operation cancelled
10-05 21:03 DEBUG  WindowsFrontend: frontend.quit
10-05 21:03 DEBUG  WindowsFrontend: frontend.on_quit
10-05 21:03 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
10-05 21:03 DEBUG  TaskList: # Cancelling tasklist
10-05 21:03 DEBUG  TaskList: ### Finished download
10-05 21:03 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
10-05 21:03 DEBUG  root: application.on_quit
10-05 21:03 DEBUG  root: Forceful exit
10-05 21:03 INFO   root: sys.exit
10-05 21:09 INFO   root: === wubi 11.04 rev211 ===
10-05 21:09 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
10-05 21:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
10-05 21:09 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\data
10-05 21:09 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\bin\7z.exe
10-05 21:09 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
10-05 21:09 DEBUG  CommonBackend: Fetching basic info...
10-05 21:09 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-05 21:09 DEBUG  CommonBackend: platform=win32
10-05 21:09 DEBUG  CommonBackend: osname=nt
10-05 21:09 DEBUG  CommonBackend: language=en_GB
10-05 21:09 DEBUG  CommonBackend: encoding=cp1252
10-05 21:09 DEBUG  WindowsBackend: arch=i386
10-05 21:09 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\data\isolist.ini
10-05 21:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-05 21:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-05 21:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-05 21:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-05 21:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-05 21:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-05 21:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-05 21:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-05 21:09 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-05 21:09 DEBUG  WindowsBackend: Fetching host info...
10-05 21:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-05 21:09 DEBUG  WindowsBackend: windows version=xp
10-05 21:09 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-05 21:09 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-05 21:09 DEBUG  WindowsBackend: windows_build=2600
10-05 21:09 DEBUG  WindowsBackend: gmt=1
10-05 21:09 DEBUG  WindowsBackend: country=GB
10-05 21:09 DEBUG  WindowsBackend: timezone=Europe/London
10-05 21:09 DEBUG  WindowsBackend: windows_username=Administrator
10-05 21:09 DEBUG  WindowsBackend: user_full_name=Administrator
10-05 21:09 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-05 21:09 DEBUG  WindowsBackend: windows_language_code=1033
10-05 21:09 DEBUG  WindowsBackend: windows_language=English
10-05 21:09 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-05 21:09 DEBUG  WindowsBackend: bootloader=xp
10-05 21:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8840.02783203 mb free ntfs)
10-05 21:09 DEBUG  WindowsBackend: drive=Drive(C: hd 8840.02783203 mb free ntfs)
10-05 21:09 DEBUG  WindowsBackend: drive=Drive(D: hd 18935.0703125 mb free ntfs)
10-05 21:09 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-05 21:09 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-05 21:09 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-05 21:09 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-05 21:09 DEBUG  WindowsBackend: keyboard_id=134809609
10-05 21:09 DEBUG  WindowsBackend: keyboard_layout=gb
10-05 21:09 DEBUG  WindowsBackend: keyboard_variant=
10-05 21:09 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-05 21:09 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-05 21:09 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-05 21:09 DEBUG  CommonBackend: Searching ISOs on USB devices
10-05 21:09 DEBUG  CommonBackend: Searching for local CDs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Ubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Ubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Ubuntu Netbook CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Kubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Kubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Xubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Xubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Mythbuntu CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp is a valid Mythbuntu CD
10-05 21:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-05 21:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-05 21:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-05 21:09 INFO   root: Running the uninstaller...
10-05 21:09 INFO   CommonBackend: This is the uninstaller running
10-05 21:09 DEBUG  WindowsFrontend: __init__...
10-05 21:09 DEBUG  WindowsFrontend: on_init...
10-05 21:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\translations, languages=['en_GB', 'en']
10-05 21:09 INFO   root: Received settings
10-05 21:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\translations, languages=['en_GB', 'en']
10-05 21:09 DEBUG  TaskList: # Running tasklist...
10-05 21:09 DEBUG  TaskList: ## Running Backup ISO...
10-05 21:09 DEBUG  TaskList: ## Finished Backup ISO
10-05 21:09 DEBUG  TaskList: ## Running Remove bootloader entry....
10-05 21:09 ERROR  WindowsBackend: Cannot find bcdedit
10-05 21:09 DEBUG  WindowsBackend: undo_bootini C:
10-05 21:09 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8840.02783203 mb free ntfs)
10-05 21:09 DEBUG  WindowsBackend: undo_bootini D:
10-05 21:09 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 18935.0703125 mb free ntfs)
10-05 21:09 DEBUG  TaskList: ## Finished Remove bootloader entry.
10-05 21:09 DEBUG  TaskList: ## Running Remove target dir....
10-05 21:09 DEBUG  CommonBackend: Deleting D:\ubuntu
10-05 21:09 DEBUG  TaskList: ## Finished Remove target dir.
10-05 21:09 DEBUG  TaskList: ## Running Remove registry key....
10-05 21:09 DEBUG  TaskList: ## Finished Remove registry key.
10-05 21:09 DEBUG  TaskList: # Finished tasklist
10-05 21:09 INFO   root: Almost finished uninstalling
10-05 21:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3B.tmp\translations, languages=['en_GB', 'en']
10-05 21:09 INFO   root: Finished uninstallation
10-05 21:09 DEBUG  root: application.quit
10-05 21:09 DEBUG  WindowsFrontend: frontend.quit
10-05 21:09 DEBUG  WindowsFrontend: frontend.on_quit
10-05 21:09 DEBUG  root: application.on_quit
10-05 21:09 INFO   root: sys.exit
10-06 09:08 INFO   root: === wubi 11.04 rev211 ===
10-06 09:08 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
10-06 09:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Administrator\\Local Settings\\Temporary Internet Files\\Content.IE5\\N939HN06\\wubi[3].exe"']
10-06 09:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data
10-06 09:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
10-06 09:08 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
10-06 09:08 DEBUG  CommonBackend: Fetching basic info...
10-06 09:08 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\N939HN06\wubi[3].exe
10-06 09:08 DEBUG  CommonBackend: platform=win32
10-06 09:08 DEBUG  CommonBackend: osname=nt
10-06 09:08 DEBUG  CommonBackend: language=en_GB
10-06 09:08 DEBUG  CommonBackend: encoding=cp1252
10-06 09:08 DEBUG  WindowsBackend: arch=i386
10-06 09:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
10-06 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-06 09:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-06 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-06 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-06 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-06 09:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-06 09:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-06 09:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-06 09:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-06 09:08 DEBUG  WindowsBackend: Fetching host info...
10-06 09:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-06 09:08 DEBUG  WindowsBackend: windows version=xp
10-06 09:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-06 09:08 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-06 09:08 DEBUG  WindowsBackend: windows_build=2600
10-06 09:08 DEBUG  WindowsBackend: gmt=1
10-06 09:08 DEBUG  WindowsBackend: country=GB
10-06 09:08 DEBUG  WindowsBackend: timezone=Europe/London
10-06 09:08 DEBUG  WindowsBackend: windows_username=Administrator
10-06 09:08 DEBUG  WindowsBackend: user_full_name=Administrator
10-06 09:08 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-06 09:08 DEBUG  WindowsBackend: windows_language_code=1033
10-06 09:08 DEBUG  WindowsBackend: windows_language=English
10-06 09:08 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-06 09:08 DEBUG  WindowsBackend: bootloader=xp
10-06 09:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8849.30126953 mb free ntfs)
10-06 09:08 DEBUG  WindowsBackend: drive=Drive(C: hd 8849.30126953 mb free ntfs)
10-06 09:08 DEBUG  WindowsBackend: drive=Drive(D: hd 18996.7460938 mb free ntfs)
10-06 09:08 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-06 09:08 DEBUG  WindowsBackend: uninstaller_path=None
10-06 09:08 DEBUG  WindowsBackend: previous_target_dir=None
10-06 09:08 DEBUG  WindowsBackend: previous_distro_name=None
10-06 09:08 DEBUG  WindowsBackend: keyboard_id=134809609
10-06 09:08 DEBUG  WindowsBackend: keyboard_layout=gb
10-06 09:08 DEBUG  WindowsBackend: keyboard_variant=
10-06 09:08 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-06 09:08 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-06 09:08 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-06 09:08 DEBUG  CommonBackend: Searching ISOs on USB devices
10-06 09:08 DEBUG  CommonBackend: Searching for local CDs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
10-06 09:08 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-06 09:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-06 09:08 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:08 INFO   root: Running the installer...
10-06 09:08 DEBUG  WindowsFrontend: __init__...
10-06 09:08 DEBUG  WindowsFrontend: on_init...
10-06 09:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
10-06 09:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
10-06 09:08 INFO   WindowsFrontend: Operation cancelled
10-06 09:08 DEBUG  WindowsFrontend: frontend.quit
10-06 09:08 DEBUG  WindowsFrontend: frontend.on_quit
10-06 09:08 DEBUG  root: application.on_quit
10-06 09:08 INFO   root: sys.exit
10-06 09:09 INFO   root: === wubi 11.04 rev211 ===
10-06 09:09 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
10-06 09:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Administrator\\Local Settings\\Temporary Internet Files\\Content.IE5\\OUNN4SGV\\wubi[2].exe"']
10-06 09:09 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\data
10-06 09:09 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\bin\7z.exe
10-06 09:09 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
10-06 09:09 DEBUG  CommonBackend: Fetching basic info...
10-06 09:09 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\OUNN4SGV\wubi[2].exe
10-06 09:09 DEBUG  CommonBackend: platform=win32
10-06 09:09 DEBUG  CommonBackend: osname=nt
10-06 09:09 DEBUG  CommonBackend: language=en_GB
10-06 09:09 DEBUG  CommonBackend: encoding=cp1252
10-06 09:09 DEBUG  WindowsBackend: arch=i386
10-06 09:09 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
10-06 09:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-06 09:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-06 09:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-06 09:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-06 09:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-06 09:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-06 09:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-06 09:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-06 09:09 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-06 09:09 DEBUG  WindowsBackend: Fetching host info...
10-06 09:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-06 09:09 DEBUG  WindowsBackend: windows version=xp
10-06 09:09 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-06 09:09 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-06 09:09 DEBUG  WindowsBackend: windows_build=2600
10-06 09:09 DEBUG  WindowsBackend: gmt=1
10-06 09:09 DEBUG  WindowsBackend: country=GB
10-06 09:09 DEBUG  WindowsBackend: timezone=Europe/London
10-06 09:09 DEBUG  WindowsBackend: windows_username=Administrator
10-06 09:09 DEBUG  WindowsBackend: user_full_name=Administrator
10-06 09:09 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-06 09:09 DEBUG  WindowsBackend: windows_language_code=1033
10-06 09:09 DEBUG  WindowsBackend: windows_language=English
10-06 09:09 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-06 09:09 DEBUG  WindowsBackend: bootloader=xp
10-06 09:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8846.5234375 mb free ntfs)
10-06 09:09 DEBUG  WindowsBackend: drive=Drive(C: hd 8846.5234375 mb free ntfs)
10-06 09:09 DEBUG  WindowsBackend: drive=Drive(D: hd 18996.7460938 mb free ntfs)
10-06 09:09 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-06 09:09 DEBUG  WindowsBackend: uninstaller_path=None
10-06 09:09 DEBUG  WindowsBackend: previous_target_dir=None
10-06 09:09 DEBUG  WindowsBackend: previous_distro_name=None
10-06 09:09 DEBUG  WindowsBackend: keyboard_id=134809609
10-06 09:09 DEBUG  WindowsBackend: keyboard_layout=gb
10-06 09:09 DEBUG  WindowsBackend: keyboard_variant=
10-06 09:09 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-06 09:09 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-06 09:09 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-06 09:09 DEBUG  CommonBackend: Searching ISOs on USB devices
10-06 09:09 DEBUG  CommonBackend: Searching for local CDs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu Netbook CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 INFO   root: Running the installer...
10-06 09:09 DEBUG  WindowsFrontend: __init__...
10-06 09:09 DEBUG  WindowsFrontend: on_init...
10-06 09:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_GB', 'en']
10-06 09:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_GB', 'en']
10-06 09:09 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=mike
10-06 09:09 INFO   root: Received settings
10-06 09:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_GB', 'en']
10-06 09:09 DEBUG  TaskList: # Running tasklist...
10-06 09:09 DEBUG  TaskList: ## Running select_target_dir...
10-06 09:09 INFO   WindowsBackend: Installing into D:\ubuntu
10-06 09:09 DEBUG  TaskList: ## Finished select_target_dir
10-06 09:09 DEBUG  TaskList: ## Running create_dir_structure...
10-06 09:09 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-06 09:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-06 09:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-06 09:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-06 09:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-06 09:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-06 09:09 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-06 09:09 DEBUG  TaskList: ## Finished create_dir_structure
10-06 09:09 DEBUG  TaskList: ## Running uncompress_target_dir...
10-06 09:09 DEBUG  TaskList: ## Finished uncompress_target_dir
10-06 09:09 DEBUG  TaskList: ## Running create_uninstaller...
10-06 09:09 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\OUNN4SGV\wubi[2].exe -> D:\ubuntu\uninstall-wubi.exe
10-06 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-06 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-06 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-06 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-06 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
10-06 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-06 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-06 09:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-06 09:09 DEBUG  TaskList: ## Finished create_uninstaller
10-06 09:09 DEBUG  TaskList: ## Running copy_installation_files...
10-06 09:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-06 09:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\winboot -> D:\ubuntu\winboot
10-06 09:09 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-06 09:09 DEBUG  TaskList: ## Finished copy_installation_files
10-06 09:09 DEBUG  TaskList: ## Running get_iso...
10-06 09:09 DEBUG  CommonBackend: Searching for local CD
10-06 09:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-06 09:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-06 09:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-06 09:09 DEBUG  CommonBackend: Searching for local ISO
10-06 09:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-06 09:09 DEBUG  TaskList: New task get_metalink
10-06 09:09 DEBUG  TaskList: ### Running get_metalink...
10-06 09:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > D:\ubuntu\install
10-06 09:09 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
10-06 09:09 DEBUG  downloader: download finished (read 28158 bytes)
10-06 09:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > D:\ubuntu\install
10-06 09:09 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
10-06 09:09 DEBUG  downloader: download finished (read 874 bytes)
10-06 09:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
10-06 09:09 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-06 09:09 DEBUG  downloader: download finished (read 198 bytes)
10-06 09:09 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-06 09:09 INFO   saplog: Checking block bindings..
10-06 09:09 INFO   saplog: Key verified successfully.
10-06 09:09 DEBUG  CommonBackend: metalink md5sums:
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
10-06 09:09 DEBUG  TaskList: ### Finished get_metalink
10-06 09:09 DEBUG  TaskList: New task download
10-06 09:09 DEBUG  TaskList: ### Running download...
10-06 09:09 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:24 DEBUG  TaskList: ### Finished download
10-06 09:24 DEBUG  TaskList: New task check_iso
10-06 09:24 DEBUG  TaskList: ### Running check_iso...
10-06 09:24 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:24 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:24 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:24 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-06 09:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
10-06 09:24 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:24 DEBUG  TaskList: New task get_file_md5
10-06 09:24 DEBUG  TaskList: #### Running get_file_md5...
10-06 09:26 DEBUG  TaskList: #### Finished get_file_md5
10-06 09:26 DEBUG  TaskList: ### Finished check_iso
10-06 09:26 DEBUG  TaskList: ## Finished get_iso
10-06 09:26 DEBUG  TaskList: ## Running extract_kernel...
10-06 09:26 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:26 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:26 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:26 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-06 09:26 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-06 09:26 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-06 09:26 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
10-06 09:26 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-06 09:26 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
10-06 09:26 DEBUG  TaskList: ## Finished extract_kernel
10-06 09:26 DEBUG  TaskList: ## Running choose_disk_sizes...
10-06 09:26 DEBUG  WindowsBackend: total size=5000
  root=4744
  swap=256
  home=0
  usr=0
10-06 09:26 DEBUG  TaskList: ## Finished choose_disk_sizes
10-06 09:26 DEBUG  TaskList: ## Running create_preseed...
10-06 09:26 DEBUG  TaskList: ## Finished create_preseed
10-06 09:26 DEBUG  TaskList: ## Running modify_bootloader...
10-06 09:26 DEBUG  TaskList: New task modify_bootini
10-06 09:26 DEBUG  TaskList: ### Running modify_bootini...
10-06 09:26 DEBUG  WindowsBackend: modify_bootini C:
10-06 09:26 DEBUG  TaskList: ### Finished modify_bootini
10-06 09:26 DEBUG  TaskList: New task modify_bootini
10-06 09:26 DEBUG  TaskList: ### Running modify_bootini...
10-06 09:26 DEBUG  WindowsBackend: modify_bootini D:
10-06 09:26 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
10-06 09:26 DEBUG  TaskList: ### Finished modify_bootini
10-06 09:26 DEBUG  TaskList: ## Finished modify_bootloader
10-06 09:26 DEBUG  TaskList: ## Running modify_grub_configuration...
10-06 09:26 DEBUG  TaskList: ## Finished modify_grub_configuration
10-06 09:26 DEBUG  TaskList: ## Running create_virtual_disks...
10-06 09:26 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 4744MB
10-06 09:26 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
10-06 09:26 DEBUG  TaskList: ## Finished create_virtual_disks
10-06 09:26 DEBUG  TaskList: ## Running uncompress_files...
10-06 09:26 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
10-06 09:26 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
10-06 09:26 DEBUG  TaskList: ## Finished uncompress_files
10-06 09:26 DEBUG  TaskList: ## Running eject_cd...
10-06 09:26 DEBUG  TaskList: ## Finished eject_cd
10-06 09:26 DEBUG  TaskList: # Finished tasklist
10-06 09:26 INFO   root: Almost finished installing
10-06 09:26 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_GB', 'en']
10-06 09:26 INFO   root: Finished installation
10-06 09:26 INFO   root: Rebooting
10-06 09:26 DEBUG  TaskList: # Running tasklist...
10-06 09:26 DEBUG  TaskList: ## Running reboot...
10-06 09:26 DEBUG  TaskList: ## Finished reboot
10-06 09:26 DEBUG  TaskList: # Finished tasklist
10-06 09:26 DEBUG  root: application.quit
10-06 09:26 DEBUG  WindowsFrontend: frontend.quit
10-06 09:26 DEBUG  WindowsFrontend: frontend.on_quit
10-06 09:26 DEBUG  root: application.on_quit
10-06 09:26 INFO   root: sys.exit
01-01 13:09 INFO   root: === wubi 11.04 rev211 ===
01-01 13:09 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
01-01 13:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
01-01 13:09 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data
01-01 13:09 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
01-01 13:09 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
01-01 13:09 DEBUG  CommonBackend: Fetching basic info...
01-01 13:09 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
01-01 13:09 DEBUG  CommonBackend: platform=win32
01-01 13:09 DEBUG  CommonBackend: osname=nt
01-01 13:09 DEBUG  CommonBackend: language=en_GB
01-01 13:09 DEBUG  CommonBackend: encoding=cp1252
01-01 13:09 DEBUG  WindowsBackend: arch=i386
01-01 13:09 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
01-01 13:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-01 13:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-01 13:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-01 13:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-01 13:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-01 13:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-01 13:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-01 13:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-01 13:09 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-01 13:09 DEBUG  WindowsBackend: Fetching host info...
01-01 13:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-01 13:09 DEBUG  WindowsBackend: windows version=xp
01-01 13:09 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-01 13:09 DEBUG  WindowsBackend: windows_sp=Service Pack 3
01-01 13:09 DEBUG  WindowsBackend: windows_build=2600
01-01 13:09 DEBUG  WindowsBackend: gmt=1
01-01 13:09 DEBUG  WindowsBackend: country=GB
01-01 13:09 DEBUG  WindowsBackend: timezone=Europe/London
01-01 13:09 DEBUG  WindowsBackend: windows_username=Administrator
01-01 13:09 DEBUG  WindowsBackend: user_full_name=Administrator
01-01 13:09 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
01-01 13:09 DEBUG  WindowsBackend: windows_language_code=1033
01-01 13:09 DEBUG  WindowsBackend: windows_language=English
01-01 13:09 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
01-01 13:09 DEBUG  WindowsBackend: bootloader=xp
01-01 13:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8760.21679688 mb free ntfs)
01-01 13:09 DEBUG  WindowsBackend: drive=Drive(C: hd 8760.21679688 mb free ntfs)
01-01 13:09 DEBUG  WindowsBackend: drive=Drive(D: hd 13309.7890625 mb free ntfs)
01-01 13:09 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-01 13:09 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
01-01 13:09 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
01-01 13:09 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-01 13:09 DEBUG  WindowsBackend: keyboard_id=134809609
01-01 13:09 DEBUG  WindowsBackend: keyboard_layout=gb
01-01 13:09 DEBUG  WindowsBackend: keyboard_variant=
01-01 13:09 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
01-01 13:09 DEBUG  CommonBackend: locale=en_GB.UTF-8
01-01 13:09 DEBUG  WindowsBackend: total_memory_mb=510.796875
01-01 13:09 DEBUG  CommonBackend: Searching ISOs on USB devices
01-01 13:09 DEBUG  CommonBackend: Searching for local CDs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
01-01 13:09 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-01 13:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-01 13:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-01 13:09 INFO   root: Running the uninstaller...
01-01 13:09 INFO   CommonBackend: This is the uninstaller running
01-01 13:09 DEBUG  WindowsFrontend: __init__...
01-01 13:09 DEBUG  WindowsFrontend: on_init...
01-01 13:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
01-01 13:09 INFO   root: Received settings
01-01 13:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
01-01 13:09 DEBUG  TaskList: # Running tasklist...
01-01 13:09 DEBUG  TaskList: ## Running Backup ISO...
01-01 13:09 DEBUG  TaskList: ## Finished Backup ISO
01-01 13:09 DEBUG  TaskList: ## Running Remove bootloader entry....
01-01 13:09 ERROR  WindowsBackend: Cannot find bcdedit
01-01 13:09 DEBUG  WindowsBackend: undo_bootini C:
01-01 13:10 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8760.21679688 mb free ntfs)
01-01 13:10 DEBUG  WindowsBackend: undo_bootini D:
01-01 13:10 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 13309.7890625 mb free ntfs)
01-01 13:10 DEBUG  TaskList: ## Finished Remove bootloader entry.
01-01 13:10 DEBUG  TaskList: ## Running Remove target dir....
01-01 13:10 DEBUG  CommonBackend: Deleting D:\ubuntu
01-01 13:10 DEBUG  TaskList: ## Finished Remove target dir.
01-01 13:10 DEBUG  TaskList: ## Running Remove registry key....
01-01 13:10 DEBUG  TaskList: ## Finished Remove registry key.
01-01 13:10 DEBUG  TaskList: # Finished tasklist
01-01 13:10 INFO   root: Almost finished uninstalling
01-01 13:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
01-01 13:10 INFO   root: Finished uninstallation
01-01 13:10 DEBUG  root: application.quit
01-01 13:10 DEBUG  WindowsFrontend: frontend.quit
01-01 13:10 DEBUG  WindowsFrontend: frontend.on_quit
01-01 13:10 DEBUG  root: application.on_quit
01-01 13:10 INFO   root: sys.exit
10-18 08:06 INFO   root: === wubi 11.04 rev211 ===
10-18 08:06 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
10-18 08:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Administrator\\Local Settings\\Temporary Internet Files\\Content.IE5\\OUNN4SGV\\wubi[2].exe"']
10-18 08:06 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data
10-18 08:06 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
10-18 08:06 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
10-18 08:06 DEBUG  CommonBackend: Fetching basic info...
10-18 08:06 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Administrator\Local Settings\Temporary Internet Files\Content.IE5\OUNN4SGV\wubi[2].exe
10-18 08:06 DEBUG  CommonBackend: platform=win32
10-18 08:06 DEBUG  CommonBackend: osname=nt
10-18 08:06 DEBUG  CommonBackend: language=en_GB
10-18 08:06 DEBUG  CommonBackend: encoding=cp1252
10-18 08:06 DEBUG  WindowsBackend: arch=i386
10-18 08:06 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
10-18 08:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 08:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 08:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 08:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 08:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 08:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 08:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 08:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 08:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 08:06 DEBUG  WindowsBackend: Fetching host info...
10-18 08:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 08:06 DEBUG  WindowsBackend: windows version=xp
10-18 08:06 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-18 08:06 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-18 08:06 DEBUG  WindowsBackend: windows_build=2600
10-18 08:06 DEBUG  WindowsBackend: gmt=1
10-18 08:06 DEBUG  WindowsBackend: country=GB
10-18 08:06 DEBUG  WindowsBackend: timezone=Europe/London
10-18 08:06 DEBUG  WindowsBackend: windows_username=Administrator
10-18 08:06 DEBUG  WindowsBackend: user_full_name=Administrator
10-18 08:06 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-18 08:06 DEBUG  WindowsBackend: windows_language_code=1033
10-18 08:06 DEBUG  WindowsBackend: windows_language=English
10-18 08:06 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-18 08:06 DEBUG  WindowsBackend: bootloader=xp
10-18 08:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8395.09814453 mb free ntfs)
10-18 08:06 DEBUG  WindowsBackend: drive=Drive(C: hd 8395.09814453 mb free ntfs)
10-18 08:06 DEBUG  WindowsBackend: drive=Drive(D: hd 15482.34375 mb free ntfs)
10-18 08:06 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-18 08:06 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-18 08:06 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-18 08:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-18 08:06 DEBUG  WindowsBackend: keyboard_id=134809609
10-18 08:06 DEBUG  WindowsBackend: keyboard_layout=gb
10-18 08:06 DEBUG  WindowsBackend: keyboard_variant=
10-18 08:06 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-18 08:06 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-18 08:06 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-18 08:06 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 08:06 DEBUG  CommonBackend: Searching for local CDs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
10-18 08:06 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 08:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-18 08:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 08:06 INFO   root: Already installed, running the uninstaller...
10-18 08:06 INFO   root: Running the uninstaller...
10-18 08:06 INFO   CommonBackend: Launching previous uninestaller D:\ubuntu\uninstall-wubi.exe
10-18 08:07 DEBUG  root: application.quit
10-18 08:07 DEBUG  root: application.on_quit
10-18 08:07 INFO   root: sys.exit
10-18 08:07 INFO   root: Quitting application
10-18 14:55 INFO   root: === wubi 11.04 rev211 ===
10-18 14:55 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-11.04-rev211.log
10-18 14:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
10-18 14:55 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data
10-18 14:55 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
10-18 14:55 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
10-18 14:55 DEBUG  CommonBackend: Fetching basic info...
10-18 14:55 DEBUG  CommonBackend: original_exe=F:\wubi.exe
10-18 14:55 DEBUG  CommonBackend: platform=win32
10-18 14:55 DEBUG  CommonBackend: osname=nt
10-18 14:55 DEBUG  CommonBackend: language=en_GB
10-18 14:55 DEBUG  CommonBackend: encoding=cp1252
10-18 14:55 DEBUG  WindowsBackend: arch=i386
10-18 14:55 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
10-18 14:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-18 14:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-18 14:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-18 14:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-18 14:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-18 14:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-18 14:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-18 14:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-18 14:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-18 14:55 DEBUG  WindowsBackend: Fetching host info...
10-18 14:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-18 14:55 DEBUG  WindowsBackend: windows version=xp
10-18 14:55 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
10-18 14:55 DEBUG  WindowsBackend: windows_sp=Service Pack 3
10-18 14:55 DEBUG  WindowsBackend: windows_build=2600
10-18 14:55 DEBUG  WindowsBackend: gmt=1
10-18 14:55 DEBUG  WindowsBackend: country=GB
10-18 14:55 DEBUG  WindowsBackend: timezone=Europe/London
10-18 14:55 DEBUG  WindowsBackend: windows_username=Administrator
10-18 14:55 DEBUG  WindowsBackend: user_full_name=Administrator
10-18 14:55 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
10-18 14:55 DEBUG  WindowsBackend: windows_language_code=1033
10-18 14:55 DEBUG  WindowsBackend: windows_language=English
10-18 14:55 DEBUG  WindowsBackend: processor_name=       Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz
10-18 14:55 DEBUG  WindowsBackend: bootloader=xp
10-18 14:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7636.30078125 mb free ntfs)
10-18 14:55 DEBUG  WindowsBackend: drive=Drive(C: hd 7636.30078125 mb free ntfs)
10-18 14:55 DEBUG  WindowsBackend: drive=Drive(D: hd 19058.5 mb free fat32)
10-18 14:55 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-18 14:55 DEBUG  WindowsBackend: drive=Drive(F: removable 3210.04296875 mb free fat32)
10-18 14:55 DEBUG  WindowsBackend: uninstaller_path=None
10-18 14:55 DEBUG  WindowsBackend: previous_target_dir=None
10-18 14:55 DEBUG  WindowsBackend: previous_distro_name=None
10-18 14:55 DEBUG  WindowsBackend: keyboard_id=134809609
10-18 14:55 DEBUG  WindowsBackend: keyboard_layout=gb
10-18 14:55 DEBUG  WindowsBackend: keyboard_variant=
10-18 14:55 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
10-18 14:55 DEBUG  CommonBackend: locale=en_GB.UTF-8
10-18 14:55 DEBUG  WindowsBackend: total_memory_mb=510.796875
10-18 14:55 DEBUG  CommonBackend: Searching ISOs on USB devices
10-18 14:55 DEBUG  CommonBackend: Searching for local CDs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
10-18 14:55 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-18 14:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-18 14:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-18 14:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-18 14:55 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-18 14:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
10-18 14:55 DEBUG  Distro: wrong arch: i386 != amd64
10-18 14:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-18 14:55 INFO   Distro: Found a valid CD for Ubuntu: F:\
10-18 14:55 INFO   root: Running the CD menu...
10-18 14:55 DEBUG  WindowsFrontend: __init__...
10-18 14:55 DEBUG  WindowsFrontend: on_init...
10-18 14:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
10-18 14:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
10-18 14:56 INFO   root: CD menu finished
10-18 14:56 INFO   root: Running the installer...
10-18 14:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
10-18 14:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
10-18 14:56 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=mike
10-18 14:56 INFO   root: Received settings
10-18 14:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_GB', 'en']
10-18 14:56 DEBUG  TaskList: # Running tasklist...
10-18 14:56 DEBUG  TaskList: ## Running select_target_dir...
10-18 14:56 INFO   WindowsBackend: Installing into D:\ubuntu
10-18 14:56 DEBUG  TaskList: ## Finished select_target_dir
10-18 14:56 DEBUG  TaskList: ## Running create_dir_structure...
10-18 14:56 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-18 14:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-18 14:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-18 14:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-18 14:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-18 14:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-18 14:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-18 14:56 DEBUG  TaskList: ## Finished create_dir_structure
10-18 14:56 DEBUG  TaskList: ## Running uncompress_target_dir...
10-18 14:56 DEBUG  TaskList: ## Finished uncompress_target_dir
10-18 14:56 DEBUG  TaskList: ## Running create_uninstaller...
10-18 14:56 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-18 14:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-18 14:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-18 14:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-18 14:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
10-18 14:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
10-18 14:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-18 14:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-18 14:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-18 14:56 DEBUG  TaskList: ## Finished create_uninstaller
10-18 14:56 DEBUG  TaskList: ## Running copy_installation_files...
10-18 14:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-18 14:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\winboot -> D:\ubuntu\winboot
10-18 14:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl4.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
10-18 14:56 DEBUG  TaskList: ## Finished copy_installation_files
10-18 14:56 DEBUG  TaskList: ## Running get_iso...
10-18 14:56 DEBUG  TaskList: New task copy_file
10-18 14:56 DEBUG  TaskList: ### Running copy_file...
10-18 16:35 DEBUG  TaskList: ### Finished copy_file
10-18 16:35 DEBUG  TaskList: New task check_iso
10-18 16:35 DEBUG  TaskList: ### Running check_iso...
10-18 16:35 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
10-18 16:35 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\installation.iso
10-18 16:35 DEBUG  Distro:     wrong size: 4110417920 > 900000000
10-18 16:35 DEBUG  TaskList: ### Finished check_iso
10-18 16:35 DEBUG  CommonBackend: Searching for local ISO
10-18 16:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
10-18 16:35 DEBUG  TaskList: New task get_metalink
10-18 16:35 DEBUG  TaskList: ### Running get_metalink...
10-18 16:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > D:\ubuntu\install
10-18 16:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
10-18 16:35 DEBUG  downloader: download finished (read 28158 bytes)
10-18 16:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > D:\ubuntu\install
10-18 16:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
10-18 16:35 DEBUG  downloader: download finished (read 874 bytes)
10-18 16:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
10-18 16:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
10-18 16:35 DEBUG  downloader: download finished (read 198 bytes)
10-18 16:35 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
10-18 16:35 INFO   saplog: Checking block bindings..
10-18 16:35 INFO   saplog: Key verified successfully.
10-18 16:35 DEBUG  CommonBackend: metalink md5sums:
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
10-18 16:35 DEBUG  TaskList: ### Finished get_metalink
10-18 16:35 DEBUG  TaskList: New task download
10-18 16:35 DEBUG  TaskList: ### Running download...
10-18 16:35 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent) > D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 16:55 DEBUG  TaskList: ### Finished download
10-18 16:55 DEBUG  TaskList: New task check_iso
10-18 16:55 DEBUG  TaskList: ### Running check_iso...
10-18 16:55 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 16:55 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 16:56 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 16:56 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
10-18 16:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
10-18 16:56 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 16:56 DEBUG  TaskList: New task get_file_md5
10-18 16:56 DEBUG  TaskList: #### Running get_file_md5...
10-18 17:01 DEBUG  TaskList: #### Finished get_file_md5
10-18 17:01 DEBUG  TaskList: ### Finished check_iso
10-18 17:01 DEBUG  TaskList: ## Finished get_iso
10-18 17:01 DEBUG  TaskList: ## Running extract_kernel...
10-18 17:01 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 17:01 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 17:01 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 17:01 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
10-18 17:01 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-18 17:01 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-18 17:01 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
10-18 17:01 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-18 17:01 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
10-18 17:01 DEBUG  TaskList: ## Finished extract_kernel
10-18 17:01 DEBUG  TaskList: ## Running choose_disk_sizes...
10-18 17:01 DEBUG  WindowsBackend: total size=5000
  root=1500
  swap=256
  home=0
  usr=3244
10-18 17:01 DEBUG  TaskList: ## Finished choose_disk_sizes
10-18 17:01 DEBUG  TaskList: ## Running create_preseed...
10-18 17:01 DEBUG  TaskList: ## Finished create_preseed
10-18 17:01 DEBUG  TaskList: ## Running modify_bootloader...
10-18 17:01 DEBUG  TaskList: New task modify_bootini
10-18 17:01 DEBUG  TaskList: ### Running modify_bootini...
10-18 17:01 DEBUG  WindowsBackend: modify_bootini C:
10-18 17:01 DEBUG  TaskList: ### Finished modify_bootini
10-18 17:01 DEBUG  TaskList: New task modify_bootini
10-18 17:01 DEBUG  TaskList: ### Running modify_bootini...
10-18 17:01 DEBUG  WindowsBackend: modify_bootini D:
10-18 17:01 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
10-18 17:01 DEBUG  TaskList: ### Finished modify_bootini
10-18 17:01 DEBUG  TaskList: New task modify_bootini
10-18 17:01 DEBUG  TaskList: ### Running modify_bootini...
10-18 17:01 DEBUG  WindowsBackend: modify_bootini F:
10-18 17:01 DEBUG  WindowsBackend: Could not find boot.ini F:\boot.ini
10-18 17:01 DEBUG  TaskList: ### Finished modify_bootini
10-18 17:01 DEBUG  TaskList: ## Finished modify_bootloader
10-18 17:01 DEBUG  TaskList: ## Running modify_grub_configuration...
10-18 17:01 DEBUG  TaskList: ## Finished modify_grub_configuration
10-18 17:01 DEBUG  TaskList: ## Running create_virtual_disks...
10-18 17:01 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 1500MB
10-18 17:11 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\usr.disk of 3244MB
10-18 17:25 INFO   WindowsFrontend: Operation cancelled
10-18 17:25 DEBUG  WindowsFrontend: frontend.quit
10-18 17:25 DEBUG  WindowsFrontend: frontend.on_quit
10-18 17:25 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
10-18 17:25 DEBUG  TaskList: # Cancelling tasklist
10-18 17:25 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
10-18 17:25 DEBUG  root: application.on_quit
10-18 17:25 DEBUG  root: Forceful exit
10-18 17:25 INFO   root: sys.exit
```

---

### Post by MonocleMike2 on 2011-10-18
Hang on everyone!!

I just tried rebooting and lo and behold it booted into the Ubuntu install process and appears to be trying to mend itself.
I'll let you know what happens.

---------------------------------------------------
I went away and it looks as if it finished and tried a restart which never worked.
I rebooted and grub can't find the kernel!
Rebooted again into recovery mode and took the menu option to repair grub.................Made no difference!
Rebooted again into recovery mode and took the menu option to fix the packages .................. this appears to be loading 224Mb of stuff from the archive store and is only 70% through.
I'll try to repair grub again when it finishes and if that doesn't work I'll have to plough through the grub help files to point it at a valid kernel ........... I'm sure there must be one there but it is getting late and I've been doing this for 13 hours straight already.  I may pack it in until the morning, I'll see whether a glass of wine revives me!! :-)

----------------------------------------------
I've just seen some entries saying it was repairing grub.cnfg and had found some kernels - maybe it has fixed itself.  I'll hang on for a while.

-----------------------------------------
It has added 2 new entries to the grubmenu and one works!  I can do no more tonight!  I look forward to your comments and suggestions in the morning.  Good night.

---

### Post by hansdown on 2011-10-18
Your patience is inspirational,MonocleMike2.

Hope all is wrking, now.

---

### Post by MonocleMike2 on 2011-10-19
Not working yet!
I have sent the following email to Boot Repair:
"The log from Boot Repair is at [http://paste.ubuntu.com/712914](http://paste.ubuntu.com/712914)

The machine is a very old Toshiba Satellite Pro that does not have the  hardware to run Unity and the wireless doesn't work under 11.10 so I am  trying to get back to 11.04 as that worked beautifully.

I am very nearly there because I can now boot a working copy of 11.04  however the boot menu is all wrong. The top entry of 2.6.38-11 fails as  it says "file not found" and that I need to load the kernel first.  The  second gives me a working copy of 2.6.38-11 but in recovery mode.  The  3rd entry gives me 2.6.38-8.  The 4th I haven't tried yet as I'm sure I  don't want it and the very last default entry is to just Windows and I  don't want that.

Please be so kind as to help."

Has anyone else any suggestions?

---

### Post by bcbc on 2011-10-19
You can't install wubi from a USB stick - it copies the entire partition as the ISO and then does a size check on it and fails it if the size is > 900,000,000 bytes. (So the partition has to be less than that for it to work, and these days most are a lot bigger).

If you get the 'no root file system defined' error it usually indicates the presence of partition table errors, an unsupported fakeraid (0 or 1+0) or presence of GPT partition data. The best way to find out is to boot from that USB, select "Try it" and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

PS fyi, you can download the wubi.exe and the desktop CD ISO into the same directory and run wubi from there without creating either a cd or usb. That works as long as you get them from the same release (ie. from that link forestpiskie gave you). But you first have to resolve the error you were getting.

---

### Post by MonocleMike2 on 2011-10-19
Thank you for your help.  Unfortunately I cannot take the first step - it will not boot from the stick.  It offers it as the boot device but if I select it then it ignores it and goes to the default of the hard disc.

However if you say I am on a hiding to nothing trying to install from the USB stick then I must write off the time I spent yesterday trying and proceed with trying to get a disk.  I'll use a partition manager in Windows to check the partitions are OK.  I wish the download site still offered 11.04 then I could repeat the original install over the web which worked perfectly.

Are you absolutely sure that there is no way I can install with wubi from this USB stick?  I used these instructions
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
and chose to use Unetbootin as mentioned in the Windows section.  However the stick would appear not to be bootable - I have tried it on 2 machines.  However does that affect the problem since I can run wub.exe from the stick.

I appear to have 3 choices:
1.  Mend the files on the stick
2.  Get a CD from somewhere
3.  Find a way to do a standard wubi install over the web.

---

### Post by bcbc on 2011-10-19
You don't need a cd or a usb stick to install with wubi. you need them to do a normal dual boot. (Wubi only installs inside windows with a virtual disk).
To install 11.04 wubi, download and run this: [http://releases.ubuntu.com/11.04/wubi.exe](http://releases.ubuntu.com/11.04/wubi.exe)

If you want to create a USB stick to try out Ubuntu or install it without using Wubi, then see the instructions[ here]("http://www.ubuntu.com/download/ubuntu/download"): Go to step 2, click on USB stick, and then SHOW ME HOW. Use those instructions with whatever desktop CD ISO you downloaded. If you already have the CD ISO on your hard drive you can reuse it.

---

### Post by MonocleMike2 on 2011-10-19
Thank you very much.  I will try all you have suggested.  I think it will probably be tomorrow before I post again as it is now 19:14 here in France.
Thank you again for your help and please keep an eye on this thread in case I get stuck again.;)

---

### Post by MonocleMike2 on 2011-10-19
> **bcbc said:**
> 
If you want to create a USB stick to try out Ubuntu or install it without using Wubi, then see the instructions here: Go to step 2, click on USB stick, and then SHOW ME HOW. Use those instructions with whatever desktop CD ISO you downloaded. If you already have the CD ISO on your hard drive you can reuse it.


Where is "here".  I think there is a link missing.

---

### Post by bcbc on 2011-10-19
My bad - I've edited the post to add it.

---

### Post by MonocleMike2 on 2011-10-19
Thank you.  I'll do it tomorrow.

---

### Post by jfbooth on 2011-10-19
> **MonocleMike2 said:**
> Thank you.  I'll do it tomorrow.

From my experience, BCBC is correct:

> You don't need a cd or a usb stick to install with wubi. you need them to do a normal dual boot. (Wubi only installs inside windows with a virtual disk).
To install 11.04 wubi, download and run this: [http://releases.ubuntu.com/11.04/wubi.exe](http://releases.ubuntu.com/11.04/wubi.exe)


I suggest that first, you undo everything you have done with UBUNTU.  Get back to a purely windows machine.  If possible, connect your computer via ETHERNET CABLE to your modem or router.  This is so you can connect to the 'NET after (Linux) is installed and get your WIFI drivers.

Go to [www.ubuntu.com](www.ubuntu.com).  Click on DOWNLOAD at the top.  Click on RUN IT WITH WINDOWS.  Click on START DOWNLOAD.  Click RUN, click RUN.  You should at that point be able to select what you want to install.  Which ever distro and ver .. (Ubuntu, Kubuntu, Xubuntu, etc .. along with your preferred version and 32-bit or 64-bit).

Follow the screens .. then reboot your computer.

To UNINSTALL (Linux), go to control panel in Windows and remove program UBUNTU.

I am referring to US English web pages .. not FRENCH.  I have done this several times .. and have never had any problems.

I hope this helps you.

---

### Post by MonocleMike2 on 2011-10-20
> **jfbooth said:**
> From my experience, BCBC is correct:

Go to [www.ubuntu.com]("http://www.ubuntu.com").  Click on DOWNLOAD at the top.  Click on RUN IT WITH WINDOWS.  Click on START DOWNLOAD.  Click RUN, click RUN.  You should at that point be able to select what you want to install.  Which ever distro and ver .. (Ubuntu, Kubuntu, Xubuntu, etc .. along with your preferred version and 32-bit or 64-bit).

  

Thank you bcbc -your URL worked.  It got the 11.04 installer.:popcorn:

Thank you jfbooth but your method does not offer you the choice of version no - only the distro.:(

Thank you all - the installation has started and I am off out.:popcorn::popcorn:

---

### Post by MonocleMike2 on 2011-10-20
It worked like a dream.
Thank you bcbc  if only you had seen my original question when I posted it then you could have provided your simple, direct and correct answer.
I am back up and running and I am typing this on the machine in question.
:popcorn::popcorn:

---

