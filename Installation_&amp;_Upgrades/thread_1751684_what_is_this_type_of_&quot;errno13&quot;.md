---
title: "what is this type of &quot;errno13&quot;?"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by Smidthmador on 2011-05-06
[Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'

I couldn't find it on the forum or Google so I thought I should just ask.  I'm trying to install Ubuntu Wubi onto my PC w/ MS and that's what it said.  

How can I remedy this?  I really wanna check Linux out!

---

### Post by bcbc on 2011-05-06
This error can be associated with a bad burn, bad image or even an optical drive incompatibility. I'd suspect a bad burn normally. You can check the CD by booting from it, hit the space bar when you see the little keyboard icon, and then from the extended menu, select to check the CD.

You can install wubi by placing wubi.exe and the desktop cd iso in the same folder (e.g. without having a cd) or just run wubi.exe standalone as well. (if you do this you have to remove the bad cd or wubi.exe will find it and use it).

---

### Post by Smidthmador on 2011-05-06
I'm not using a CD, I'm doing this via download.

How do I go about moving the Iso and exe files and where do I find them?

---

### Post by bcbc on 2011-05-07
Can you post the log file? Go to the %temp% directory and look for the wubi-11.04-rev211.log file.

Thanks

---

### Post by Smidthmador on 2011-05-07
I restarted my PC and instead of giving me the option of choosing an OS it did a disk check...  It deleted ehRecvr.ba1 in index $I30 of file 8429



05-06 15:29 INFO   root: === wubi 11.04 rev211 ===
05-06 15:29 DEBUG  root: Logfile is c:\docume~1\jake\locals~1\temp\wubi-11.04-rev211.log
05-06 15:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jake\\My Documents\\Downloads\\wubi.exe"']
05-06 15:29 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\data
05-06 15:29 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\bin\7z.exe
05-06 15:29 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
05-06 15:29 DEBUG  CommonBackend: Fetching basic info...
05-06 15:29 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe
05-06 15:29 DEBUG  CommonBackend: platform=win32
05-06 15:29 DEBUG  CommonBackend: osname=nt
05-06 15:29 DEBUG  CommonBackend: language=en_US
05-06 15:29 DEBUG  CommonBackend: encoding=cp1252
05-06 15:29 DEBUG  WindowsBackend: arch=amd64
05-06 15:29 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\data\isolist.ini
05-06 15:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-06 15:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-06 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-06 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-06 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-06 15:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-06 15:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-06 15:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-06 15:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-06 15:29 DEBUG  WindowsBackend: Fetching host info...
05-06 15:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-06 15:29 DEBUG  WindowsBackend: windows version=xp
05-06 15:29 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-06 15:29 DEBUG  WindowsBackend: windows_sp=Service Pack 3
05-06 15:29 DEBUG  WindowsBackend: windows_build=2600
05-06 15:29 DEBUG  WindowsBackend: gmt=-8
05-06 15:29 DEBUG  WindowsBackend: country=US
05-06 15:29 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-06 15:29 DEBUG  WindowsBackend: windows_username=Jake
05-06 15:29 DEBUG  WindowsBackend: user_full_name=Jake
05-06 15:29 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jake
05-06 15:29 DEBUG  WindowsBackend: windows_language_code=1033
05-06 15:29 DEBUG  WindowsBackend: windows_language=English
05-06 15:29 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
05-06 15:29 DEBUG  WindowsBackend: bootloader=xp
05-06 15:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77353.7929688 mb free ntfs)
05-06 15:29 DEBUG  WindowsBackend: drive=Drive(C: hd 77353.7929688 mb free ntfs)
05-06 15:29 DEBUG  WindowsBackend: drive=Drive(D: hd 2165.859375 mb free fat32)
05-06 15:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
05-06 15:29 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-06 15:29 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
05-06 15:29 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-06 15:29 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-06 15:29 DEBUG  WindowsBackend: uninstaller_path=None
05-06 15:29 DEBUG  WindowsBackend: previous_target_dir=None
05-06 15:29 DEBUG  WindowsBackend: previous_distro_name=None
05-06 15:29 DEBUG  WindowsBackend: keyboard_id=67699721
05-06 15:29 DEBUG  WindowsBackend: keyboard_layout=us
05-06 15:29 DEBUG  WindowsBackend: keyboard_variant=
05-06 15:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-06 15:29 DEBUG  CommonBackend: locale=en_US.UTF-8
05-06 15:29 DEBUG  WindowsBackend: total_memory_mb=445.05859375
05-06 15:29 DEBUG  CommonBackend: Searching ISOs on USB devices
05-06 15:29 DEBUG  CommonBackend: Searching for local CDs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Ubuntu Netbook CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 15:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:29 INFO   root: Running the installer...
05-06 15:29 DEBUG  WindowsFrontend: __init__...
05-06 15:29 DEBUG  WindowsFrontend: on_init...
05-06 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\translations, languages=['en_US', 'en']
05-06 15:29 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\translations, languages=['en_US', 'en']
05-06 15:34 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jake
05-06 15:34 INFO   root: Received settings
05-06 15:34 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\translations, languages=['en_US', 'en']
05-06 15:34 DEBUG  TaskList: # Running tasklist...
05-06 15:34 DEBUG  TaskList: ## Running select_target_dir...
05-06 15:34 INFO   WindowsBackend: Installing into C:\ubuntu
05-06 15:34 DEBUG  TaskList: ## Finished select_target_dir
05-06 15:34 DEBUG  TaskList: ## Running create_dir_structure...
05-06 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-06 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-06 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-06 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-06 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-06 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-06 15:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-06 15:34 DEBUG  TaskList: ## Finished create_dir_structure
05-06 15:34 DEBUG  TaskList: ## Running uncompress_target_dir...
05-06 15:34 DEBUG  TaskList: ## Finished uncompress_target_dir
05-06 15:34 DEBUG  TaskList: ## Running create_uninstaller...
05-06 15:34 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-06 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-06 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-06 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-06 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-06 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-06 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-06 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-06 15:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-06 15:34 DEBUG  TaskList: ## Finished create_uninstaller
05-06 15:34 DEBUG  TaskList: ## Running copy_installation_files...
05-06 15:34 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-06 15:34 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\winboot -> C:\ubuntu\winboot
05-06 15:34 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-06 15:34 DEBUG  TaskList: ## Finished copy_installation_files
05-06 15:34 DEBUG  TaskList: ## Running get_iso...
05-06 15:34 DEBUG  CommonBackend: Searching for local CD
05-06 15:34 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp is a valid Ubuntu CD
05-06 15:34 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\casper\filesystem.squashfs
05-06 15:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 15:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 15:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 15:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 15:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 15:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 15:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 15:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 15:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 15:34 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 15:34 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 15:34 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 15:34 DEBUG  CommonBackend: Searching for local ISO
05-06 15:34 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Jake\My Documents\Downloads\ubuntu-10.10-desktop-i386.iso
05-06 15:34 DEBUG  Distro:     wrong size: 0 < 600000000
05-06 15:34 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-06 15:34 DEBUG  TaskList: New task get_metalink
05-06 15:34 DEBUG  TaskList: ### Running get_metalink...
05-06 15:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-06 15:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-06 15:34 DEBUG  downloader: download finished (read 28363 bytes)
05-06 15:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-06 15:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-06 15:34 DEBUG  downloader: download finished (read 874 bytes)
05-06 15:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-06 15:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-06 15:34 DEBUG  downloader: download finished (read 198 bytes)
05-06 15:34 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-06 15:34 INFO   saplog: Checking block bindings..
05-06 15:34 INFO   saplog: Key verified successfully.
05-06 15:34 DEBUG  CommonBackend: metalink md5sums:
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

05-06 15:34 DEBUG  TaskList: ### Finished get_metalink
05-06 15:34 DEBUG  TaskList: New task download
05-06 15:34 DEBUG  TaskList: ### Running download...
05-06 15:34 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:48 DEBUG  TaskList: ### Finished download
05-06 16:48 DEBUG  TaskList: New task check_iso
05-06 16:48 DEBUG  TaskList: ### Running check_iso...
05-06 16:48 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:48 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:48 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:48 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
05-06 16:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
05-06 16:48 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:48 DEBUG  TaskList: New task get_file_md5
05-06 16:48 DEBUG  TaskList: #### Running get_file_md5...
05-06 16:49 DEBUG  TaskList: #### Finished get_file_md5
05-06 16:49 DEBUG  TaskList: ### Finished check_iso
05-06 16:49 DEBUG  TaskList: ## Finished get_iso
05-06 16:49 DEBUG  TaskList: ## Running extract_kernel...
05-06 16:49 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:49 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:49 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:49 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 16:49 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-06 16:49 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
05-06 16:49 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
05-06 16:49 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
05-06 16:49 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
05-06 16:49 DEBUG  TaskList: ## Finished extract_kernel
05-06 16:49 DEBUG  TaskList: ## Running choose_disk_sizes...
05-06 16:49 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
05-06 16:49 DEBUG  TaskList: ## Finished choose_disk_sizes
05-06 16:49 DEBUG  TaskList: ## Running create_preseed...
05-06 16:49 DEBUG  TaskList: ## Finished create_preseed
05-06 16:49 DEBUG  TaskList: ## Running modify_bootloader...
05-06 16:49 DEBUG  TaskList: New task modify_bootini
05-06 16:49 DEBUG  TaskList: ### Running modify_bootini...
05-06 16:49 DEBUG  WindowsBackend: modify_bootini C:
05-06 16:49 DEBUG  TaskList: ### Finished modify_bootini
05-06 16:49 DEBUG  TaskList: New task modify_bootini
05-06 16:49 DEBUG  TaskList: ### Running modify_bootini...
05-06 16:49 DEBUG  WindowsBackend: modify_bootini D:
05-06 16:49 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
05-06 16:49 DEBUG  TaskList: ### Finished modify_bootini
05-06 16:49 DEBUG  TaskList: New task modify_bootini
05-06 16:49 DEBUG  TaskList: ### Running modify_bootini...
05-06 16:49 DEBUG  WindowsBackend: modify_bootini F:
05-06 16:49 DEBUG  WindowsBackend: Could not find boot.ini F:\boot.ini
05-06 16:49 DEBUG  TaskList: ### Finished modify_bootini
05-06 16:49 DEBUG  TaskList: New task modify_bootini
05-06 16:49 DEBUG  TaskList: ### Running modify_bootini...
05-06 16:49 DEBUG  WindowsBackend: modify_bootini G:
05-06 16:49 DEBUG  WindowsBackend: Could not find boot.ini G:\boot.ini
05-06 16:49 DEBUG  TaskList: ### Finished modify_bootini
05-06 16:49 DEBUG  TaskList: New task modify_bootini
05-06 16:49 DEBUG  TaskList: ### Running modify_bootini...
05-06 16:49 DEBUG  WindowsBackend: modify_bootini H:
05-06 16:49 DEBUG  WindowsBackend: Could not find boot.ini H:\boot.ini
05-06 16:49 DEBUG  TaskList: ### Finished modify_bootini
05-06 16:49 DEBUG  TaskList: New task modify_bootini
05-06 16:49 DEBUG  TaskList: ### Running modify_bootini...
05-06 16:49 DEBUG  WindowsBackend: modify_bootini I:
05-06 16:49 DEBUG  WindowsBackend: Could not find boot.ini I:\boot.ini
05-06 16:49 DEBUG  TaskList: ### Finished modify_bootini
05-06 16:49 DEBUG  TaskList: ## Finished modify_bootloader
05-06 16:49 DEBUG  TaskList: ## Running modify_grub_configuration...
05-06 16:49 DEBUG  TaskList: ## Finished modify_grub_configuration
05-06 16:49 DEBUG  TaskList: ## Running create_virtual_disks...
05-06 16:49 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
05-06 16:49 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
05-06 16:49 DEBUG  TaskList: ## Finished create_virtual_disks
05-06 16:49 DEBUG  TaskList: ## Running uncompress_files...
05-06 16:49 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
05-06 16:49 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
05-06 16:49 DEBUG  TaskList: ## Finished uncompress_files
05-06 16:49 DEBUG  TaskList: ## Running eject_cd...
05-06 16:49 DEBUG  TaskList: ## Finished eject_cd
05-06 16:49 DEBUG  TaskList: # Finished tasklist
05-06 16:49 INFO   root: Almost finished installing
05-06 16:49 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl22A.tmp\translations, languages=['en_US', 'en']
05-06 17:08 INFO   root: Finished installation
05-06 17:08 INFO   root: Rebooting
05-06 17:08 DEBUG  TaskList: # Running tasklist...
05-06 17:08 DEBUG  TaskList: ## Running reboot...
05-06 17:08 DEBUG  TaskList: ## Finished reboot
05-06 17:08 DEBUG  TaskList: # Finished tasklist
05-06 17:08 DEBUG  root: application.quit
05-06 17:08 DEBUG  WindowsFrontend: frontend.quit
05-06 17:08 DEBUG  WindowsFrontend: frontend.on_quit
05-06 17:08 DEBUG  root: application.on_quit
05-06 17:08 INFO   root: sys.exit
05-06 18:13 INFO   root: === wubi 11.04 rev211 ===
05-06 18:13 DEBUG  root: Logfile is c:\docume~1\jake\locals~1\temp\wubi-11.04-rev211.log
05-06 18:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jake\\My Documents\\Downloads\\wubi.exe"']
05-06 18:13 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\data
05-06 18:13 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\bin\7z.exe
05-06 18:13 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
05-06 18:13 DEBUG  CommonBackend: Fetching basic info...
05-06 18:13 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe
05-06 18:13 DEBUG  CommonBackend: platform=win32
05-06 18:13 DEBUG  CommonBackend: osname=nt
05-06 18:13 DEBUG  CommonBackend: language=en_US
05-06 18:13 DEBUG  CommonBackend: encoding=cp1252
05-06 18:13 DEBUG  WindowsBackend: arch=amd64
05-06 18:13 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\data\isolist.ini
05-06 18:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-06 18:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-06 18:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-06 18:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-06 18:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-06 18:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-06 18:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-06 18:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-06 18:13 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-06 18:13 DEBUG  WindowsBackend: Fetching host info...
05-06 18:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-06 18:13 DEBUG  WindowsBackend: windows version=xp
05-06 18:13 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-06 18:13 DEBUG  WindowsBackend: windows_sp=Service Pack 3
05-06 18:13 DEBUG  WindowsBackend: windows_build=2600
05-06 18:13 DEBUG  WindowsBackend: gmt=-8
05-06 18:13 DEBUG  WindowsBackend: country=US
05-06 18:13 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-06 18:13 DEBUG  WindowsBackend: windows_username=Jake
05-06 18:13 DEBUG  WindowsBackend: user_full_name=Jake
05-06 18:13 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jake
05-06 18:13 DEBUG  WindowsBackend: windows_language_code=1033
05-06 18:13 DEBUG  WindowsBackend: windows_language=English
05-06 18:13 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
05-06 18:13 DEBUG  WindowsBackend: bootloader=xp
05-06 18:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 59575.328125 mb free ntfs)
05-06 18:13 DEBUG  WindowsBackend: drive=Drive(C: hd 59575.328125 mb free ntfs)
05-06 18:13 DEBUG  WindowsBackend: drive=Drive(D: hd 2165.859375 mb free fat32)
05-06 18:13 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
05-06 18:13 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-06 18:13 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
05-06 18:13 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-06 18:13 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-06 18:13 DEBUG  WindowsBackend: drive=Drive(J: removable 291.5 mb free fat32)
05-06 18:13 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-06 18:13 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-06 18:13 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-06 18:13 DEBUG  WindowsBackend: keyboard_id=67699721
05-06 18:13 DEBUG  WindowsBackend: keyboard_layout=us
05-06 18:13 DEBUG  WindowsBackend: keyboard_variant=
05-06 18:13 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-06 18:13 DEBUG  CommonBackend: locale=en_US.UTF-8
05-06 18:13 DEBUG  WindowsBackend: total_memory_mb=445.05859375
05-06 18:13 DEBUG  CommonBackend: Searching ISOs on USB devices
05-06 18:13 DEBUG  CommonBackend: Searching for local CDs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu Netbook CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 18:13 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:13 INFO   root: Already installed, running the uninstaller...
05-06 18:13 INFO   root: Running the uninstaller...
05-06 18:13 INFO   CommonBackend: This is the uninstaller running
05-06 18:13 DEBUG  WindowsFrontend: __init__...
05-06 18:13 DEBUG  WindowsFrontend: on_init...
05-06 18:13 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
05-06 18:58 INFO   root: Received settings
05-06 18:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
05-06 18:58 DEBUG  TaskList: # Running tasklist...
05-06 18:58 DEBUG  TaskList: ## Running Backup ISO...
05-06 18:58 DEBUG  TaskList: ## Finished Backup ISO
05-06 18:58 DEBUG  TaskList: ## Running Remove bootloader entry...
05-06 18:58 ERROR  WindowsBackend: Cannot find bcdedit
05-06 18:58 DEBUG  WindowsBackend: undo_bootini C:
05-06 18:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 59575.328125 mb free ntfs)
05-06 18:58 DEBUG  WindowsBackend: undo_bootini D:
05-06 18:58 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2165.859375 mb free fat32)
05-06 18:58 DEBUG  WindowsBackend: undo_bootini F:
05-06 18:58 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
05-06 18:58 DEBUG  WindowsBackend: undo_bootini G:
05-06 18:58 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
05-06 18:58 DEBUG  WindowsBackend: undo_bootini H:
05-06 18:58 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
05-06 18:58 DEBUG  WindowsBackend: undo_bootini I:
05-06 18:58 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
05-06 18:58 DEBUG  WindowsBackend: undo_bootini J:
05-06 18:58 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 291.5 mb free fat32)
05-06 18:58 DEBUG  TaskList: ## Finished Remove bootloader entry
05-06 18:58 DEBUG  TaskList: ## Running Remove target dir...
05-06 18:58 DEBUG  CommonBackend: Deleting C:\ubuntu
05-06 18:58 DEBUG  TaskList: ## Finished Remove target dir
05-06 18:58 DEBUG  TaskList: ## Running Remove registry key...
05-06 18:58 DEBUG  TaskList: ## Finished Remove registry key
05-06 18:58 DEBUG  TaskList: # Finished tasklist
05-06 18:58 INFO   root: Almost finished uninstalling
05-06 18:58 INFO   root: Finished uninstallation
05-06 18:58 DEBUG  CommonBackend: Fetching basic info...
05-06 18:58 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe
05-06 18:58 DEBUG  CommonBackend: platform=win32
05-06 18:58 DEBUG  CommonBackend: osname=nt
05-06 18:58 DEBUG  WindowsBackend: arch=amd64
05-06 18:58 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\data\isolist.ini
05-06 18:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-06 18:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-06 18:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-06 18:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-06 18:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-06 18:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-06 18:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-06 18:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-06 18:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-06 18:58 DEBUG  WindowsBackend: Fetching host info...
05-06 18:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-06 18:58 DEBUG  WindowsBackend: windows version=xp
05-06 18:58 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-06 18:58 DEBUG  WindowsBackend: windows_sp=Service Pack 3
05-06 18:58 DEBUG  WindowsBackend: windows_build=2600
05-06 18:58 DEBUG  WindowsBackend: gmt=-8
05-06 18:58 DEBUG  WindowsBackend: country=US
05-06 18:58 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-06 18:58 DEBUG  WindowsBackend: windows_username=Jake
05-06 18:58 DEBUG  WindowsBackend: user_full_name=Jake
05-06 18:58 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jake
05-06 18:58 DEBUG  WindowsBackend: windows_language_code=1033
05-06 18:58 DEBUG  WindowsBackend: windows_language=English
05-06 18:58 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
05-06 18:58 DEBUG  WindowsBackend: bootloader=xp
05-06 18:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77291.2304688 mb free ntfs)
05-06 18:58 DEBUG  WindowsBackend: drive=Drive(C: hd 77291.2304688 mb free ntfs)
05-06 18:58 DEBUG  WindowsBackend: drive=Drive(D: hd 2165.859375 mb free fat32)
05-06 18:58 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
05-06 18:58 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-06 18:58 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
05-06 18:58 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-06 18:58 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-06 18:58 DEBUG  WindowsBackend: drive=Drive(J: removable 291.5 mb free fat32)
05-06 18:58 DEBUG  WindowsBackend: uninstaller_path=None
05-06 18:58 DEBUG  WindowsBackend: previous_target_dir=None
05-06 18:58 DEBUG  WindowsBackend: previous_distro_name=None
05-06 18:58 DEBUG  WindowsBackend: keyboard_id=67699721
05-06 18:58 DEBUG  WindowsBackend: keyboard_layout=us
05-06 18:58 DEBUG  WindowsBackend: keyboard_variant=
05-06 18:58 DEBUG  WindowsBackend: total_memory_mb=445.05859375
05-06 18:58 DEBUG  CommonBackend: Searching ISOs on USB devices
05-06 18:58 DEBUG  CommonBackend: Searching for local CDs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu Netbook CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 INFO   root: Running the installer...
05-06 18:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
05-06 18:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
05-06 18:58 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jake
05-06 18:58 INFO   root: Received settings
05-06 18:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\translations, languages=['en_US', 'en']
05-06 18:58 DEBUG  TaskList: # Running tasklist...
05-06 18:58 DEBUG  TaskList: ## Running select_target_dir...
05-06 18:58 INFO   WindowsBackend: Installing into C:\ubuntu
05-06 18:58 DEBUG  TaskList: ## Finished select_target_dir
05-06 18:58 DEBUG  TaskList: ## Running create_dir_structure...
05-06 18:58 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-06 18:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-06 18:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-06 18:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-06 18:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-06 18:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-06 18:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-06 18:58 DEBUG  TaskList: ## Finished create_dir_structure
05-06 18:58 DEBUG  TaskList: ## Running uncompress_target_dir...
05-06 18:58 DEBUG  TaskList: ## Finished uncompress_target_dir
05-06 18:58 DEBUG  TaskList: ## Running create_uninstaller...
05-06 18:58 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-06 18:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-06 18:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-06 18:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-06 18:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-06 18:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-06 18:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-06 18:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-06 18:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-06 18:58 DEBUG  TaskList: ## Finished create_uninstaller
05-06 18:58 DEBUG  TaskList: ## Running copy_installation_files...
05-06 18:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-06 18:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\winboot -> C:\ubuntu\winboot
05-06 18:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-06 18:58 DEBUG  TaskList: ## Finished copy_installation_files
05-06 18:58 DEBUG  TaskList: ## Running get_iso...
05-06 18:58 DEBUG  CommonBackend: Searching for local CD
05-06 18:58 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl2B.tmp\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:58 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 18:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:58 DEBUG  CommonBackend: Searching for local ISO
05-06 18:58 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Jake\My Documents\Downloads\ubuntu-10.10-desktop-i386.iso
05-06 18:58 DEBUG  Distro:     wrong size: 0 < 600000000
05-06 18:58 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-06 18:58 DEBUG  TaskList: New task get_metalink
05-06 18:58 DEBUG  TaskList: ### Running get_metalink...
05-06 18:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-06 18:58 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-06 18:58 DEBUG  downloader: download finished (read 28363 bytes)
05-06 18:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-06 18:58 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-06 18:58 DEBUG  downloader: download finished (read 874 bytes)
05-06 18:58 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-06 18:58 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-06 18:58 DEBUG  downloader: download finished (read 198 bytes)
05-06 18:58 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-06 18:58 INFO   saplog: Checking block bindings..
05-06 18:58 INFO   saplog: Key verified successfully.
05-06 18:58 DEBUG  CommonBackend: metalink md5sums:
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

05-06 18:58 DEBUG  TaskList: ### Finished get_metalink
05-06 18:58 DEBUG  TaskList: New task download
05-06 18:58 DEBUG  TaskList: ### Running download...
05-06 18:58 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 18:59 INFO   root: === wubi 11.04 rev211 ===
05-06 18:59 DEBUG  root: Logfile is c:\docume~1\jake\locals~1\temp\wubi-11.04-rev211.log
05-06 18:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jake\\My Documents\\Downloads\\wubi.exe"']
05-06 18:59 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\data
05-06 18:59 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\bin\7z.exe
05-06 18:59 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
05-06 18:59 DEBUG  CommonBackend: Fetching basic info...
05-06 18:59 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe
05-06 18:59 DEBUG  CommonBackend: platform=win32
05-06 18:59 DEBUG  CommonBackend: osname=nt
05-06 18:59 DEBUG  CommonBackend: language=en_US
05-06 18:59 DEBUG  CommonBackend: encoding=cp1252
05-06 18:59 DEBUG  WindowsBackend: arch=amd64
05-06 18:59 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\data\isolist.ini
05-06 18:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-06 18:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-06 18:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-06 18:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-06 18:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-06 18:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-06 18:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-06 18:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-06 18:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-06 18:59 DEBUG  WindowsBackend: Fetching host info...
05-06 18:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-06 18:59 DEBUG  WindowsBackend: windows version=xp
05-06 18:59 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-06 18:59 DEBUG  WindowsBackend: windows_sp=Service Pack 3
05-06 18:59 DEBUG  WindowsBackend: windows_build=2600
05-06 18:59 DEBUG  WindowsBackend: gmt=-8
05-06 18:59 DEBUG  WindowsBackend: country=US
05-06 18:59 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-06 18:59 DEBUG  WindowsBackend: windows_username=Jake
05-06 18:59 DEBUG  WindowsBackend: user_full_name=Jake
05-06 18:59 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jake
05-06 18:59 DEBUG  WindowsBackend: windows_language_code=1033
05-06 18:59 DEBUG  WindowsBackend: windows_language=English
05-06 18:59 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
05-06 18:59 DEBUG  WindowsBackend: bootloader=xp
05-06 18:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77281.9921875 mb free ntfs)
05-06 18:59 DEBUG  WindowsBackend: drive=Drive(C: hd 77281.9921875 mb free ntfs)
05-06 18:59 DEBUG  WindowsBackend: drive=Drive(D: hd 2165.859375 mb free fat32)
05-06 18:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
05-06 18:59 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-06 18:59 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
05-06 18:59 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-06 18:59 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-06 18:59 DEBUG  WindowsBackend: drive=Drive(J: removable 291.5 mb free fat32)
05-06 18:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-06 18:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-06 18:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-06 18:59 DEBUG  WindowsBackend: keyboard_id=67699721
05-06 18:59 DEBUG  WindowsBackend: keyboard_layout=us
05-06 18:59 DEBUG  WindowsBackend: keyboard_variant=
05-06 18:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-06 18:59 DEBUG  CommonBackend: locale=en_US.UTF-8
05-06 18:59 DEBUG  WindowsBackend: total_memory_mb=445.05859375
05-06 18:59 DEBUG  CommonBackend: Searching ISOs on USB devices
05-06 18:59 DEBUG  CommonBackend: Searching for local CDs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Ubuntu Netbook CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 18:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 18:59 INFO   root: Already installed, running the uninstaller...
05-06 18:59 INFO   root: Running the uninstaller...
05-06 18:59 INFO   CommonBackend: This is the uninstaller running
05-06 18:59 DEBUG  WindowsFrontend: __init__...
05-06 18:59 DEBUG  WindowsFrontend: on_init...
05-06 18:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\translations, languages=['en_US', 'en']
05-06 18:59 INFO   root: Received settings
05-06 18:59 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl3F.tmp\translations, languages=['en_US', 'en']
05-06 18:59 DEBUG  TaskList: # Running tasklist...
05-06 18:59 DEBUG  TaskList: ## Running Backup ISO...
05-06 18:59 DEBUG  TaskList: ## Finished Backup ISO
05-06 18:59 DEBUG  TaskList: ## Running Remove bootloader entry...
05-06 18:59 ERROR  WindowsBackend: Cannot find bcdedit
05-06 18:59 DEBUG  WindowsBackend: undo_bootini C:
05-06 18:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 77281.9921875 mb free ntfs)
05-06 18:59 DEBUG  WindowsBackend: undo_bootini D:
05-06 18:59 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2165.859375 mb free fat32)
05-06 18:59 DEBUG  WindowsBackend: undo_bootini F:
05-06 18:59 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
05-06 18:59 DEBUG  WindowsBackend: undo_bootini G:
05-06 18:59 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
05-06 18:59 DEBUG  WindowsBackend: undo_bootini H:
05-06 18:59 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
05-06 18:59 DEBUG  WindowsBackend: undo_bootini I:
05-06 18:59 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
05-06 18:59 DEBUG  WindowsBackend: undo_bootini J:
05-06 18:59 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 291.5 mb free fat32)
05-06 18:59 DEBUG  TaskList: ## Finished Remove bootloader entry
05-06 18:59 DEBUG  TaskList: ## Running Remove target dir...
05-06 18:59 DEBUG  CommonBackend: Deleting C:\ubuntu
05-06 18:59 ERROR  TaskList: [Errno 13] Permission denied removing C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 18:59 DEBUG  TaskList: # Cancelling tasklist
05-06 18:59 DEBUG  TaskList: # Finished tasklist
05-06 18:59 ERROR  root: [Errno 13] Permission denied removing C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 13] Permission denied removing C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 18:59 INFO   WindowsFrontend: Operation cancelled
05-06 18:59 DEBUG  WindowsFrontend: frontend.quit
05-06 18:59 DEBUG  WindowsFrontend: frontend.on_quit
05-06 18:59 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
05-06 18:59 DEBUG  TaskList: # Cancelling tasklist
05-06 18:59 DEBUG  TaskList: ### Finished download
05-06 18:59 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
05-06 18:59 DEBUG  root: application.on_quit
05-06 18:59 DEBUG  root: Forceful exit
05-06 18:59 INFO   root: sys.exit
05-06 19:00 INFO   root: === wubi 11.04 rev211 ===
05-06 19:00 DEBUG  root: Logfile is c:\docume~1\jake\locals~1\temp\wubi-11.04-rev211.log
05-06 19:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jake\\My Documents\\Downloads\\wubi.exe"']
05-06 19:00 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\data
05-06 19:00 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\bin\7z.exe
05-06 19:00 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
05-06 19:00 DEBUG  CommonBackend: Fetching basic info...
05-06 19:00 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe
05-06 19:00 DEBUG  CommonBackend: platform=win32
05-06 19:00 DEBUG  CommonBackend: osname=nt
05-06 19:00 DEBUG  CommonBackend: language=en_US
05-06 19:00 DEBUG  CommonBackend: encoding=cp1252
05-06 19:00 DEBUG  WindowsBackend: arch=amd64
05-06 19:00 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\data\isolist.ini
05-06 19:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-06 19:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-06 19:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-06 19:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-06 19:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-06 19:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-06 19:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-06 19:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-06 19:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-06 19:00 DEBUG  WindowsBackend: Fetching host info...
05-06 19:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-06 19:00 DEBUG  WindowsBackend: windows version=xp
05-06 19:00 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-06 19:00 DEBUG  WindowsBackend: windows_sp=Service Pack 3
05-06 19:00 DEBUG  WindowsBackend: windows_build=2600
05-06 19:00 DEBUG  WindowsBackend: gmt=-8
05-06 19:00 DEBUG  WindowsBackend: country=US
05-06 19:00 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-06 19:00 DEBUG  WindowsBackend: windows_username=Jake
05-06 19:00 DEBUG  WindowsBackend: user_full_name=Jake
05-06 19:00 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jake
05-06 19:00 DEBUG  WindowsBackend: windows_language_code=1033
05-06 19:00 DEBUG  WindowsBackend: windows_language=English
05-06 19:00 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
05-06 19:00 DEBUG  WindowsBackend: bootloader=xp
05-06 19:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77288.3125 mb free ntfs)
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(C: hd 77288.3125 mb free ntfs)
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(D: hd 2165.859375 mb free fat32)
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(J: removable 291.5 mb free fat32)
05-06 19:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-06 19:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-06 19:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-06 19:00 DEBUG  WindowsBackend: keyboard_id=67699721
05-06 19:00 DEBUG  WindowsBackend: keyboard_layout=us
05-06 19:00 DEBUG  WindowsBackend: keyboard_variant=
05-06 19:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-06 19:00 DEBUG  CommonBackend: locale=en_US.UTF-8
05-06 19:00 DEBUG  WindowsBackend: total_memory_mb=445.05859375
05-06 19:00 DEBUG  CommonBackend: Searching ISOs on USB devices
05-06 19:00 DEBUG  CommonBackend: Searching for local CDs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 INFO   root: Already installed, running the uninstaller...
05-06 19:00 INFO   root: Running the uninstaller...
05-06 19:00 INFO   CommonBackend: This is the uninstaller running
05-06 19:00 DEBUG  WindowsFrontend: __init__...
05-06 19:00 DEBUG  WindowsFrontend: on_init...
05-06 19:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
05-06 19:00 INFO   root: Received settings
05-06 19:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
05-06 19:00 DEBUG  TaskList: # Running tasklist...
05-06 19:00 DEBUG  TaskList: ## Running Backup ISO...
05-06 19:00 DEBUG  TaskList: ## Finished Backup ISO
05-06 19:00 DEBUG  TaskList: ## Running Remove bootloader entry...
05-06 19:00 ERROR  WindowsBackend: Cannot find bcdedit
05-06 19:00 DEBUG  WindowsBackend: undo_bootini C:
05-06 19:00 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 77288.3125 mb free ntfs)
05-06 19:00 DEBUG  WindowsBackend: undo_bootini D:
05-06 19:00 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2165.859375 mb free fat32)
05-06 19:00 DEBUG  WindowsBackend: undo_bootini F:
05-06 19:00 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: undo_bootini G:
05-06 19:00 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: undo_bootini H:
05-06 19:00 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: undo_bootini I:
05-06 19:00 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: undo_bootini J:
05-06 19:00 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 291.5 mb free fat32)
05-06 19:00 DEBUG  TaskList: ## Finished Remove bootloader entry
05-06 19:00 DEBUG  TaskList: ## Running Remove target dir...
05-06 19:00 DEBUG  CommonBackend: Deleting C:\ubuntu
05-06 19:00 DEBUG  TaskList: ## Finished Remove target dir
05-06 19:00 DEBUG  TaskList: ## Running Remove registry key...
05-06 19:00 DEBUG  TaskList: ## Finished Remove registry key
05-06 19:00 DEBUG  TaskList: # Finished tasklist
05-06 19:00 INFO   root: Almost finished uninstalling
05-06 19:00 INFO   root: Finished uninstallation
05-06 19:00 DEBUG  CommonBackend: Fetching basic info...
05-06 19:00 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe
05-06 19:00 DEBUG  CommonBackend: platform=win32
05-06 19:00 DEBUG  CommonBackend: osname=nt
05-06 19:00 DEBUG  WindowsBackend: arch=amd64
05-06 19:00 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\data\isolist.ini
05-06 19:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-06 19:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-06 19:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-06 19:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-06 19:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-06 19:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-06 19:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-06 19:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-06 19:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-06 19:00 DEBUG  WindowsBackend: Fetching host info...
05-06 19:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-06 19:00 DEBUG  WindowsBackend: windows version=xp
05-06 19:00 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-06 19:00 DEBUG  WindowsBackend: windows_sp=Service Pack 3
05-06 19:00 DEBUG  WindowsBackend: windows_build=2600
05-06 19:00 DEBUG  WindowsBackend: gmt=-8
05-06 19:00 DEBUG  WindowsBackend: country=US
05-06 19:00 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-06 19:00 DEBUG  WindowsBackend: windows_username=Jake
05-06 19:00 DEBUG  WindowsBackend: user_full_name=Jake
05-06 19:00 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jake
05-06 19:00 DEBUG  WindowsBackend: windows_language_code=1033
05-06 19:00 DEBUG  WindowsBackend: windows_language=English
05-06 19:00 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 3.00GHz
05-06 19:00 DEBUG  WindowsBackend: bootloader=xp
05-06 19:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 77290.3789063 mb free ntfs)
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(C: hd 77290.3789063 mb free ntfs)
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(D: hd 2165.859375 mb free fat32)
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
05-06 19:00 DEBUG  WindowsBackend: drive=Drive(J: removable 291.5 mb free fat32)
05-06 19:00 DEBUG  WindowsBackend: uninstaller_path=None
05-06 19:00 DEBUG  WindowsBackend: previous_target_dir=None
05-06 19:00 DEBUG  WindowsBackend: previous_distro_name=None
05-06 19:00 DEBUG  WindowsBackend: keyboard_id=67699721
05-06 19:00 DEBUG  WindowsBackend: keyboard_layout=us
05-06 19:00 DEBUG  WindowsBackend: keyboard_variant=
05-06 19:00 DEBUG  WindowsBackend: total_memory_mb=445.05859375
05-06 19:00 DEBUG  CommonBackend: Searching ISOs on USB devices
05-06 19:00 DEBUG  CommonBackend: Searching for local CDs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 INFO   root: Running the installer...
05-06 19:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
05-06 19:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
05-06 19:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jake
05-06 19:00 INFO   root: Received settings
05-06 19:00 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\translations, languages=['en_US', 'en']
05-06 19:00 DEBUG  TaskList: # Running tasklist...
05-06 19:00 DEBUG  TaskList: ## Running select_target_dir...
05-06 19:00 INFO   WindowsBackend: Installing into C:\ubuntu
05-06 19:00 DEBUG  TaskList: ## Finished select_target_dir
05-06 19:00 DEBUG  TaskList: ## Running create_dir_structure...
05-06 19:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-06 19:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-06 19:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-06 19:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-06 19:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-06 19:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-06 19:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-06 19:00 DEBUG  TaskList: ## Finished create_dir_structure
05-06 19:00 DEBUG  TaskList: ## Running uncompress_target_dir...
05-06 19:00 DEBUG  TaskList: ## Finished uncompress_target_dir
05-06 19:00 DEBUG  TaskList: ## Running create_uninstaller...
05-06 19:00 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Jake\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-06 19:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-06 19:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-06 19:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-06 19:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-06 19:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-06 19:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-06 19:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-06 19:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-06 19:00 DEBUG  TaskList: ## Finished create_uninstaller
05-06 19:00 DEBUG  TaskList: ## Running copy_installation_files...
05-06 19:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-06 19:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\winboot -> C:\ubuntu\winboot
05-06 19:00 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-06 19:00 DEBUG  TaskList: ## Finished copy_installation_files
05-06 19:00 DEBUG  TaskList: ## Running get_iso...
05-06 19:00 DEBUG  CommonBackend: Searching for local CD
05-06 19:00 DEBUG  Distro:   checking whether C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain C:\DOCUME~1\Jake\LOCALS~1\Temp\pyl40.tmp\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-06 19:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-06 19:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-06 19:00 DEBUG  CommonBackend: Searching for local ISO
05-06 19:00 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\Jake\My Documents\Downloads\ubuntu-10.10-desktop-i386.iso
05-06 19:00 DEBUG  Distro:     wrong size: 0 < 600000000
05-06 19:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-06 19:00 DEBUG  TaskList: New task get_metalink
05-06 19:00 DEBUG  TaskList: ### Running get_metalink...
05-06 19:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-06 19:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-06 19:00 DEBUG  downloader: download finished (read 28363 bytes)
05-06 19:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-06 19:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-06 19:00 DEBUG  downloader: download finished (read 874 bytes)
05-06 19:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-06 19:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-06 19:00 DEBUG  downloader: download finished (read 198 bytes)
05-06 19:00 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-06 19:00 INFO   saplog: Checking block bindings..
05-06 19:00 INFO   saplog: Key verified successfully.
05-06 19:00 DEBUG  CommonBackend: metalink md5sums:
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

05-06 19:00 DEBUG  TaskList: ### Finished get_metalink
05-06 19:00 DEBUG  TaskList: New task download
05-06 19:00 DEBUG  TaskList: ### Running download...
05-06 19:00 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-06 20:05 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-06 20:06 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-06 20:06 DEBUG  TaskList: ### Finished download
05-06 20:06 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
05-06 20:06 DEBUG  TaskList: # Cancelling tasklist
05-06 20:06 DEBUG  TaskList: # Finished tasklist
05-06 20:06 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'

---

### Post by bcbc on 2011-05-07
It looks like the first time you ran it, the install completed successfully. What happened after you rebooted?
Then you ran it again , and it uninstalled and tried to install again - it looks like you canceled during the download. At some point there must have been some corruption/permission problem because it couldn't delete the files in c:\ubuntu while trying to uninstall.
Then you had some problems connecting to download a new iso.

I think - if you are having problems where you repeatedly try to install you should probably download the cd iso yourself - you can save it in the same folder as wubi.exe and it will use it - instead of letting wubi download it each time.

But before you try installing again, run chkdsk to make sure any corrupted files are removed. ( go to Computer, right click on drive C:, Properties, Tools, Check disk for errors, fix automatically, Reboot to complete)

---

### Post by Smidthmador on 2011-05-07
Where do I download the CD Iso and how do I implement it?  I have no folder with a wubi.exe file in it... I checked and did a search.  All that it brought up  was the installer.

Would it be easier to just delete all the files and try to re-reinstall?

Thanks for all ur help man!

---

### Post by bcbc on 2011-05-07
Wubi.exe is in your downloads folder:
> 05-06 15:29 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jake\\My Documents\\Downloads\\wubi.exe"']

Download the ISO from here: [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

For 64 bit use ubuntu-11.04-desktop-amd64.iso
For 32 bit use ubuntu-11.04-desktop-i386.iso

It's probably quicker to use a bittorrent client if you have one. Save it to your downloads folder and then run wubi.exe from there.

---

### Post by Smidthmador on 2011-05-07
I feel lame for asking, but how do I check how many bits my system uses?

I uninstalled wubi and thought that it might be a good idea to try to reinstall it after a dskchk, since you said that it was because of a problem with me messin' with ****.  Think that might work?

---

### Post by bcbc on 2011-05-07
> **Smidthmador said:**
> I feel lame for asking, but how do I check how many bits my system uses?

I uninstalled wubi and thought that it might be a good idea to try to reinstall it after a dskchk, since you said that it was because of a problem with me messin' with ****.  Think that might work?

You have a 64 bit machine. You can use either 64bit or 32bit Ubuntu. There's nothing you did that should have caused corruption. If it occurred it's likely a wubi problem.

---

### Post by Smidthmador on 2011-05-07
...If I've uninstalled wubi then I've really messed up, haven't I?

After I install this stuff do I just keep it or put it in the Downloads folder like when you said to put the cd iso in the same folder as the .exe.  Do I just copy n paste into there?

---

### Post by bcbc on 2011-05-07
> **Smidthmador said:**
> ...If I've uninstalled wubi then I've really messed up, haven't I?

After I install this stuff do I just keep it or put it in the Downloads folder like when you said to put the cd iso in the same folder as the .exe.  Do I just copy n paste into there?

Wubi automatically uninstalls if it finds a previous install - even one that didn't fully install. The first time it looks like you did a complete install, from the log. That's why I asked what happened when you rebooted. 

If you don't download it to your Downloads folder, then cut and paste it in there. You can copy it but why have two 700MB images.

---

### Post by Smidthmador on 2011-05-07
You must have not noticed, when I posted my log the first thing I said was that the PC did an auto diskchk and deleted a file called ehRecvr.ba1 in index $I30 of file 8492.  Save for the time that it ran the check it's started up normally.

YAY!  It's not my fault :D

Do I need to reinstall wubi and use it in tandem with the cd iso or can I just soley use the CD?

..Now that I'm sober I find that I am WAY more lost than I thought that I was.  If you felt like giving me explicit directions on what to do and what should be done I would listen and greatly appreciate it!

---

### Post by bcbc on 2011-05-07
Start by having a read of this [https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation)

I'm not going to be online for most of the day... but Wubi installs are usually pretty straightforward. The guide covers most scenarios.

---

