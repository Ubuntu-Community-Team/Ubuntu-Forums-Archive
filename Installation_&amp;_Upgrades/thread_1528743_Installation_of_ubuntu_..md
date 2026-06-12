---
title: "Installation of ubuntu ."
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by mkarthik90 on 2010-07-11
Hi,
    i tried installing ubuntu in my neighbor system. I inserted  the ubuntu disk and gave the option install along with windows   and   proceeded by giving the installation size and the drive where the OS  needs to be installed. Installation started and after few min i got the  error stating that **" Permission Denied " "For more information ,  please see the log file : "** and an path in C:\documen~ was  specified. I tried re installing. First of all it started uninstalling  and started its installation like the same and ended up with the same  problem.

---

### Post by Joe of loath on 2010-07-11
This is wubi, yes? I do think dual booting is less problematic, but there you go.

Are you installing as administrator on the windows box? If it's XP, check to see if the user has administrative rights. If it's Vista/7, right click the installer then click 'run as administrator'.

---

### Post by mkarthik90 on 2010-07-11
HI,
        i am win xp os . can you tell me how to check whether i am an administrator?

---

### Post by wookieshaver on 2010-07-11
You can check for admin rights by doing this: Go to "User Accounts" in control panel (start then control panel and then user accounts) and make sure your account is a member of the "Administrators" group.

---

### Post by mkarthik90 on 2010-07-12
I am in administrator account. SO tell me what will be the problem then??

---

### Post by wookieshaver on 2010-07-12
Since you are an administrator on the XP machine the most likely error wouuld be you are trying to install a 64bit version of Ubuntu inside a 32bit operating system. The "wubi" installer that allows this type of installation for Ubuntu would also be a 64 bit application if the Ubuntu disc you downloaded is the 64 bit version. 
 
So, is your disc the Ubuntu 64 bit version and is your cpu on the machine a 64 bit processor?

---

### Post by bcbc on 2010-07-12
> **mkarthik90 said:**
> Hi,
    i tried installing ubuntu in my neighbor system. I inserted  the ubuntu disk and gave the option install along with windows   and   proceeded by giving the installation size and the drive where the OS  needs to be installed. Installation started and after few min i got the  error stating that **" Permission Denied " "For more information ,  please see the log file : "** and an path in C:\documen~ was  specified. I tried re installing. First of all it started uninstalling  and started its installation like the same and ended up with the same  problem.

Reading the log file helps to narrow down the problem. Open windows explorer and enter %temp% - this will take you to the directory with the log file, then check it out. It's called wubi.log or something similar.

---

### Post by mkarthik90 on 2010-07-13
hi here i have attached the log file. 

06-30 20:11 INFO   root: === wubi 10.04 rev189 ===
06-30 20:11 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data
06-30 20:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
06-30 20:11 DEBUG  CommonBackend: Fetching basic info...
06-30 20:11 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:11 DEBUG  CommonBackend: platform=win32
06-30 20:11 DEBUG  CommonBackend: osname=nt
06-30 20:11 DEBUG  CommonBackend: language=en_US
06-30 20:11 DEBUG  CommonBackend: encoding=cp1252
06-30 20:11 DEBUG  WindowsBackend: arch=amd64
06-30 20:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
06-30 20:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:11 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:11 DEBUG  WindowsBackend: Fetching host info...
06-30 20:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:11 DEBUG  WindowsBackend: windows version=xp
06-30 20:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:11 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:11 DEBUG  WindowsBackend: windows_build=2600
06-30 20:11 DEBUG  WindowsBackend: gmt=-8
06-30 20:11 DEBUG  WindowsBackend: country=US
06-30 20:11 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:11 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:11 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:11 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:11 DEBUG  WindowsBackend: windows_language=English
06-30 20:11 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:11 DEBUG  WindowsBackend: bootloader=xp
06-30 20:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6549.87109375 mb free ntfs)
06-30 20:11 DEBUG  WindowsBackend: drive=Drive(C: hd 6549.87109375 mb free ntfs)
06-30 20:11 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.328125 mb free ntfs)
06-30 20:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:11 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:11 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:11 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:11 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:11 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:11 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:11 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:11 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:11 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:11 DEBUG  CommonBackend: Searching for local CDs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-30 20:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:11 INFO   root: Running the installer...
06-30 20:11 DEBUG  WindowsFrontend: __init__...
06-30 20:11 DEBUG  WindowsFrontend: on_init...
06-30 20:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 20:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 20:18 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=5000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
06-30 20:18 INFO   root: Received settings
06-30 20:18 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 20:18 DEBUG  TaskList: # Running tasklist...
06-30 20:18 DEBUG  TaskList: ## Running select_target_dir...
06-30 20:18 INFO   WindowsBackend: Installing into D:\ubuntu
06-30 20:18 DEBUG  TaskList: ## Finished select_target_dir
06-30 20:18 DEBUG  TaskList: ## Running create_dir_structure...
06-30 20:18 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-30 20:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-30 20:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-30 20:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-30 20:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-30 20:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-30 20:18 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-30 20:18 DEBUG  TaskList: ## Finished create_dir_structure
06-30 20:18 DEBUG  TaskList: ## Running uncompress_target_dir...
06-30 20:18 DEBUG  TaskList: ## Finished uncompress_target_dir
06-30 20:18 DEBUG  TaskList: ## Running create_uninstaller...
06-30 20:18 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-30 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-30 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-30 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-30 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-30 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
06-30 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-30 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-30 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-30 20:18 DEBUG  TaskList: ## Finished create_uninstaller
06-30 20:18 DEBUG  TaskList: ## Running copy_installation_files...
06-30 20:18 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-30 20:18 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\winboot -> D:\ubuntu\winboot
06-30 20:18 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-30 20:18 DEBUG  TaskList: ## Finished copy_installation_files
06-30 20:18 DEBUG  TaskList: ## Running get_iso...
06-30 20:18 DEBUG  CommonBackend: Searching for local CD
06-30 20:18 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 20:18 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:18 DEBUG  CommonBackend: Searching for local ISO
06-30 20:18 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-30 20:18 DEBUG  TaskList: New task get_metalink
06-30 20:18 DEBUG  TaskList: ### Running get_metalink...
06-30 20:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
06-30 20:18 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
06-30 20:18 DEBUG  downloader: download finished (read 7472 bytes)
06-30 20:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
06-30 20:18 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
06-30 20:18 DEBUG  downloader: download finished (read 639 bytes)
06-30 20:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
06-30 20:18 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
06-30 20:18 DEBUG  downloader: download finished (read 189 bytes)
06-30 20:18 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-30 20:18 INFO   saplog: Checking block bindings..
06-30 20:18 INFO   saplog: Key verified successfully.
06-30 20:18 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

06-30 20:18 DEBUG  TaskList: ### Finished get_metalink
06-30 20:18 DEBUG  TaskList: New task download
06-30 20:18 DEBUG  TaskList: ### Running download...
06-30 20:18 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
06-30 20:18 INFO   WindowsFrontend: Operation cancelled
06-30 20:18 DEBUG  WindowsFrontend: frontend.quit
06-30 20:18 DEBUG  WindowsFrontend: frontend.on_quit
06-30 20:18 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
06-30 20:18 DEBUG  TaskList: # Cancelling tasklist
06-30 20:18 DEBUG  TaskList: ### Finished download
06-30 20:18 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
06-30 20:18 DEBUG  root: application.on_quit
06-30 20:18 DEBUG  root: Forceful exit
06-30 20:18 INFO   root: sys.exit
06-30 20:19 INFO   root: === wubi 10.04 rev189 ===
06-30 20:19 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:19 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\data
06-30 20:19 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\bin\7z.exe
06-30 20:19 DEBUG  CommonBackend: Fetching basic info...
06-30 20:19 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:19 DEBUG  CommonBackend: platform=win32
06-30 20:19 DEBUG  CommonBackend: osname=nt
06-30 20:19 DEBUG  CommonBackend: language=en_US
06-30 20:19 DEBUG  CommonBackend: encoding=cp1252
06-30 20:19 DEBUG  WindowsBackend: arch=amd64
06-30 20:19 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
06-30 20:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:19 DEBUG  WindowsBackend: Fetching host info...
06-30 20:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:19 DEBUG  WindowsBackend: windows version=xp
06-30 20:19 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:19 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:19 DEBUG  WindowsBackend: windows_build=2600
06-30 20:19 DEBUG  WindowsBackend: gmt=-8
06-30 20:19 DEBUG  WindowsBackend: country=US
06-30 20:19 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:19 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:19 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:19 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:19 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:19 DEBUG  WindowsBackend: windows_language=English
06-30 20:19 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:19 DEBUG  WindowsBackend: bootloader=xp
06-30 20:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6535.08203125 mb free ntfs)
06-30 20:19 DEBUG  WindowsBackend: drive=Drive(C: hd 6535.08203125 mb free ntfs)
06-30 20:19 DEBUG  WindowsBackend: drive=Drive(D: hd 60152.2890625 mb free ntfs)
06-30 20:19 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:19 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
06-30 20:19 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
06-30 20:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 20:19 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:19 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:19 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:19 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:19 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:19 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:19 DEBUG  CommonBackend: Searching for local CDs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 INFO   root: Already installed, running the uninstaller...
06-30 20:19 INFO   root: Running the uninstaller...
06-30 20:19 INFO   CommonBackend: This is the uninstaller running
06-30 20:19 DEBUG  WindowsFrontend: __init__...
06-30 20:19 DEBUG  WindowsFrontend: on_init...
06-30 20:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
06-30 20:19 INFO   root: Received settings
06-30 20:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
06-30 20:19 DEBUG  TaskList: # Running tasklist...
06-30 20:19 DEBUG  TaskList: ## Running Backup ISO...
06-30 20:19 DEBUG  TaskList: ## Finished Backup ISO
06-30 20:19 DEBUG  TaskList: ## Running Remove bootloader entry...
06-30 20:19 ERROR  WindowsBackend: Cannot find bcdedit
06-30 20:19 DEBUG  WindowsBackend: undo_bootini C:
06-30 20:19 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6535.08203125 mb free ntfs)
06-30 20:19 DEBUG  WindowsBackend: undo_bootini D:
06-30 20:19 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60152.2890625 mb free ntfs)
06-30 20:19 DEBUG  TaskList: ## Finished Remove bootloader entry
06-30 20:19 DEBUG  TaskList: ## Running Remove target dir...
06-30 20:19 DEBUG  CommonBackend: Deleting D:\ubuntu
06-30 20:19 DEBUG  TaskList: ## Finished Remove target dir
06-30 20:19 DEBUG  TaskList: ## Running Remove registry key...
06-30 20:19 DEBUG  TaskList: ## Finished Remove registry key
06-30 20:19 DEBUG  TaskList: # Finished tasklist
06-30 20:19 INFO   root: Almost finished uninstalling
06-30 20:19 INFO   root: Finished uninstallation
06-30 20:19 DEBUG  CommonBackend: Fetching basic info...
06-30 20:19 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:19 DEBUG  CommonBackend: platform=win32
06-30 20:19 DEBUG  CommonBackend: osname=nt
06-30 20:19 DEBUG  WindowsBackend: arch=amd64
06-30 20:19 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\data\isolist.ini
06-30 20:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:19 DEBUG  WindowsBackend: Fetching host info...
06-30 20:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:19 DEBUG  WindowsBackend: windows version=xp
06-30 20:19 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:19 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:19 DEBUG  WindowsBackend: windows_build=2600
06-30 20:19 DEBUG  WindowsBackend: gmt=-8
06-30 20:19 DEBUG  WindowsBackend: country=US
06-30 20:19 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:19 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:19 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:19 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:19 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:19 DEBUG  WindowsBackend: windows_language=English
06-30 20:19 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:19 DEBUG  WindowsBackend: bootloader=xp
06-30 20:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6535.04296875 mb free ntfs)
06-30 20:19 DEBUG  WindowsBackend: drive=Drive(C: hd 6535.04296875 mb free ntfs)
06-30 20:19 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.328125 mb free ntfs)
06-30 20:19 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:19 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:19 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:19 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:19 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:19 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:19 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:19 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:19 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:19 DEBUG  CommonBackend: Searching for local CDs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Kubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 INFO   root: Running the installer...
06-30 20:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
06-30 20:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
06-30 20:19 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
06-30 20:19 INFO   root: Received settings
06-30 20:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\translations, languages=['en_US', 'en']
06-30 20:19 DEBUG  TaskList: # Running tasklist...
06-30 20:19 DEBUG  TaskList: ## Running select_target_dir...
06-30 20:19 INFO   WindowsBackend: Installing into D:\ubuntu
06-30 20:19 DEBUG  TaskList: ## Finished select_target_dir
06-30 20:19 DEBUG  TaskList: ## Running create_dir_structure...
06-30 20:19 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-30 20:19 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-30 20:19 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-30 20:19 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-30 20:19 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-30 20:19 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-30 20:19 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-30 20:19 DEBUG  TaskList: ## Finished create_dir_structure
06-30 20:19 DEBUG  TaskList: ## Running uncompress_target_dir...
06-30 20:19 DEBUG  TaskList: ## Finished uncompress_target_dir
06-30 20:19 DEBUG  TaskList: ## Running create_uninstaller...
06-30 20:19 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-30 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-30 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-30 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-30 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-30 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
06-30 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-30 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-30 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-30 20:19 DEBUG  TaskList: ## Finished create_uninstaller
06-30 20:19 DEBUG  TaskList: ## Running copy_installation_files...
06-30 20:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-30 20:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\winboot -> D:\ubuntu\winboot
06-30 20:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-30 20:19 DEBUG  TaskList: ## Finished copy_installation_files
06-30 20:19 DEBUG  TaskList: ## Running get_iso...
06-30 20:19 DEBUG  CommonBackend: Searching for local CD
06-30 20:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl6.tmp\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:19 DEBUG  CommonBackend: Searching for local ISO
06-30 20:19 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-30 20:19 DEBUG  TaskList: New task get_metalink
06-30 20:19 DEBUG  TaskList: ### Running get_metalink...
06-30 20:19 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
06-30 20:19 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
06-30 20:19 DEBUG  downloader: download finished (read 7472 bytes)
06-30 20:19 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
06-30 20:19 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
06-30 20:19 DEBUG  downloader: download finished (read 639 bytes)
06-30 20:19 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
06-30 20:19 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
06-30 20:19 DEBUG  downloader: download finished (read 189 bytes)
06-30 20:19 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-30 20:19 INFO   saplog: Checking block bindings..
06-30 20:19 INFO   saplog: Key verified successfully.
06-30 20:19 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

06-30 20:19 DEBUG  TaskList: ### Finished get_metalink
06-30 20:19 DEBUG  TaskList: New task download
06-30 20:19 DEBUG  TaskList: ### Running download...
06-30 20:19 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
06-30 20:20 INFO   WindowsFrontend: Operation cancelled
06-30 20:20 DEBUG  WindowsFrontend: frontend.quit
06-30 20:20 DEBUG  WindowsFrontend: frontend.on_quit
06-30 20:20 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
06-30 20:20 DEBUG  TaskList: # Cancelling tasklist
06-30 20:20 DEBUG  TaskList: ### Finished download
06-30 20:20 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
06-30 20:20 DEBUG  root: application.on_quit
06-30 20:20 DEBUG  root: Forceful exit
06-30 20:20 INFO   root: sys.exit
06-30 20:20 INFO   root: === wubi 10.04 rev189 ===
06-30 20:20 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:20 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\data
06-30 20:20 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\bin\7z.exe
06-30 20:20 DEBUG  CommonBackend: Fetching basic info...
06-30 20:20 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:20 DEBUG  CommonBackend: platform=win32
06-30 20:20 DEBUG  CommonBackend: osname=nt
06-30 20:20 DEBUG  CommonBackend: language=en_US
06-30 20:20 DEBUG  CommonBackend: encoding=cp1252
06-30 20:20 DEBUG  WindowsBackend: arch=amd64
06-30 20:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
06-30 20:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:20 DEBUG  WindowsBackend: Fetching host info...
06-30 20:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:20 DEBUG  WindowsBackend: windows version=xp
06-30 20:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:20 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:20 DEBUG  WindowsBackend: windows_build=2600
06-30 20:20 DEBUG  WindowsBackend: gmt=-8
06-30 20:20 DEBUG  WindowsBackend: country=US
06-30 20:20 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:20 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:20 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:20 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:20 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:20 DEBUG  WindowsBackend: windows_language=English
06-30 20:20 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:20 DEBUG  WindowsBackend: bootloader=xp
06-30 20:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6534.89453125 mb free ntfs)
06-30 20:20 DEBUG  WindowsBackend: drive=Drive(C: hd 6534.89453125 mb free ntfs)
06-30 20:20 DEBUG  WindowsBackend: drive=Drive(D: hd 60148.296875 mb free ntfs)
06-30 20:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:20 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
06-30 20:20 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
06-30 20:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 20:20 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:20 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:20 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:20 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:20 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:20 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:20 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:20 DEBUG  CommonBackend: Searching for local CDs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 INFO   root: Already installed, running the uninstaller...
06-30 20:20 INFO   root: Running the uninstaller...
06-30 20:20 INFO   CommonBackend: This is the uninstaller running
06-30 20:20 DEBUG  WindowsFrontend: __init__...
06-30 20:20 DEBUG  WindowsFrontend: on_init...
06-30 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
06-30 20:20 INFO   root: Received settings
06-30 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
06-30 20:20 DEBUG  TaskList: # Running tasklist...
06-30 20:20 DEBUG  TaskList: ## Running Backup ISO...
06-30 20:20 DEBUG  TaskList: ## Finished Backup ISO
06-30 20:20 DEBUG  TaskList: ## Running Remove bootloader entry...
06-30 20:20 ERROR  WindowsBackend: Cannot find bcdedit
06-30 20:20 DEBUG  WindowsBackend: undo_bootini C:
06-30 20:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6534.89453125 mb free ntfs)
06-30 20:20 DEBUG  WindowsBackend: undo_bootini D:
06-30 20:20 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60148.296875 mb free ntfs)
06-30 20:20 DEBUG  TaskList: ## Finished Remove bootloader entry
06-30 20:20 DEBUG  TaskList: ## Running Remove target dir...
06-30 20:20 DEBUG  CommonBackend: Deleting D:\ubuntu
06-30 20:20 DEBUG  TaskList: ## Finished Remove target dir
06-30 20:20 DEBUG  TaskList: ## Running Remove registry key...
06-30 20:20 DEBUG  TaskList: ## Finished Remove registry key
06-30 20:20 DEBUG  TaskList: # Finished tasklist
06-30 20:20 INFO   root: Almost finished uninstalling
06-30 20:20 INFO   root: Finished uninstallation
06-30 20:20 DEBUG  CommonBackend: Fetching basic info...
06-30 20:20 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:20 DEBUG  CommonBackend: platform=win32
06-30 20:20 DEBUG  CommonBackend: osname=nt
06-30 20:20 DEBUG  WindowsBackend: arch=amd64
06-30 20:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\data\isolist.ini
06-30 20:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:20 DEBUG  WindowsBackend: Fetching host info...
06-30 20:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:20 DEBUG  WindowsBackend: windows version=xp
06-30 20:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:20 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:20 DEBUG  WindowsBackend: windows_build=2600
06-30 20:20 DEBUG  WindowsBackend: gmt=-8
06-30 20:20 DEBUG  WindowsBackend: country=US
06-30 20:20 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:20 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:20 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:20 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:20 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:20 DEBUG  WindowsBackend: windows_language=English
06-30 20:20 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:20 DEBUG  WindowsBackend: bootloader=xp
06-30 20:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6534.88671875 mb free ntfs)
06-30 20:20 DEBUG  WindowsBackend: drive=Drive(C: hd 6534.88671875 mb free ntfs)
06-30 20:20 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.328125 mb free ntfs)
06-30 20:20 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:20 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:20 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:20 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:20 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:20 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:20 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:20 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:20 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:20 DEBUG  CommonBackend: Searching for local CDs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Ubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Kubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:20 INFO   root: Running the installer...
06-30 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
06-30 20:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl7.tmp\translations, languages=['en_US', 'en']
06-30 20:21 INFO   WindowsFrontend: Operation cancelled
06-30 20:21 DEBUG  WindowsFrontend: frontend.quit
06-30 20:21 DEBUG  WindowsFrontend: frontend.on_quit
06-30 20:21 DEBUG  root: application.on_quit
06-30 20:21 INFO   root: sys.exit
06-30 20:21 INFO   root: === wubi 10.04 rev189 ===
06-30 20:21 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:21 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\data
06-30 20:21 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\bin\7z.exe
06-30 20:21 DEBUG  CommonBackend: Fetching basic info...
06-30 20:21 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:21 DEBUG  CommonBackend: platform=win32
06-30 20:21 DEBUG  CommonBackend: osname=nt
06-30 20:21 DEBUG  CommonBackend: language=en_US
06-30 20:21 DEBUG  CommonBackend: encoding=cp1252
06-30 20:21 DEBUG  WindowsBackend: arch=amd64
06-30 20:21 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\data\isolist.ini
06-30 20:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:21 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:21 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:21 DEBUG  WindowsBackend: Fetching host info...
06-30 20:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:21 DEBUG  WindowsBackend: windows version=xp
06-30 20:21 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:21 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:21 DEBUG  WindowsBackend: windows_build=2600
06-30 20:21 DEBUG  WindowsBackend: gmt=-8
06-30 20:21 DEBUG  WindowsBackend: country=US
06-30 20:21 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:21 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:21 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:21 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:21 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:21 DEBUG  WindowsBackend: windows_language=English
06-30 20:21 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:21 DEBUG  WindowsBackend: bootloader=xp
06-30 20:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6534.77734375 mb free ntfs)
06-30 20:21 DEBUG  WindowsBackend: drive=Drive(C: hd 6534.77734375 mb free ntfs)
06-30 20:21 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.328125 mb free ntfs)
06-30 20:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:21 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:21 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:21 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:21 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:21 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:21 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:21 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:21 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:21 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:21 DEBUG  CommonBackend: Searching for local CDs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu Netbook CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Kubuntu Netbook CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Xubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Mythbuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 INFO   root: Running the installer...
06-30 20:21 DEBUG  WindowsFrontend: __init__...
06-30 20:21 DEBUG  WindowsFrontend: on_init...
06-30 20:21 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
06-30 20:21 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
06-30 20:21 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
06-30 20:21 INFO   root: Received settings
06-30 20:21 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\translations, languages=['en_US', 'en']
06-30 20:21 DEBUG  TaskList: # Running tasklist...
06-30 20:21 DEBUG  TaskList: ## Running select_target_dir...
06-30 20:21 INFO   WindowsBackend: Installing into D:\ubuntu
06-30 20:21 DEBUG  TaskList: ## Finished select_target_dir
06-30 20:21 DEBUG  TaskList: ## Running create_dir_structure...
06-30 20:21 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-30 20:21 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-30 20:21 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-30 20:21 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-30 20:21 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-30 20:21 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-30 20:21 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-30 20:21 DEBUG  TaskList: ## Finished create_dir_structure
06-30 20:21 DEBUG  TaskList: ## Running uncompress_target_dir...
06-30 20:21 DEBUG  TaskList: ## Finished uncompress_target_dir
06-30 20:21 DEBUG  TaskList: ## Running create_uninstaller...
06-30 20:21 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-30 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-30 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-30 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-30 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-30 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
06-30 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-30 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-30 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-30 20:21 DEBUG  TaskList: ## Finished create_uninstaller
06-30 20:21 DEBUG  TaskList: ## Running copy_installation_files...
06-30 20:21 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-30 20:21 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\winboot -> D:\ubuntu\winboot
06-30 20:21 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-30 20:21 DEBUG  TaskList: ## Finished copy_installation_files
06-30 20:21 DEBUG  TaskList: ## Running get_iso...
06-30 20:21 DEBUG  CommonBackend: Searching for local CD
06-30 20:21 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl8.tmp\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:21 DEBUG  CommonBackend: Searching for local ISO
06-30 20:21 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-30 20:21 DEBUG  TaskList: New task get_metalink
06-30 20:21 DEBUG  TaskList: ### Running get_metalink...
06-30 20:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
06-30 20:21 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
06-30 20:21 DEBUG  downloader: download finished (read 7472 bytes)
06-30 20:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
06-30 20:21 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
06-30 20:21 DEBUG  downloader: download finished (read 639 bytes)
06-30 20:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
06-30 20:21 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
06-30 20:21 DEBUG  downloader: download finished (read 189 bytes)
06-30 20:21 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-30 20:21 INFO   saplog: Checking block bindings..
06-30 20:21 INFO   saplog: Key verified successfully.
06-30 20:21 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

06-30 20:21 DEBUG  TaskList: ### Finished get_metalink
06-30 20:21 DEBUG  TaskList: New task download
06-30 20:21 DEBUG  TaskList: ### Running download...
06-30 20:21 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
06-30 20:22 INFO   WindowsFrontend: Operation cancelled
06-30 20:22 DEBUG  WindowsFrontend: frontend.quit
06-30 20:22 DEBUG  WindowsFrontend: frontend.on_quit
06-30 20:22 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
06-30 20:22 DEBUG  TaskList: # Cancelling tasklist
06-30 20:22 DEBUG  TaskList: ### Finished download
06-30 20:22 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
06-30 20:22 DEBUG  root: application.on_quit
06-30 20:22 DEBUG  root: Forceful exit
06-30 20:22 INFO   root: sys.exit
06-30 20:22 INFO   root: === wubi 10.04 rev189 ===
06-30 20:22 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:22 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\data
06-30 20:22 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\bin\7z.exe
06-30 20:22 DEBUG  CommonBackend: Fetching basic info...
06-30 20:22 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:22 DEBUG  CommonBackend: platform=win32
06-30 20:22 DEBUG  CommonBackend: osname=nt
06-30 20:22 DEBUG  CommonBackend: language=en_US
06-30 20:22 DEBUG  CommonBackend: encoding=cp1252
06-30 20:22 DEBUG  WindowsBackend: arch=amd64
06-30 20:22 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
06-30 20:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:22 DEBUG  WindowsBackend: Fetching host info...
06-30 20:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:22 DEBUG  WindowsBackend: windows version=xp
06-30 20:22 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:22 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:22 DEBUG  WindowsBackend: windows_build=2600
06-30 20:22 DEBUG  WindowsBackend: gmt=-8
06-30 20:22 DEBUG  WindowsBackend: country=US
06-30 20:22 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:22 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:22 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:22 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:22 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:22 DEBUG  WindowsBackend: windows_language=English
06-30 20:22 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:22 DEBUG  WindowsBackend: bootloader=xp
06-30 20:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6534.66015625 mb free ntfs)
06-30 20:22 DEBUG  WindowsBackend: drive=Drive(C: hd 6534.66015625 mb free ntfs)
06-30 20:22 DEBUG  WindowsBackend: drive=Drive(D: hd 60151.296875 mb free ntfs)
06-30 20:22 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:22 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
06-30 20:22 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
06-30 20:22 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 20:22 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:22 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:22 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:22 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:22 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:22 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:22 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:22 DEBUG  CommonBackend: Searching for local CDs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 INFO   root: Already installed, running the uninstaller...
06-30 20:22 INFO   root: Running the uninstaller...
06-30 20:22 INFO   CommonBackend: This is the uninstaller running
06-30 20:22 DEBUG  WindowsFrontend: __init__...
06-30 20:22 DEBUG  WindowsFrontend: on_init...
06-30 20:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
06-30 20:22 INFO   root: Received settings
06-30 20:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
06-30 20:22 DEBUG  TaskList: # Running tasklist...
06-30 20:22 DEBUG  TaskList: ## Running Backup ISO...
06-30 20:22 DEBUG  TaskList: ## Finished Backup ISO
06-30 20:22 DEBUG  TaskList: ## Running Remove bootloader entry...
06-30 20:22 ERROR  WindowsBackend: Cannot find bcdedit
06-30 20:22 DEBUG  WindowsBackend: undo_bootini C:
06-30 20:22 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6534.66015625 mb free ntfs)
06-30 20:22 DEBUG  WindowsBackend: undo_bootini D:
06-30 20:22 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60151.296875 mb free ntfs)
06-30 20:22 DEBUG  TaskList: ## Finished Remove bootloader entry
06-30 20:22 DEBUG  TaskList: ## Running Remove target dir...
06-30 20:22 DEBUG  CommonBackend: Deleting D:\ubuntu
06-30 20:22 DEBUG  TaskList: ## Finished Remove target dir
06-30 20:22 DEBUG  TaskList: ## Running Remove registry key...
06-30 20:22 DEBUG  TaskList: ## Finished Remove registry key
06-30 20:22 DEBUG  TaskList: # Finished tasklist
06-30 20:22 INFO   root: Almost finished uninstalling
06-30 20:22 INFO   root: Finished uninstallation
06-30 20:22 DEBUG  CommonBackend: Fetching basic info...
06-30 20:22 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:22 DEBUG  CommonBackend: platform=win32
06-30 20:22 DEBUG  CommonBackend: osname=nt
06-30 20:22 DEBUG  WindowsBackend: arch=amd64
06-30 20:22 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\data\isolist.ini
06-30 20:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:22 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:22 DEBUG  WindowsBackend: Fetching host info...
06-30 20:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:22 DEBUG  WindowsBackend: windows version=xp
06-30 20:22 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:22 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:22 DEBUG  WindowsBackend: windows_build=2600
06-30 20:22 DEBUG  WindowsBackend: gmt=-8
06-30 20:22 DEBUG  WindowsBackend: country=US
06-30 20:22 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:22 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:22 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:22 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:22 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:22 DEBUG  WindowsBackend: windows_language=English
06-30 20:22 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:22 DEBUG  WindowsBackend: bootloader=xp
06-30 20:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6534.6484375 mb free ntfs)
06-30 20:22 DEBUG  WindowsBackend: drive=Drive(C: hd 6534.6484375 mb free ntfs)
06-30 20:22 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.3125 mb free ntfs)
06-30 20:22 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:22 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:22 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:22 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:22 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:22 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:22 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:22 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:22 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:22 DEBUG  CommonBackend: Searching for local CDs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Ubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Kubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:22 INFO   root: Running the installer...
06-30 20:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
06-30 20:22 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl9.tmp\translations, languages=['en_US', 'en']
06-30 20:22 INFO   WindowsFrontend: Operation cancelled
06-30 20:22 DEBUG  WindowsFrontend: frontend.quit
06-30 20:22 DEBUG  WindowsFrontend: frontend.on_quit
06-30 20:22 DEBUG  root: application.on_quit
06-30 20:22 INFO   root: sys.exit
06-30 20:31 INFO   root: === wubi 10.04 rev189 ===
06-30 20:31 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:31 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\data
06-30 20:31 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\bin\7z.exe
06-30 20:31 DEBUG  CommonBackend: Fetching basic info...
06-30 20:31 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:31 DEBUG  CommonBackend: platform=win32
06-30 20:31 DEBUG  CommonBackend: osname=nt
06-30 20:31 DEBUG  CommonBackend: language=en_US
06-30 20:31 DEBUG  CommonBackend: encoding=cp1252
06-30 20:31 DEBUG  WindowsBackend: arch=amd64
06-30 20:31 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\data\isolist.ini
06-30 20:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:31 DEBUG  WindowsBackend: Fetching host info...
06-30 20:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:31 DEBUG  WindowsBackend: windows version=xp
06-30 20:31 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:31 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:31 DEBUG  WindowsBackend: windows_build=2600
06-30 20:31 DEBUG  WindowsBackend: gmt=-8
06-30 20:31 DEBUG  WindowsBackend: country=US
06-30 20:31 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:31 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:31 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:31 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:31 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:31 DEBUG  WindowsBackend: windows_language=English
06-30 20:31 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:31 DEBUG  WindowsBackend: bootloader=xp
06-30 20:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6520.51171875 mb free ntfs)
06-30 20:31 DEBUG  WindowsBackend: drive=Drive(C: hd 6520.51171875 mb free ntfs)
06-30 20:31 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.3125 mb free ntfs)
06-30 20:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:31 DEBUG  WindowsBackend: drive=Drive(G: removable 3.58984375 mb free fat32)
06-30 20:31 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:31 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:31 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:31 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:31 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:31 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:31 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:31 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:31 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:31 DEBUG  CommonBackend: Searching for local CDs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Ubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Kubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 INFO   root: Running the installer...
06-30 20:31 DEBUG  WindowsFrontend: __init__...
06-30 20:31 DEBUG  WindowsFrontend: on_init...
06-30 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_US', 'en']
06-30 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pylF.tmp\translations, languages=['en_US', 'en']
06-30 20:31 INFO   WindowsFrontend: Operation cancelled
06-30 20:31 DEBUG  WindowsFrontend: frontend.quit
06-30 20:31 DEBUG  WindowsFrontend: frontend.on_quit
06-30 20:31 DEBUG  root: application.on_quit
06-30 20:31 INFO   root: sys.exit
06-30 20:31 INFO   root: === wubi 10.04 rev189 ===
06-30 20:31 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:31 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\data
06-30 20:31 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\bin\7z.exe
06-30 20:31 DEBUG  CommonBackend: Fetching basic info...
06-30 20:31 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:31 DEBUG  CommonBackend: platform=win32
06-30 20:31 DEBUG  CommonBackend: osname=nt
06-30 20:31 DEBUG  CommonBackend: language=en_US
06-30 20:31 DEBUG  CommonBackend: encoding=cp1252
06-30 20:31 DEBUG  WindowsBackend: arch=amd64
06-30 20:31 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\data\isolist.ini
06-30 20:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:31 DEBUG  WindowsBackend: Fetching host info...
06-30 20:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:31 DEBUG  WindowsBackend: windows version=xp
06-30 20:31 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:31 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:31 DEBUG  WindowsBackend: windows_build=2600
06-30 20:31 DEBUG  WindowsBackend: gmt=-8
06-30 20:31 DEBUG  WindowsBackend: country=US
06-30 20:31 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:31 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:31 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:31 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:31 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:31 DEBUG  WindowsBackend: windows_language=English
06-30 20:31 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:31 DEBUG  WindowsBackend: bootloader=xp
06-30 20:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6520.3984375 mb free ntfs)
06-30 20:31 DEBUG  WindowsBackend: drive=Drive(C: hd 6520.3984375 mb free ntfs)
06-30 20:31 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.3125 mb free ntfs)
06-30 20:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:31 DEBUG  WindowsBackend: drive=Drive(G: removable 3.58984375 mb free fat32)
06-30 20:31 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:31 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:31 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:31 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:31 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:31 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:31 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:31 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:31 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:31 DEBUG  CommonBackend: Searching for local CDs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Ubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Kubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
06-30 20:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
06-30 20:31 INFO   root: Running the installer...
06-30 20:31 DEBUG  WindowsFrontend: __init__...
06-30 20:31 DEBUG  WindowsFrontend: on_init...
06-30 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\translations, languages=['en_US', 'en']
06-30 20:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl10.tmp\translations, languages=['en_US', 'en']
06-30 20:31 INFO   WindowsFrontend: Operation cancelled
06-30 20:31 DEBUG  WindowsFrontend: frontend.quit
06-30 20:31 DEBUG  WindowsFrontend: frontend.on_quit
06-30 20:31 DEBUG  root: application.on_quit
06-30 20:31 INFO   root: sys.exit
06-30 20:54 INFO   root: === wubi 10.04 rev189 ===
06-30 20:54 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:54 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data
06-30 20:54 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
06-30 20:54 DEBUG  CommonBackend: Fetching basic info...
06-30 20:54 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:54 DEBUG  CommonBackend: platform=win32
06-30 20:54 DEBUG  CommonBackend: osname=nt
06-30 20:54 DEBUG  CommonBackend: language=en_US
06-30 20:54 DEBUG  CommonBackend: encoding=cp1252
06-30 20:54 DEBUG  WindowsBackend: arch=amd64
06-30 20:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
06-30 20:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:54 DEBUG  WindowsBackend: Fetching host info...
06-30 20:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:54 DEBUG  WindowsBackend: windows version=xp
06-30 20:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:54 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:54 DEBUG  WindowsBackend: windows_build=2600
06-30 20:54 DEBUG  WindowsBackend: gmt=-8
06-30 20:54 DEBUG  WindowsBackend: country=US
06-30 20:54 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:54 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:54 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:54 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:54 DEBUG  WindowsBackend: windows_language=English
06-30 20:54 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:54 DEBUG  WindowsBackend: bootloader=xp
06-30 20:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6518.4375 mb free ntfs)
06-30 20:54 DEBUG  WindowsBackend: drive=Drive(C: hd 6518.4375 mb free ntfs)
06-30 20:54 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.3242188 mb free ntfs)
06-30 20:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
06-30 20:54 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:54 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:54 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:54 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:54 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:54 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:54 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:54 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:54 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:54 DEBUG  CommonBackend: Searching for local CDs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-30 20:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:55 INFO   root: Running the installer...
06-30 20:55 DEBUG  WindowsFrontend: __init__...
06-30 20:55 DEBUG  WindowsFrontend: on_init...
06-30 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 20:55 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
06-30 20:55 INFO   root: Received settings
06-30 20:55 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 20:55 DEBUG  TaskList: # Running tasklist...
06-30 20:55 DEBUG  TaskList: ## Running select_target_dir...
06-30 20:55 INFO   WindowsBackend: Installing into D:\ubuntu
06-30 20:55 DEBUG  TaskList: ## Finished select_target_dir
06-30 20:55 DEBUG  TaskList: ## Running create_dir_structure...
06-30 20:55 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-30 20:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-30 20:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-30 20:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-30 20:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-30 20:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-30 20:55 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-30 20:55 DEBUG  TaskList: ## Finished create_dir_structure
06-30 20:55 DEBUG  TaskList: ## Running uncompress_target_dir...
06-30 20:55 DEBUG  TaskList: ## Finished uncompress_target_dir
06-30 20:55 DEBUG  TaskList: ## Running create_uninstaller...
06-30 20:55 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-30 20:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-30 20:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-30 20:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-30 20:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-30 20:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
06-30 20:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-30 20:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-30 20:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-30 20:55 DEBUG  TaskList: ## Finished create_uninstaller
06-30 20:55 DEBUG  TaskList: ## Running copy_installation_files...
06-30 20:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-30 20:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\winboot -> D:\ubuntu\winboot
06-30 20:55 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-30 20:55 DEBUG  TaskList: ## Finished copy_installation_files
06-30 20:55 DEBUG  TaskList: ## Running get_iso...
06-30 20:55 DEBUG  CommonBackend: Searching for local CD
06-30 20:55 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 20:55 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 20:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:55 DEBUG  CommonBackend: Searching for local ISO
06-30 20:55 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-30 20:55 DEBUG  TaskList: New task get_metalink
06-30 20:55 DEBUG  TaskList: ### Running get_metalink...
06-30 20:55 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
06-30 20:55 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
06-30 20:55 DEBUG  downloader: download finished (read 7472 bytes)
06-30 20:55 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
06-30 20:55 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
06-30 20:55 DEBUG  downloader: download finished (read 639 bytes)
06-30 20:55 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
06-30 20:55 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
06-30 20:55 DEBUG  downloader: download finished (read 189 bytes)
06-30 20:55 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-30 20:55 INFO   saplog: Checking block bindings..
06-30 20:55 INFO   saplog: Key verified successfully.
06-30 20:55 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

06-30 20:55 DEBUG  TaskList: ### Finished get_metalink
06-30 20:55 DEBUG  TaskList: New task download
06-30 20:55 DEBUG  TaskList: ### Running download...
06-30 20:55 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
06-30 20:55 INFO   WindowsFrontend: Operation cancelled
06-30 20:55 DEBUG  WindowsFrontend: frontend.quit
06-30 20:55 DEBUG  WindowsFrontend: frontend.on_quit
06-30 20:55 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
06-30 20:55 DEBUG  TaskList: # Cancelling tasklist
06-30 20:55 DEBUG  TaskList: ### Finished download
06-30 20:55 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
06-30 20:55 DEBUG  root: application.on_quit
06-30 20:55 DEBUG  root: Forceful exit
06-30 20:55 INFO   root: sys.exit
06-30 20:56 INFO   root: === wubi 10.04 rev189 ===
06-30 20:56 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 20:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 20:56 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\data
06-30 20:56 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
06-30 20:56 DEBUG  CommonBackend: Fetching basic info...
06-30 20:56 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:56 DEBUG  CommonBackend: platform=win32
06-30 20:56 DEBUG  CommonBackend: osname=nt
06-30 20:56 DEBUG  CommonBackend: language=en_US
06-30 20:56 DEBUG  CommonBackend: encoding=cp1252
06-30 20:56 DEBUG  WindowsBackend: arch=amd64
06-30 20:56 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
06-30 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:56 DEBUG  WindowsBackend: Fetching host info...
06-30 20:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:56 DEBUG  WindowsBackend: windows version=xp
06-30 20:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:56 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:56 DEBUG  WindowsBackend: windows_build=2600
06-30 20:56 DEBUG  WindowsBackend: gmt=-8
06-30 20:56 DEBUG  WindowsBackend: country=US
06-30 20:56 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:56 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:56 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:56 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:56 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:56 DEBUG  WindowsBackend: windows_language=English
06-30 20:56 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:56 DEBUG  WindowsBackend: bootloader=xp
06-30 20:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6518.1484375 mb free ntfs)
06-30 20:56 DEBUG  WindowsBackend: drive=Drive(C: hd 6518.1484375 mb free ntfs)
06-30 20:56 DEBUG  WindowsBackend: drive=Drive(D: hd 60153.7773438 mb free ntfs)
06-30 20:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-30 20:56 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
06-30 20:56 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
06-30 20:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 20:56 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:56 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:56 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 20:56 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 20:56 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:56 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 20:56 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
06-30 20:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
06-30 20:56 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  CommonBackend: Searching for local CDs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 INFO   root: Already installed, running the uninstaller...
06-30 20:56 INFO   root: Running the uninstaller...
06-30 20:56 INFO   CommonBackend: This is the uninstaller running
06-30 20:56 DEBUG  WindowsFrontend: __init__...
06-30 20:56 DEBUG  WindowsFrontend: on_init...
06-30 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
06-30 20:56 INFO   root: Received settings
06-30 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
06-30 20:56 DEBUG  TaskList: # Running tasklist...
06-30 20:56 DEBUG  TaskList: ## Running Backup ISO...
06-30 20:56 DEBUG  TaskList: ## Finished Backup ISO
06-30 20:56 DEBUG  TaskList: ## Running Remove bootloader entry...
06-30 20:56 ERROR  WindowsBackend: Cannot find bcdedit
06-30 20:56 DEBUG  WindowsBackend: undo_bootini C:
06-30 20:56 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6518.1484375 mb free ntfs)
06-30 20:56 DEBUG  WindowsBackend: undo_bootini D:
06-30 20:56 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60153.7773438 mb free ntfs)
06-30 20:56 DEBUG  TaskList: ## Finished Remove bootloader entry
06-30 20:56 DEBUG  TaskList: ## Running Remove target dir...
06-30 20:56 DEBUG  CommonBackend: Deleting D:\ubuntu
06-30 20:56 DEBUG  TaskList: ## Finished Remove target dir
06-30 20:56 DEBUG  TaskList: ## Running Remove registry key...
06-30 20:56 DEBUG  TaskList: ## Finished Remove registry key
06-30 20:56 DEBUG  TaskList: # Finished tasklist
06-30 20:56 INFO   root: Almost finished uninstalling
06-30 20:56 INFO   root: Finished uninstallation
06-30 20:56 DEBUG  CommonBackend: Fetching basic info...
06-30 20:56 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 20:56 DEBUG  CommonBackend: platform=win32
06-30 20:56 DEBUG  CommonBackend: osname=nt
06-30 20:56 DEBUG  WindowsBackend: arch=amd64
06-30 20:56 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
06-30 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 20:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 20:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 20:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 20:56 DEBUG  WindowsBackend: Fetching host info...
06-30 20:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 20:56 DEBUG  WindowsBackend: windows version=xp
06-30 20:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 20:56 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 20:56 DEBUG  WindowsBackend: windows_build=2600
06-30 20:56 DEBUG  WindowsBackend: gmt=-8
06-30 20:56 DEBUG  WindowsBackend: country=US
06-30 20:56 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 20:56 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 20:56 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 20:56 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 20:56 DEBUG  WindowsBackend: windows_language_code=1033
06-30 20:56 DEBUG  WindowsBackend: windows_language=English
06-30 20:56 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 20:56 DEBUG  WindowsBackend: bootloader=xp
06-30 20:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6518.13671875 mb free ntfs)
06-30 20:56 DEBUG  WindowsBackend: drive=Drive(C: hd 6518.13671875 mb free ntfs)
06-30 20:56 DEBUG  WindowsBackend: drive=Drive(D: hd 60155.3085938 mb free ntfs)
06-30 20:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-30 20:56 DEBUG  WindowsBackend: uninstaller_path=None
06-30 20:56 DEBUG  WindowsBackend: previous_target_dir=None
06-30 20:56 DEBUG  WindowsBackend: previous_distro_name=None
06-30 20:56 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 20:56 DEBUG  WindowsBackend: keyboard_layout=us
06-30 20:56 DEBUG  WindowsBackend: keyboard_variant=
06-30 20:56 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 20:56 DEBUG  CommonBackend: Checking pre-specified ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  CommonBackend: Searching for local CDs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 20:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 20:56 INFO   root: Running the installer...
06-30 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
06-30 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
06-30 20:56 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
06-30 20:56 INFO   root: Received settings
06-30 20:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\translations, languages=['en_US', 'en']
06-30 20:56 DEBUG  TaskList: # Running tasklist...
06-30 20:56 DEBUG  TaskList: ## Running select_target_dir...
06-30 20:56 INFO   WindowsBackend: Installing into D:\ubuntu
06-30 20:56 DEBUG  TaskList: ## Finished select_target_dir
06-30 20:56 DEBUG  TaskList: ## Running create_dir_structure...
06-30 20:56 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-30 20:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-30 20:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-30 20:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-30 20:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-30 20:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-30 20:56 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-30 20:56 DEBUG  TaskList: ## Finished create_dir_structure
06-30 20:56 DEBUG  TaskList: ## Running uncompress_target_dir...
06-30 20:56 DEBUG  TaskList: ## Finished uncompress_target_dir
06-30 20:56 DEBUG  TaskList: ## Running create_uninstaller...
06-30 20:56 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-30 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-30 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-30 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-30 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-30 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
06-30 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-30 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-30 20:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-30 20:56 DEBUG  TaskList: ## Finished create_uninstaller
06-30 20:56 DEBUG  TaskList: ## Running copy_installation_files...
06-30 20:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-30 20:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\winboot -> D:\ubuntu\winboot
06-30 20:56 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-30 20:56 DEBUG  TaskList: ## Finished copy_installation_files
06-30 20:56 DEBUG  TaskList: ## Running get_iso...
06-30 20:56 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  TaskList: New task is_valid_iso
06-30 20:56 DEBUG  TaskList: ### Running is_valid_iso...
06-30 20:56 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  TaskList: ### Finished is_valid_iso
06-30 20:56 DEBUG  TaskList: New task check_iso
06-30 20:56 DEBUG  TaskList: ### Running check_iso...
06-30 20:56 DEBUG  CommonBackend: Checking E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
06-30 20:56 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
06-30 20:56 DEBUG  TaskList: New task get_metalink
06-30 20:56 DEBUG  TaskList: #### Running get_metalink...
06-30 20:56 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > D:\ubuntu\install
06-30 20:56 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink, basename=ubuntu-10.04-desktop-i386.metalink, length=7420, text=None
06-30 20:56 DEBUG  downloader: download finished (read 7420 bytes)
06-30 20:56 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
06-30 20:56 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
06-30 20:56 DEBUG  downloader: download finished (read 639 bytes)
06-30 20:56 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
06-30 20:56 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
06-30 20:56 DEBUG  downloader: download finished (read 189 bytes)
06-30 20:56 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-30 20:56 INFO   saplog: Checking block bindings..
06-30 20:56 INFO   saplog: Key verified successfully.
06-30 20:56 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

06-30 20:56 DEBUG  TaskList: #### Finished get_metalink
06-30 20:56 DEBUG  TaskList: New task get_file_md5
06-30 20:56 DEBUG  TaskList: #### Running get_file_md5...
06-30 21:11 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 165, in get_file_md5
IOError: [Errno 13] Permission denied
06-30 21:11 DEBUG  TaskList: # Cancelling tasklist
06-30 21:11 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 165, in get_file_md5
IOError: [Errno 13] Permission denied
06-30 21:11 ERROR  CommonBackend: Invalid md5 for ISO E:\ubuntu-10.04-desktop-i386.iso (d044a2a0c8103fc3e5b7e18b0f7de1c8 != None)
None
06-30 21:11 DEBUG  TaskList: ### Finished check_iso
06-30 21:11 DEBUG  CommonBackend: Searching for local CD
06-30 21:11 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
06-30 21:11 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
06-30 21:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 21:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 INFO   root: === wubi 10.04 rev189 ===
06-30 21:24 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
06-30 21:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
06-30 21:24 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data
06-30 21:24 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
06-30 21:24 DEBUG  CommonBackend: Fetching basic info...
06-30 21:24 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 21:24 DEBUG  CommonBackend: platform=win32
06-30 21:24 DEBUG  CommonBackend: osname=nt
06-30 21:24 DEBUG  CommonBackend: language=en_US
06-30 21:24 DEBUG  CommonBackend: encoding=cp1252
06-30 21:24 DEBUG  WindowsBackend: arch=amd64
06-30 21:24 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
06-30 21:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 21:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 21:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 21:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 21:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 21:24 DEBUG  WindowsBackend: Fetching host info...
06-30 21:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 21:24 DEBUG  WindowsBackend: windows version=xp
06-30 21:24 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 21:24 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 21:24 DEBUG  WindowsBackend: windows_build=2600
06-30 21:24 DEBUG  WindowsBackend: gmt=-8
06-30 21:24 DEBUG  WindowsBackend: country=US
06-30 21:24 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 21:24 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 21:24 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 21:24 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 21:24 DEBUG  WindowsBackend: windows_language_code=1033
06-30 21:24 DEBUG  WindowsBackend: windows_language=English
06-30 21:24 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 21:24 DEBUG  WindowsBackend: bootloader=xp
06-30 21:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6515.765625 mb free ntfs)
06-30 21:24 DEBUG  WindowsBackend: drive=Drive(C: hd 6515.765625 mb free ntfs)
06-30 21:24 DEBUG  WindowsBackend: drive=Drive(D: hd 60154.4882813 mb free ntfs)
06-30 21:24 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-30 21:24 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
06-30 21:24 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
06-30 21:24 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-30 21:24 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 21:24 DEBUG  WindowsBackend: keyboard_layout=us
06-30 21:24 DEBUG  WindowsBackend: keyboard_variant=
06-30 21:24 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-30 21:24 DEBUG  CommonBackend: locale=en_US.UTF-8
06-30 21:24 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 21:24 DEBUG  CommonBackend: Searching ISOs on USB devices
06-30 21:24 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
06-30 21:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
06-30 21:24 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  CommonBackend: Searching for local CDs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 INFO   root: Already installed, running the uninstaller...
06-30 21:24 INFO   root: Running the uninstaller...
06-30 21:24 INFO   CommonBackend: This is the uninstaller running
06-30 21:24 DEBUG  WindowsFrontend: __init__...
06-30 21:24 DEBUG  WindowsFrontend: on_init...
06-30 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 21:24 INFO   root: Received settings
06-30 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 21:24 DEBUG  TaskList: # Running tasklist...
06-30 21:24 DEBUG  TaskList: ## Running Backup ISO...
06-30 21:24 DEBUG  TaskList: ## Finished Backup ISO
06-30 21:24 DEBUG  TaskList: ## Running Remove bootloader entry...
06-30 21:24 ERROR  WindowsBackend: Cannot find bcdedit
06-30 21:24 DEBUG  WindowsBackend: undo_bootini C:
06-30 21:24 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6515.765625 mb free ntfs)
06-30 21:24 DEBUG  WindowsBackend: undo_bootini D:
06-30 21:24 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60154.4882813 mb free ntfs)
06-30 21:24 DEBUG  TaskList: ## Finished Remove bootloader entry
06-30 21:24 DEBUG  TaskList: ## Running Remove target dir...
06-30 21:24 DEBUG  CommonBackend: Deleting D:\ubuntu
06-30 21:24 DEBUG  TaskList: ## Finished Remove target dir
06-30 21:24 DEBUG  TaskList: ## Running Remove registry key...
06-30 21:24 DEBUG  TaskList: ## Finished Remove registry key
06-30 21:24 DEBUG  TaskList: # Finished tasklist
06-30 21:24 INFO   root: Almost finished uninstalling
06-30 21:24 INFO   root: Finished uninstallation
06-30 21:24 DEBUG  CommonBackend: Fetching basic info...
06-30 21:24 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
06-30 21:24 DEBUG  CommonBackend: platform=win32
06-30 21:24 DEBUG  CommonBackend: osname=nt
06-30 21:24 DEBUG  WindowsBackend: arch=amd64
06-30 21:24 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
06-30 21:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-30 21:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-30 21:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-30 21:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-30 21:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-30 21:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-30 21:24 DEBUG  WindowsBackend: Fetching host info...
06-30 21:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-30 21:24 DEBUG  WindowsBackend: windows version=xp
06-30 21:24 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-30 21:24 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-30 21:24 DEBUG  WindowsBackend: windows_build=2600
06-30 21:24 DEBUG  WindowsBackend: gmt=-8
06-30 21:24 DEBUG  WindowsBackend: country=US
06-30 21:24 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-30 21:24 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
06-30 21:24 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
06-30 21:24 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
06-30 21:24 DEBUG  WindowsBackend: windows_language_code=1033
06-30 21:24 DEBUG  WindowsBackend: windows_language=English
06-30 21:24 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
06-30 21:24 DEBUG  WindowsBackend: bootloader=xp
06-30 21:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6515.70703125 mb free ntfs)
06-30 21:24 DEBUG  WindowsBackend: drive=Drive(C: hd 6515.70703125 mb free ntfs)
06-30 21:24 DEBUG  WindowsBackend: drive=Drive(D: hd 60154.59375 mb free ntfs)
06-30 21:24 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-30 21:24 DEBUG  WindowsBackend: uninstaller_path=None
06-30 21:24 DEBUG  WindowsBackend: previous_target_dir=None
06-30 21:24 DEBUG  WindowsBackend: previous_distro_name=None
06-30 21:24 DEBUG  WindowsBackend: keyboard_id=67699721
06-30 21:24 DEBUG  WindowsBackend: keyboard_layout=us
06-30 21:24 DEBUG  WindowsBackend: keyboard_variant=
06-30 21:24 DEBUG  WindowsBackend: total_memory_mb=1014.421875
06-30 21:24 DEBUG  CommonBackend: Checking pre-specified ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  CommonBackend: Searching for local CDs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-30 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-30 21:24 INFO   root: Running the installer...
06-30 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 21:24 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
06-30 21:24 INFO   root: Received settings
06-30 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
06-30 21:24 DEBUG  TaskList: # Running tasklist...
06-30 21:24 DEBUG  TaskList: ## Running select_target_dir...
06-30 21:24 INFO   WindowsBackend: Installing into D:\ubuntu
06-30 21:24 DEBUG  TaskList: ## Finished select_target_dir
06-30 21:24 DEBUG  TaskList: ## Running create_dir_structure...
06-30 21:24 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-30 21:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-30 21:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-30 21:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-30 21:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-30 21:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-30 21:24 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-30 21:24 DEBUG  TaskList: ## Finished create_dir_structure
06-30 21:24 DEBUG  TaskList: ## Running uncompress_target_dir...
06-30 21:24 DEBUG  TaskList: ## Finished uncompress_target_dir
06-30 21:24 DEBUG  TaskList: ## Running create_uninstaller...
06-30 21:24 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-30 21:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-30 21:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-30 21:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-30 21:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-30 21:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
06-30 21:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-30 21:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-30 21:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-30 21:24 DEBUG  TaskList: ## Finished create_uninstaller
06-30 21:24 DEBUG  TaskList: ## Running copy_installation_files...
06-30 21:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-30 21:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\winboot -> D:\ubuntu\winboot
06-30 21:24 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-30 21:24 DEBUG  TaskList: ## Finished copy_installation_files
06-30 21:24 DEBUG  TaskList: ## Running get_iso...
06-30 21:24 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  TaskList: New task is_valid_iso
06-30 21:24 DEBUG  TaskList: ### Running is_valid_iso...
06-30 21:24 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  TaskList: ### Finished is_valid_iso
06-30 21:24 DEBUG  TaskList: New task check_iso
06-30 21:24 DEBUG  TaskList: ### Running check_iso...
06-30 21:24 DEBUG  CommonBackend: Checking E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
06-30 21:24 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
06-30 21:24 DEBUG  TaskList: New task get_metalink
06-30 21:24 DEBUG  TaskList: #### Running get_metalink...
06-30 21:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > D:\ubuntu\install
06-30 21:24 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink, basename=ubuntu-10.04-desktop-i386.metalink, length=7420, text=None
06-30 21:24 DEBUG  downloader: download finished (read 7420 bytes)
06-30 21:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
06-30 21:24 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
06-30 21:24 DEBUG  downloader: download finished (read 639 bytes)
06-30 21:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
06-30 21:24 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
06-30 21:24 DEBUG  downloader: download finished (read 189 bytes)
06-30 21:24 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-30 21:24 INFO   saplog: Checking block bindings..
06-30 21:24 INFO   saplog: Key verified successfully.
06-30 21:24 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

06-30 21:24 DEBUG  TaskList: #### Finished get_metalink
06-30 21:24 DEBUG  TaskList: New task get_file_md5
06-30 21:24 DEBUG  TaskList: #### Running get_file_md5...
06-30 21:34 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 165, in get_file_md5
IOError: [Errno 13] Permission denied
06-30 21:34 DEBUG  TaskList: # Cancelling tasklist
06-30 21:34 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 165, in get_file_md5
IOError: [Errno 13] Permission denied
06-30 21:34 ERROR  CommonBackend: Invalid md5 for ISO E:\ubuntu-10.04-desktop-i386.iso (d044a2a0c8103fc3e5b7e18b0f7de1c8 != None)
None
06-30 21:34 DEBUG  TaskList: ### Finished check_iso
06-30 21:34 DEBUG  CommonBackend: Searching for local CD
06-30 21:34 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
06-30 21:34 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
06-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-30 21:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 20:46 INFO   root: === wubi 10.04 rev189 ===
07-01 20:46 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
07-01 20:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
07-01 20:46 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data
07-01 20:46 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
07-01 20:46 DEBUG  CommonBackend: Fetching basic info...
07-01 20:46 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
07-01 20:46 DEBUG  CommonBackend: platform=win32
07-01 20:46 DEBUG  CommonBackend: osname=nt
07-01 20:46 DEBUG  CommonBackend: language=en_US
07-01 20:46 DEBUG  CommonBackend: encoding=cp1252
07-01 20:46 DEBUG  WindowsBackend: arch=amd64
07-01 20:46 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
07-01 20:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-01 20:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-01 20:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-01 20:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-01 20:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-01 20:46 DEBUG  WindowsBackend: Fetching host info...
07-01 20:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-01 20:46 DEBUG  WindowsBackend: windows version=xp
07-01 20:46 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-01 20:46 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-01 20:46 DEBUG  WindowsBackend: windows_build=2600
07-01 20:46 DEBUG  WindowsBackend: gmt=-8
07-01 20:46 DEBUG  WindowsBackend: country=US
07-01 20:46 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-01 20:46 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-01 20:46 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-01 20:46 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-01 20:46 DEBUG  WindowsBackend: windows_language_code=1033
07-01 20:46 DEBUG  WindowsBackend: windows_language=English
07-01 20:46 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-01 20:46 DEBUG  WindowsBackend: bootloader=xp
07-01 20:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6493.09765625 mb free ntfs)
07-01 20:46 DEBUG  WindowsBackend: drive=Drive(C: hd 6493.09765625 mb free ntfs)
07-01 20:46 DEBUG  WindowsBackend: drive=Drive(D: hd 60153.0664063 mb free ntfs)
07-01 20:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-01 20:46 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-01 20:46 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-01 20:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-01 20:46 DEBUG  WindowsBackend: keyboard_id=67699721
07-01 20:46 DEBUG  WindowsBackend: keyboard_layout=us
07-01 20:46 DEBUG  WindowsBackend: keyboard_variant=
07-01 20:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-01 20:46 DEBUG  CommonBackend: locale=en_US.UTF-8
07-01 20:46 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-01 20:46 DEBUG  CommonBackend: Searching ISOs on USB devices
07-01 20:46 DEBUG  CommonBackend: Searching for local CDs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 INFO   root: Already installed, running the uninstaller...
07-01 20:46 INFO   root: Running the uninstaller...
07-01 20:46 INFO   CommonBackend: This is the uninstaller running
07-01 20:46 DEBUG  WindowsFrontend: __init__...
07-01 20:46 DEBUG  WindowsFrontend: on_init...
07-01 20:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-01 20:46 INFO   root: Received settings
07-01 20:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-01 20:46 DEBUG  TaskList: # Running tasklist...
07-01 20:46 DEBUG  TaskList: ## Running Backup ISO...
07-01 20:46 DEBUG  TaskList: ## Finished Backup ISO
07-01 20:46 DEBUG  TaskList: ## Running Remove bootloader entry...
07-01 20:46 ERROR  WindowsBackend: Cannot find bcdedit
07-01 20:46 DEBUG  WindowsBackend: undo_bootini C:
07-01 20:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6493.09765625 mb free ntfs)
07-01 20:46 DEBUG  WindowsBackend: undo_bootini D:
07-01 20:46 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60153.0664063 mb free ntfs)
07-01 20:46 DEBUG  TaskList: ## Finished Remove bootloader entry
07-01 20:46 DEBUG  TaskList: ## Running Remove target dir...
07-01 20:46 DEBUG  CommonBackend: Deleting D:\ubuntu
07-01 20:46 DEBUG  TaskList: ## Finished Remove target dir
07-01 20:46 DEBUG  TaskList: ## Running Remove registry key...
07-01 20:46 DEBUG  TaskList: ## Finished Remove registry key
07-01 20:46 DEBUG  TaskList: # Finished tasklist
07-01 20:46 INFO   root: Almost finished uninstalling
07-01 20:46 INFO   root: Finished uninstallation
07-01 20:46 DEBUG  CommonBackend: Fetching basic info...
07-01 20:46 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
07-01 20:46 DEBUG  CommonBackend: platform=win32
07-01 20:46 DEBUG  CommonBackend: osname=nt
07-01 20:46 DEBUG  WindowsBackend: arch=amd64
07-01 20:46 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
07-01 20:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-01 20:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-01 20:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-01 20:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-01 20:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-01 20:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-01 20:46 DEBUG  WindowsBackend: Fetching host info...
07-01 20:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-01 20:46 DEBUG  WindowsBackend: windows version=xp
07-01 20:46 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-01 20:46 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-01 20:46 DEBUG  WindowsBackend: windows_build=2600
07-01 20:46 DEBUG  WindowsBackend: gmt=-8
07-01 20:46 DEBUG  WindowsBackend: country=US
07-01 20:46 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-01 20:46 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-01 20:46 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-01 20:46 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-01 20:46 DEBUG  WindowsBackend: windows_language_code=1033
07-01 20:46 DEBUG  WindowsBackend: windows_language=English
07-01 20:46 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-01 20:46 DEBUG  WindowsBackend: bootloader=xp
07-01 20:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6493.0859375 mb free ntfs)
07-01 20:46 DEBUG  WindowsBackend: drive=Drive(C: hd 6493.0859375 mb free ntfs)
07-01 20:46 DEBUG  WindowsBackend: drive=Drive(D: hd 60153.171875 mb free ntfs)
07-01 20:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-01 20:46 DEBUG  WindowsBackend: uninstaller_path=None
07-01 20:46 DEBUG  WindowsBackend: previous_target_dir=None
07-01 20:46 DEBUG  WindowsBackend: previous_distro_name=None
07-01 20:46 DEBUG  WindowsBackend: keyboard_id=67699721
07-01 20:46 DEBUG  WindowsBackend: keyboard_layout=us
07-01 20:46 DEBUG  WindowsBackend: keyboard_variant=
07-01 20:46 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-01 20:46 DEBUG  CommonBackend: Searching ISOs on USB devices
07-01 20:46 DEBUG  CommonBackend: Searching for local CDs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 INFO   root: Running the installer...
07-01 20:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-01 20:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-01 20:46 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
07-01 20:46 INFO   root: Received settings
07-01 20:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-01 20:46 DEBUG  TaskList: # Running tasklist...
07-01 20:46 DEBUG  TaskList: ## Running select_target_dir...
07-01 20:46 INFO   WindowsBackend: Installing into D:\ubuntu
07-01 20:46 DEBUG  TaskList: ## Finished select_target_dir
07-01 20:46 DEBUG  TaskList: ## Running create_dir_structure...
07-01 20:46 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-01 20:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-01 20:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-01 20:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-01 20:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-01 20:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-01 20:46 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-01 20:46 DEBUG  TaskList: ## Finished create_dir_structure
07-01 20:46 DEBUG  TaskList: ## Running uncompress_target_dir...
07-01 20:46 DEBUG  TaskList: ## Finished uncompress_target_dir
07-01 20:46 DEBUG  TaskList: ## Running create_uninstaller...
07-01 20:46 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-01 20:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-01 20:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-01 20:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-01 20:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-01 20:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-01 20:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-01 20:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-01 20:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-01 20:46 DEBUG  TaskList: ## Finished create_uninstaller
07-01 20:46 DEBUG  TaskList: ## Running copy_installation_files...
07-01 20:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-01 20:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\winboot -> D:\ubuntu\winboot
07-01 20:46 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-01 20:46 DEBUG  TaskList: ## Finished copy_installation_files
07-01 20:46 DEBUG  TaskList: ## Running get_iso...
07-01 20:46 DEBUG  CommonBackend: Searching for local CD
07-01 20:46 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 20:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 20:46 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 20:46 DEBUG  CommonBackend: Searching for local ISO
07-01 20:46 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-01 20:46 DEBUG  TaskList: New task get_metalink
07-01 20:46 DEBUG  TaskList: ### Running get_metalink...
07-01 20:46 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
07-01 20:46 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-01 20:46 DEBUG  downloader: download finished (read 7472 bytes)
07-01 20:46 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
07-01 20:46 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-01 20:46 DEBUG  downloader: download finished (read 639 bytes)
07-01 20:46 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-01 20:46 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-01 20:46 DEBUG  downloader: download finished (read 189 bytes)
07-01 20:46 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-01 20:46 INFO   saplog: Checking block bindings..
07-01 20:46 INFO   saplog: Key verified successfully.
07-01 20:46 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

07-01 20:46 DEBUG  TaskList: ### Finished get_metalink
07-01 20:46 DEBUG  TaskList: New task download
07-01 20:46 DEBUG  TaskList: ### Running download...
07-01 20:46 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-01 20:59 INFO   WindowsFrontend: Operation cancelled
07-01 20:59 DEBUG  WindowsFrontend: frontend.quit
07-01 20:59 DEBUG  WindowsFrontend: frontend.on_quit
07-01 20:59 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
07-01 20:59 DEBUG  TaskList: # Cancelling tasklist
07-01 20:59 DEBUG  TaskList: ### Finished download
07-01 20:59 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
07-01 20:59 DEBUG  root: application.on_quit
07-01 20:59 DEBUG  root: Forceful exit
07-01 20:59 INFO   root: sys.exit
07-01 21:01 INFO   root: === wubi 10.04 rev189 ===
07-01 21:01 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
07-01 21:01 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe"']
07-01 21:01 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\data
07-01 21:01 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
07-01 21:01 DEBUG  CommonBackend: Fetching basic info...
07-01 21:01 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
07-01 21:01 DEBUG  CommonBackend: platform=win32
07-01 21:01 DEBUG  CommonBackend: osname=nt
07-01 21:01 DEBUG  CommonBackend: language=en_US
07-01 21:01 DEBUG  CommonBackend: encoding=cp1252
07-01 21:01 DEBUG  WindowsBackend: arch=amd64
07-01 21:01 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
07-01 21:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-01 21:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-01 21:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-01 21:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-01 21:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-01 21:01 DEBUG  WindowsBackend: Fetching host info...
07-01 21:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-01 21:01 DEBUG  WindowsBackend: windows version=xp
07-01 21:01 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-01 21:01 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-01 21:01 DEBUG  WindowsBackend: windows_build=2600
07-01 21:01 DEBUG  WindowsBackend: gmt=-8
07-01 21:01 DEBUG  WindowsBackend: country=US
07-01 21:01 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-01 21:01 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-01 21:01 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-01 21:01 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-01 21:01 DEBUG  WindowsBackend: windows_language_code=1033
07-01 21:01 DEBUG  WindowsBackend: windows_language=English
07-01 21:01 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-01 21:01 DEBUG  WindowsBackend: bootloader=xp
07-01 21:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6490.2265625 mb free ntfs)
07-01 21:01 DEBUG  WindowsBackend: drive=Drive(C: hd 6490.2265625 mb free ntfs)
07-01 21:01 DEBUG  WindowsBackend: drive=Drive(D: hd 60109.640625 mb free ntfs)
07-01 21:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-01 21:01 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-01 21:01 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-01 21:01 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-01 21:01 DEBUG  WindowsBackend: keyboard_id=67699721
07-01 21:01 DEBUG  WindowsBackend: keyboard_layout=us
07-01 21:01 DEBUG  WindowsBackend: keyboard_variant=
07-01 21:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-01 21:01 DEBUG  CommonBackend: locale=en_US.UTF-8
07-01 21:01 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-01 21:01 DEBUG  CommonBackend: Searching ISOs on USB devices
07-01 21:01 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-01 21:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-01 21:01 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  CommonBackend: Searching for local CDs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 INFO   root: Already installed, running the uninstaller...
07-01 21:01 INFO   root: Running the uninstaller...
07-01 21:01 INFO   CommonBackend: This is the uninstaller running
07-01 21:01 DEBUG  WindowsFrontend: __init__...
07-01 21:01 DEBUG  WindowsFrontend: on_init...
07-01 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-01 21:01 INFO   root: Received settings
07-01 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-01 21:01 DEBUG  TaskList: # Running tasklist...
07-01 21:01 DEBUG  TaskList: ## Running Backup ISO...
07-01 21:01 DEBUG  TaskList: ## Finished Backup ISO
07-01 21:01 DEBUG  TaskList: ## Running Remove bootloader entry...
07-01 21:01 ERROR  WindowsBackend: Cannot find bcdedit
07-01 21:01 DEBUG  WindowsBackend: undo_bootini C:
07-01 21:01 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6490.2265625 mb free ntfs)
07-01 21:01 DEBUG  WindowsBackend: undo_bootini D:
07-01 21:01 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60109.640625 mb free ntfs)
07-01 21:01 DEBUG  TaskList: ## Finished Remove bootloader entry
07-01 21:01 DEBUG  TaskList: ## Running Remove target dir...
07-01 21:01 DEBUG  CommonBackend: Deleting D:\ubuntu
07-01 21:01 DEBUG  TaskList: ## Finished Remove target dir
07-01 21:01 DEBUG  TaskList: ## Running Remove registry key...
07-01 21:01 DEBUG  TaskList: ## Finished Remove registry key
07-01 21:01 DEBUG  TaskList: # Finished tasklist
07-01 21:01 INFO   root: Almost finished uninstalling
07-01 21:01 INFO   root: Finished uninstallation
07-01 21:01 DEBUG  CommonBackend: Fetching basic info...
07-01 21:01 DEBUG  CommonBackend: original_exe=C:\ubuntu-10.04-desktop-i386\wubi.exe
07-01 21:01 DEBUG  CommonBackend: platform=win32
07-01 21:01 DEBUG  CommonBackend: osname=nt
07-01 21:01 DEBUG  WindowsBackend: arch=amd64
07-01 21:01 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
07-01 21:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-01 21:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-01 21:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-01 21:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-01 21:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-01 21:01 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-01 21:01 DEBUG  WindowsBackend: Fetching host info...
07-01 21:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-01 21:01 DEBUG  WindowsBackend: windows version=xp
07-01 21:01 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-01 21:01 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-01 21:01 DEBUG  WindowsBackend: windows_build=2600
07-01 21:01 DEBUG  WindowsBackend: gmt=-8
07-01 21:01 DEBUG  WindowsBackend: country=US
07-01 21:01 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-01 21:01 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-01 21:01 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-01 21:01 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-01 21:01 DEBUG  WindowsBackend: windows_language_code=1033
07-01 21:01 DEBUG  WindowsBackend: windows_language=English
07-01 21:01 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-01 21:01 DEBUG  WindowsBackend: bootloader=xp
07-01 21:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6490.19140625 mb free ntfs)
07-01 21:01 DEBUG  WindowsBackend: drive=Drive(C: hd 6490.19140625 mb free ntfs)
07-01 21:01 DEBUG  WindowsBackend: drive=Drive(D: hd 60153.171875 mb free ntfs)
07-01 21:01 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-01 21:01 DEBUG  WindowsBackend: uninstaller_path=None
07-01 21:01 DEBUG  WindowsBackend: previous_target_dir=None
07-01 21:01 DEBUG  WindowsBackend: previous_distro_name=None
07-01 21:01 DEBUG  WindowsBackend: keyboard_id=67699721
07-01 21:01 DEBUG  WindowsBackend: keyboard_layout=us
07-01 21:01 DEBUG  WindowsBackend: keyboard_variant=
07-01 21:01 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-01 21:01 DEBUG  CommonBackend: Checking pre-specified ISO E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  CommonBackend: Searching for local CDs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 21:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 21:01 INFO   root: Running the installer...
07-01 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-01 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-01 21:01 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
07-01 21:01 INFO   root: Received settings
07-01 21:01 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-01 21:01 DEBUG  TaskList: # Running tasklist...
07-01 21:01 DEBUG  TaskList: ## Running select_target_dir...
07-01 21:01 INFO   WindowsBackend: Installing into D:\ubuntu
07-01 21:01 DEBUG  TaskList: ## Finished select_target_dir
07-01 21:01 DEBUG  TaskList: ## Running create_dir_structure...
07-01 21:01 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-01 21:01 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-01 21:01 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-01 21:01 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-01 21:01 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-01 21:01 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-01 21:01 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-01 21:01 DEBUG  TaskList: ## Finished create_dir_structure
07-01 21:01 DEBUG  TaskList: ## Running uncompress_target_dir...
07-01 21:01 DEBUG  TaskList: ## Finished uncompress_target_dir
07-01 21:01 DEBUG  TaskList: ## Running create_uninstaller...
07-01 21:01 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-10.04-desktop-i386\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-01 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-01 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-01 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-01 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-01 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-01 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-01 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-01 21:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-01 21:01 DEBUG  TaskList: ## Finished create_uninstaller
07-01 21:01 DEBUG  TaskList: ## Running copy_installation_files...
07-01 21:01 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-01 21:01 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\winboot -> D:\ubuntu\winboot
07-01 21:01 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-01 21:01 DEBUG  TaskList: ## Finished copy_installation_files
07-01 21:01 DEBUG  TaskList: ## Running get_iso...
07-01 21:01 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  TaskList: New task is_valid_iso
07-01 21:01 DEBUG  TaskList: ### Running is_valid_iso...
07-01 21:01 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  TaskList: ### Finished is_valid_iso
07-01 21:01 DEBUG  TaskList: New task check_iso
07-01 21:01 DEBUG  TaskList: ### Running check_iso...
07-01 21:01 DEBUG  CommonBackend: Checking E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
07-01 21:01 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
07-01 21:01 DEBUG  TaskList: New task get_metalink
07-01 21:01 DEBUG  TaskList: #### Running get_metalink...
07-01 21:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > D:\ubuntu\install
07-01 21:01 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink, basename=ubuntu-10.04-desktop-i386.metalink, length=7420, text=None
07-01 21:01 DEBUG  downloader: download finished (read 7420 bytes)
07-01 21:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
07-01 21:01 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-01 21:01 DEBUG  downloader: download finished (read 639 bytes)
07-01 21:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-01 21:01 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-01 21:01 DEBUG  downloader: download finished (read 189 bytes)
07-01 21:01 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-01 21:01 INFO   saplog: Checking block bindings..
07-01 21:01 INFO   saplog: Key verified successfully.
07-01 21:01 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

07-01 21:01 DEBUG  TaskList: #### Finished get_metalink
07-01 21:01 DEBUG  TaskList: New task get_file_md5
07-01 21:01 DEBUG  TaskList: #### Running get_file_md5...
07-01 21:20 DEBUG  TaskList: #### Finished get_file_md5
07-01 21:20 DEBUG  TaskList: ### Finished check_iso
07-01 21:20 DEBUG  TaskList: New task copy_file
07-01 21:20 DEBUG  CommonBackend: Copying E:\ubuntu-10.04-desktop-i386.iso > D:\ubuntu\install\installation.iso
07-01 21:20 DEBUG  TaskList: ### Running copy_file...
07-01 21:35 DEBUG  TaskList: ### Finished copy_file
07-01 21:35 DEBUG  TaskList: ## Finished get_iso
07-01 21:35 DEBUG  TaskList: ## Running extract_kernel...
07-01 21:35 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
07-01 21:35 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
07-01 21:35 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
07-01 21:35 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
07-01 21:35 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-01 21:35 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
07-01 21:35 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
07-01 21:35 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
07-01 21:35 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
07-01 21:35 DEBUG  TaskList: ## Finished extract_kernel
07-01 21:35 DEBUG  TaskList: ## Running choose_disk_sizes...
07-01 21:35 DEBUG  WindowsBackend: total size=3000
  root=2744
  swap=256
  home=0
  usr=0
07-01 21:35 DEBUG  TaskList: ## Finished choose_disk_sizes
07-01 21:35 DEBUG  TaskList: ## Running create_preseed...
07-01 21:35 DEBUG  TaskList: ## Finished create_preseed
07-01 21:35 DEBUG  TaskList: ## Running modify_bootloader...
07-01 21:35 DEBUG  TaskList: New task modify_bootini
07-01 21:35 DEBUG  TaskList: ### Running modify_bootini...
07-01 21:35 DEBUG  WindowsBackend: modify_bootini C:
07-01 21:35 DEBUG  TaskList: ### Finished modify_bootini
07-01 21:35 DEBUG  TaskList: New task modify_bootini
07-01 21:35 DEBUG  TaskList: ### Running modify_bootini...
07-01 21:35 DEBUG  WindowsBackend: modify_bootini D:
07-01 21:35 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
07-01 21:35 DEBUG  TaskList: ### Finished modify_bootini
07-01 21:35 DEBUG  TaskList: ## Finished modify_bootloader
07-01 21:35 DEBUG  TaskList: ## Running modify_grub_configuration...
07-01 21:35 DEBUG  TaskList: ## Finished modify_grub_configuration
07-01 21:35 DEBUG  TaskList: ## Running create_virtual_disks...
07-01 21:35 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 2744MB
07-01 21:35 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
07-01 21:35 DEBUG  TaskList: ## Finished create_virtual_disks
07-01 21:35 DEBUG  TaskList: ## Running uncompress_files...
07-01 21:35 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
07-01 21:35 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
07-01 21:35 DEBUG  TaskList: ## Finished uncompress_files
07-01 21:35 DEBUG  TaskList: ## Running eject_cd...
07-01 21:35 DEBUG  TaskList: ## Finished eject_cd
07-01 21:35 DEBUG  TaskList: # Finished tasklist
07-01 21:35 INFO   root: Almost finished installing
07-01 21:35 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
07-01 21:40 INFO   root: Finished installation
07-01 21:40 INFO   root: Rebooting
07-01 21:40 DEBUG  TaskList: # Running tasklist...
07-01 21:40 DEBUG  TaskList: ## Running reboot...
07-01 21:40 DEBUG  TaskList: ## Finished reboot
07-01 21:40 DEBUG  TaskList: # Finished tasklist
07-01 21:40 DEBUG  root: application.quit
07-01 21:40 DEBUG  WindowsFrontend: frontend.quit
07-01 21:40 DEBUG  WindowsFrontend: frontend.on_quit
07-01 21:40 DEBUG  root: application.on_quit
07-01 21:40 INFO   root: sys.exit
07-01 09:31 INFO   root: === wubi 10.04 rev189 ===
07-01 09:31 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
07-01 09:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-01 09:31 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data
07-01 09:31 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
07-01 09:31 DEBUG  CommonBackend: Fetching basic info...
07-01 09:31 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-01 09:31 DEBUG  CommonBackend: platform=win32
07-01 09:31 DEBUG  CommonBackend: osname=nt
07-01 09:31 DEBUG  CommonBackend: language=en_US
07-01 09:31 DEBUG  CommonBackend: encoding=cp1252
07-01 09:31 DEBUG  WindowsBackend: arch=amd64
07-01 09:31 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
07-01 09:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-01 09:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-01 09:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-01 09:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-01 09:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-01 09:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-01 09:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-01 09:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-01 09:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-01 09:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-01 09:31 DEBUG  WindowsBackend: Fetching host info...
07-01 09:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-01 09:31 DEBUG  WindowsBackend: windows version=xp
07-01 09:31 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-01 09:31 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-01 09:31 DEBUG  WindowsBackend: windows_build=2600
07-01 09:31 DEBUG  WindowsBackend: gmt=-8
07-01 09:31 DEBUG  WindowsBackend: country=US
07-01 09:31 DEBUG  WindowsBackend: timezone=America/Los_Angeles
07-01 09:31 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-01 09:31 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-01 09:31 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-01 09:31 DEBUG  WindowsBackend: windows_language_code=1033
07-01 09:31 DEBUG  WindowsBackend: windows_language=English
07-01 09:31 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-01 09:31 DEBUG  WindowsBackend: bootloader=xp
07-01 09:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6476.39453125 mb free ntfs)
07-01 09:31 DEBUG  WindowsBackend: drive=Drive(C: hd 6476.39453125 mb free ntfs)
07-01 09:31 DEBUG  WindowsBackend: drive=Drive(D: hd 56476.2617188 mb free ntfs)
07-01 09:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-01 09:31 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-01 09:31 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-01 09:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-01 09:31 DEBUG  WindowsBackend: keyboard_id=67699721
07-01 09:31 DEBUG  WindowsBackend: keyboard_layout=us
07-01 09:31 DEBUG  WindowsBackend: keyboard_variant=
07-01 09:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-01 09:31 DEBUG  CommonBackend: locale=en_US.UTF-8
07-01 09:31 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-01 09:31 DEBUG  CommonBackend: Searching ISOs on USB devices
07-01 09:31 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04-desktop-i386.iso
07-01 09:31 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04-desktop-i386.iso
07-01 09:31 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-01 09:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-01 09:31 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04-desktop-i386.iso
07-01 09:31 DEBUG  CommonBackend: Searching for local CDs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-01 09:31 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-01 09:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-01 09:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-01 09:31 INFO   root: Running the uninstaller...
07-01 09:31 INFO   CommonBackend: This is the uninstaller running
07-01 09:31 DEBUG  WindowsFrontend: __init__...
07-01 09:31 DEBUG  WindowsFrontend: on_init...
07-01 09:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-01 09:31 INFO   root: Received settings
07-01 09:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-01 09:31 DEBUG  TaskList: # Running tasklist...
07-01 09:31 DEBUG  TaskList: ## Running Backup ISO...
07-01 09:31 DEBUG  TaskList: ## Finished Backup ISO
07-01 09:31 DEBUG  TaskList: ## Running Remove bootloader entry...
07-01 09:31 ERROR  WindowsBackend: Cannot find bcdedit
07-01 09:31 DEBUG  WindowsBackend: undo_bootini C:
07-01 09:31 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6476.39453125 mb free ntfs)
07-01 09:31 DEBUG  WindowsBackend: undo_bootini D:
07-01 09:31 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 56476.2617188 mb free ntfs)
07-01 09:31 DEBUG  TaskList: ## Finished Remove bootloader entry
07-01 09:31 DEBUG  TaskList: ## Running Remove target dir...
07-01 09:31 DEBUG  CommonBackend: Deleting D:\ubuntu
07-01 09:31 DEBUG  TaskList: ## Finished Remove target dir
07-01 09:31 DEBUG  TaskList: ## Running Remove registry key...
07-01 09:31 DEBUG  TaskList: ## Finished Remove registry key
07-01 09:31 DEBUG  TaskList: # Finished tasklist
07-01 09:31 INFO   root: Almost finished uninstalling
07-01 09:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-01 09:31 INFO   root: Finished uninstallation
07-01 09:31 DEBUG  root: application.quit
07-01 09:31 DEBUG  WindowsFrontend: frontend.quit
07-01 09:31 DEBUG  WindowsFrontend: frontend.on_quit
07-01 09:31 DEBUG  root: application.on_quit
07-01 09:31 INFO   root: sys.exit
07-03 21:51 INFO   root: === wubi 10.04 rev189 ===
07-03 21:51 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
07-03 21:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
07-03 21:51 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data
07-03 21:51 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
07-03 21:51 DEBUG  CommonBackend: Fetching basic info...
07-03 21:51 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-03 21:51 DEBUG  CommonBackend: platform=win32
07-03 21:51 DEBUG  CommonBackend: osname=nt
07-03 21:51 DEBUG  CommonBackend: language=en_US
07-03 21:51 DEBUG  CommonBackend: encoding=cp1252
07-03 21:51 DEBUG  WindowsBackend: arch=amd64
07-03 21:51 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
07-03 21:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 21:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 21:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 21:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 21:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 21:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 21:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 21:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 21:51 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-03 21:51 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 21:51 DEBUG  WindowsBackend: Fetching host info...
07-03 21:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 21:51 DEBUG  WindowsBackend: windows version=xp
07-03 21:51 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-03 21:51 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-03 21:51 DEBUG  WindowsBackend: windows_build=2600
07-03 21:51 DEBUG  WindowsBackend: gmt=5
07-03 21:51 DEBUG  WindowsBackend: country=US
07-03 21:51 DEBUG  WindowsBackend: timezone=America/New_York
07-03 21:51 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-03 21:51 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-03 21:51 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-03 21:51 DEBUG  WindowsBackend: windows_language_code=1033
07-03 21:51 DEBUG  WindowsBackend: windows_language=English
07-03 21:51 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-03 21:51 DEBUG  WindowsBackend: bootloader=xp
07-03 21:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6345.26953125 mb free ntfs)
07-03 21:51 DEBUG  WindowsBackend: drive=Drive(C: hd 6345.26953125 mb free ntfs)
07-03 21:51 DEBUG  WindowsBackend: drive=Drive(D: hd 60175.796875 mb free ntfs)
07-03 21:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-03 21:51 DEBUG  WindowsBackend: uninstaller_path=None
07-03 21:51 DEBUG  WindowsBackend: previous_target_dir=None
07-03 21:51 DEBUG  WindowsBackend: previous_distro_name=None
07-03 21:51 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 21:51 DEBUG  WindowsBackend: keyboard_layout=us
07-03 21:51 DEBUG  WindowsBackend: keyboard_variant=
07-03 21:51 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 21:51 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 21:51 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-03 21:51 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 21:51 DEBUG  CommonBackend: Searching for local CDs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-03 21:51 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 21:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 21:51 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-03 21:51 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-03 21:51 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-03 21:51 INFO   root: Running the CD menu...
07-03 21:51 DEBUG  WindowsFrontend: __init__...
07-03 21:51 DEBUG  WindowsFrontend: on_init...
07-03 21:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 21:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 21:51 INFO   root: CD menu finished
07-03 21:51 INFO   root: Running the installer...
07-03 21:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 21:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 21:51 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
07-03 21:51 INFO   root: Received settings
07-03 21:51 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 21:51 DEBUG  TaskList: # Running tasklist...
07-03 21:51 DEBUG  TaskList: ## Running select_target_dir...
07-03 21:51 INFO   WindowsBackend: Installing into D:\ubuntu
07-03 21:51 DEBUG  TaskList: ## Finished select_target_dir
07-03 21:51 DEBUG  TaskList: ## Running create_dir_structure...
07-03 21:51 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-03 21:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-03 21:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-03 21:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-03 21:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-03 21:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-03 21:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-03 21:51 DEBUG  TaskList: ## Finished create_dir_structure
07-03 21:51 DEBUG  TaskList: ## Running uncompress_target_dir...
07-03 21:51 DEBUG  TaskList: ## Finished uncompress_target_dir
07-03 21:51 DEBUG  TaskList: ## Running create_uninstaller...
07-03 21:51 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-03 21:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-03 21:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-03 21:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 21:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-03 21:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-03 21:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 21:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 21:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 21:51 DEBUG  TaskList: ## Finished create_uninstaller
07-03 21:51 DEBUG  TaskList: ## Running copy_installation_files...
07-03 21:51 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-03 21:51 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\winboot -> D:\ubuntu\winboot
07-03 21:51 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-03 21:51 DEBUG  TaskList: ## Finished copy_installation_files
07-03 21:51 DEBUG  TaskList: ## Running get_iso...
07-03 21:51 DEBUG  TaskList: New task copy_file
07-03 21:51 DEBUG  TaskList: ### Running copy_file...
07-03 21:53 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
07-03 21:53 DEBUG  TaskList: # Cancelling tasklist
07-03 21:53 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
07-03 21:53 DEBUG  TaskList: New task check_iso
07-03 21:53 DEBUG  CommonBackend: Searching for local ISO
07-03 21:53 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-03 21:53 DEBUG  TaskList: New task get_metalink
07-03 21:53 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 21:53 DEBUG  TaskList: # Cancelling tasklist
07-03 21:53 DEBUG  TaskList: # Finished tasklist
07-03 21:54 INFO   root: === wubi 10.04 rev189 ===
07-03 21:54 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
07-03 21:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
07-03 21:54 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\data
07-03 21:54 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\bin\7z.exe
07-03 21:54 DEBUG  CommonBackend: Fetching basic info...
07-03 21:54 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-03 21:54 DEBUG  CommonBackend: platform=win32
07-03 21:54 DEBUG  CommonBackend: osname=nt
07-03 21:54 DEBUG  CommonBackend: language=en_US
07-03 21:54 DEBUG  CommonBackend: encoding=cp1252
07-03 21:54 DEBUG  WindowsBackend: arch=amd64
07-03 21:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
07-03 21:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 21:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 21:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 21:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 21:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 21:54 DEBUG  WindowsBackend: Fetching host info...
07-03 21:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 21:54 DEBUG  WindowsBackend: windows version=xp
07-03 21:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-03 21:54 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-03 21:54 DEBUG  WindowsBackend: windows_build=2600
07-03 21:54 DEBUG  WindowsBackend: gmt=5
07-03 21:54 DEBUG  WindowsBackend: country=US
07-03 21:54 DEBUG  WindowsBackend: timezone=America/New_York
07-03 21:54 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-03 21:54 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-03 21:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-03 21:54 DEBUG  WindowsBackend: windows_language_code=1033
07-03 21:54 DEBUG  WindowsBackend: windows_language=English
07-03 21:54 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-03 21:54 DEBUG  WindowsBackend: bootloader=xp
07-03 21:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6345.234375 mb free ntfs)
07-03 21:54 DEBUG  WindowsBackend: drive=Drive(C: hd 6345.234375 mb free ntfs)
07-03 21:54 DEBUG  WindowsBackend: drive=Drive(D: hd 59916.2617188 mb free ntfs)
07-03 21:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-03 21:54 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-03 21:54 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-03 21:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-03 21:54 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 21:54 DEBUG  WindowsBackend: keyboard_layout=us
07-03 21:54 DEBUG  WindowsBackend: keyboard_variant=
07-03 21:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 21:54 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 21:54 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-03 21:54 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 21:54 DEBUG  CommonBackend: Searching for local CDs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu Netbook CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-03 21:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-03 21:54 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-03 21:54 INFO   root: Running the CD menu...
07-03 21:54 DEBUG  WindowsFrontend: __init__...
07-03 21:54 DEBUG  WindowsFrontend: on_init...
07-03 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
07-03 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
07-03 21:54 INFO   root: CD menu finished
07-03 21:54 INFO   root: Already installed, running the uninstaller...
07-03 21:54 INFO   root: Running the uninstaller...
07-03 21:54 INFO   CommonBackend: This is the uninstaller running
07-03 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
07-03 21:54 INFO   root: Received settings
07-03 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
07-03 21:54 DEBUG  TaskList: # Running tasklist...
07-03 21:54 DEBUG  TaskList: ## Running Backup ISO...
07-03 21:54 DEBUG  TaskList: ## Finished Backup ISO
07-03 21:54 DEBUG  TaskList: ## Running Remove bootloader entry...
07-03 21:54 ERROR  WindowsBackend: Cannot find bcdedit
07-03 21:54 DEBUG  WindowsBackend: undo_bootini C:
07-03 21:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6345.234375 mb free ntfs)
07-03 21:54 DEBUG  WindowsBackend: undo_bootini D:
07-03 21:54 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 59916.2617188 mb free ntfs)
07-03 21:54 DEBUG  TaskList: ## Finished Remove bootloader entry
07-03 21:54 DEBUG  TaskList: ## Running Remove target dir...
07-03 21:54 DEBUG  CommonBackend: Deleting D:\ubuntu
07-03 21:54 DEBUG  TaskList: ## Finished Remove target dir
07-03 21:54 DEBUG  TaskList: ## Running Remove registry key...
07-03 21:54 DEBUG  TaskList: ## Finished Remove registry key
07-03 21:54 DEBUG  TaskList: # Finished tasklist
07-03 21:54 INFO   root: Almost finished uninstalling
07-03 21:54 INFO   root: Finished uninstallation
07-03 21:54 DEBUG  CommonBackend: Fetching basic info...
07-03 21:54 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-03 21:54 DEBUG  CommonBackend: platform=win32
07-03 21:54 DEBUG  CommonBackend: osname=nt
07-03 21:54 DEBUG  WindowsBackend: arch=amd64
07-03 21:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\data\isolist.ini
07-03 21:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 21:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 21:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 21:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 21:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-03 21:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 21:54 DEBUG  WindowsBackend: Fetching host info...
07-03 21:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 21:54 DEBUG  WindowsBackend: windows version=xp
07-03 21:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-03 21:54 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-03 21:54 DEBUG  WindowsBackend: windows_build=2600
07-03 21:54 DEBUG  WindowsBackend: gmt=5
07-03 21:54 DEBUG  WindowsBackend: country=US
07-03 21:54 DEBUG  WindowsBackend: timezone=America/New_York
07-03 21:54 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-03 21:54 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-03 21:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-03 21:54 DEBUG  WindowsBackend: windows_language_code=1033
07-03 21:54 DEBUG  WindowsBackend: windows_language=English
07-03 21:54 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-03 21:54 DEBUG  WindowsBackend: bootloader=xp
07-03 21:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6345.22265625 mb free ntfs)
07-03 21:54 DEBUG  WindowsBackend: drive=Drive(C: hd 6345.22265625 mb free ntfs)
07-03 21:54 DEBUG  WindowsBackend: drive=Drive(D: hd 60175.7773438 mb free ntfs)
07-03 21:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-03 21:54 DEBUG  WindowsBackend: uninstaller_path=None
07-03 21:54 DEBUG  WindowsBackend: previous_target_dir=None
07-03 21:54 DEBUG  WindowsBackend: previous_distro_name=None
07-03 21:54 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 21:54 DEBUG  WindowsBackend: keyboard_layout=us
07-03 21:54 DEBUG  WindowsBackend: keyboard_variant=
07-03 21:54 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-03 21:54 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 21:54 DEBUG  CommonBackend: Searching for local CDs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Ubuntu Netbook CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Kubuntu Netbook CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Xubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp is a valid Mythbuntu CD
07-03 21:54 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 21:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 21:54 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-03 21:54 INFO   root: Running the installer...
07-03 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
07-03 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
07-03 21:54 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=4000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
07-03 21:54 INFO   root: Received settings
07-03 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\translations, languages=['en_US', 'en']
07-03 21:54 DEBUG  TaskList: # Running tasklist...
07-03 21:54 DEBUG  TaskList: ## Running select_target_dir...
07-03 21:54 INFO   WindowsBackend: Installing into D:\ubuntu
07-03 21:54 DEBUG  TaskList: ## Finished select_target_dir
07-03 21:54 DEBUG  TaskList: ## Running create_dir_structure...
07-03 21:54 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-03 21:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-03 21:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-03 21:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-03 21:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-03 21:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-03 21:54 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-03 21:54 DEBUG  TaskList: ## Finished create_dir_structure
07-03 21:54 DEBUG  TaskList: ## Running uncompress_target_dir...
07-03 21:54 DEBUG  TaskList: ## Finished uncompress_target_dir
07-03 21:54 DEBUG  TaskList: ## Running create_uninstaller...
07-03 21:54 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-03 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-03 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-03 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-03 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-03 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 21:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 21:54 DEBUG  TaskList: ## Finished create_uninstaller
07-03 21:54 DEBUG  TaskList: ## Running copy_installation_files...
07-03 21:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-03 21:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\winboot -> D:\ubuntu\winboot
07-03 21:54 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl4.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-03 21:54 DEBUG  TaskList: ## Finished copy_installation_files
07-03 21:54 DEBUG  TaskList: ## Running get_iso...
07-03 21:54 DEBUG  TaskList: New task copy_file
07-03 21:54 DEBUG  TaskList: ### Running copy_file...
07-03 21:57 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
07-03 21:57 DEBUG  TaskList: # Cancelling tasklist
07-03 21:57 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
07-03 21:57 DEBUG  TaskList: New task check_iso
07-03 21:57 DEBUG  CommonBackend: Searching for local ISO
07-03 21:57 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-03 21:57 DEBUG  TaskList: New task get_metalink
07-03 21:57 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 21:57 DEBUG  TaskList: # Cancelling tasklist
07-03 21:57 DEBUG  TaskList: # Finished tasklist
07-03 22:05 INFO   root: === wubi 10.04 rev189 ===
07-03 22:05 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
07-03 22:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
07-03 22:05 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data
07-03 22:05 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
07-03 22:05 DEBUG  CommonBackend: Fetching basic info...
07-03 22:05 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-03 22:05 DEBUG  CommonBackend: platform=win32
07-03 22:05 DEBUG  CommonBackend: osname=nt
07-03 22:05 DEBUG  CommonBackend: language=en_US
07-03 22:05 DEBUG  CommonBackend: encoding=cp1252
07-03 22:05 DEBUG  WindowsBackend: arch=amd64
07-03 22:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
07-03 22:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 22:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 22:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 22:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 22:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 22:05 DEBUG  WindowsBackend: Fetching host info...
07-03 22:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 22:05 DEBUG  WindowsBackend: windows version=xp
07-03 22:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-03 22:05 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-03 22:05 DEBUG  WindowsBackend: windows_build=2600
07-03 22:05 DEBUG  WindowsBackend: gmt=5
07-03 22:05 DEBUG  WindowsBackend: country=US
07-03 22:05 DEBUG  WindowsBackend: timezone=America/New_York
07-03 22:05 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-03 22:05 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-03 22:05 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-03 22:05 DEBUG  WindowsBackend: windows_language_code=1033
07-03 22:05 DEBUG  WindowsBackend: windows_language=English
07-03 22:05 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-03 22:05 DEBUG  WindowsBackend: bootloader=xp
07-03 22:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6344.4453125 mb free ntfs)
07-03 22:05 DEBUG  WindowsBackend: drive=Drive(C: hd 6344.4453125 mb free ntfs)
07-03 22:05 DEBUG  WindowsBackend: drive=Drive(D: hd 59910.265625 mb free ntfs)
07-03 22:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-03 22:05 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-03 22:05 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-03 22:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-03 22:05 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 22:05 DEBUG  WindowsBackend: keyboard_layout=us
07-03 22:05 DEBUG  WindowsBackend: keyboard_variant=
07-03 22:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 22:05 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 22:05 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-03 22:05 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 22:05 DEBUG  CommonBackend: Searching for local CDs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-03 22:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-03 22:05 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-03 22:05 INFO   root: Running the CD menu...
07-03 22:05 DEBUG  WindowsFrontend: __init__...
07-03 22:05 DEBUG  WindowsFrontend: on_init...
07-03 22:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 22:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 22:05 INFO   root: CD menu finished
07-03 22:05 INFO   root: Already installed, running the uninstaller...
07-03 22:05 INFO   root: Running the uninstaller...
07-03 22:05 INFO   CommonBackend: This is the uninstaller running
07-03 22:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 22:05 INFO   root: Received settings
07-03 22:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 22:05 DEBUG  TaskList: # Running tasklist...
07-03 22:05 DEBUG  TaskList: ## Running Backup ISO...
07-03 22:05 DEBUG  TaskList: ## Finished Backup ISO
07-03 22:05 DEBUG  TaskList: ## Running Remove bootloader entry...
07-03 22:05 ERROR  WindowsBackend: Cannot find bcdedit
07-03 22:05 DEBUG  WindowsBackend: undo_bootini C:
07-03 22:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6344.4453125 mb free ntfs)
07-03 22:05 DEBUG  WindowsBackend: undo_bootini D:
07-03 22:05 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 59910.265625 mb free ntfs)
07-03 22:05 DEBUG  TaskList: ## Finished Remove bootloader entry
07-03 22:05 DEBUG  TaskList: ## Running Remove target dir...
07-03 22:05 DEBUG  CommonBackend: Deleting D:\ubuntu
07-03 22:05 DEBUG  TaskList: ## Finished Remove target dir
07-03 22:05 DEBUG  TaskList: ## Running Remove registry key...
07-03 22:05 DEBUG  TaskList: ## Finished Remove registry key
07-03 22:05 DEBUG  TaskList: # Finished tasklist
07-03 22:05 INFO   root: Almost finished uninstalling
07-03 22:05 INFO   root: Finished uninstallation
07-03 22:05 DEBUG  CommonBackend: Fetching basic info...
07-03 22:05 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-03 22:05 DEBUG  CommonBackend: platform=win32
07-03 22:05 DEBUG  CommonBackend: osname=nt
07-03 22:05 DEBUG  WindowsBackend: arch=amd64
07-03 22:05 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
07-03 22:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 22:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 22:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 22:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 22:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-03 22:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 22:05 DEBUG  WindowsBackend: Fetching host info...
07-03 22:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 22:05 DEBUG  WindowsBackend: windows version=xp
07-03 22:05 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-03 22:05 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-03 22:05 DEBUG  WindowsBackend: windows_build=2600
07-03 22:05 DEBUG  WindowsBackend: gmt=5
07-03 22:05 DEBUG  WindowsBackend: country=US
07-03 22:05 DEBUG  WindowsBackend: timezone=America/New_York
07-03 22:05 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-03 22:05 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-03 22:05 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-03 22:05 DEBUG  WindowsBackend: windows_language_code=1033
07-03 22:05 DEBUG  WindowsBackend: windows_language=English
07-03 22:05 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-03 22:05 DEBUG  WindowsBackend: bootloader=xp
07-03 22:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6344.43359375 mb free ntfs)
07-03 22:05 DEBUG  WindowsBackend: drive=Drive(C: hd 6344.43359375 mb free ntfs)
07-03 22:05 DEBUG  WindowsBackend: drive=Drive(D: hd 60174.3554688 mb free ntfs)
07-03 22:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-03 22:05 DEBUG  WindowsBackend: uninstaller_path=None
07-03 22:05 DEBUG  WindowsBackend: previous_target_dir=None
07-03 22:05 DEBUG  WindowsBackend: previous_distro_name=None
07-03 22:05 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 22:05 DEBUG  WindowsBackend: keyboard_layout=us
07-03 22:05 DEBUG  WindowsBackend: keyboard_variant=
07-03 22:05 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-03 22:05 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 22:05 DEBUG  CommonBackend: Searching for local CDs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu Netbook CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
07-03 22:05 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 22:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 22:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 22:05 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-03 22:05 INFO   root: Running the installer...
07-03 22:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 22:05 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 22:06 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
07-03 22:06 INFO   root: Received settings
07-03 22:06 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
07-03 22:06 DEBUG  TaskList: # Running tasklist...
07-03 22:06 DEBUG  TaskList: ## Running select_target_dir...
07-03 22:06 INFO   WindowsBackend: Installing into D:\ubuntu
07-03 22:06 DEBUG  TaskList: ## Finished select_target_dir
07-03 22:06 DEBUG  TaskList: ## Running create_dir_structure...
07-03 22:06 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-03 22:06 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-03 22:06 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-03 22:06 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-03 22:06 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-03 22:06 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-03 22:06 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-03 22:06 DEBUG  TaskList: ## Finished create_dir_structure
07-03 22:06 DEBUG  TaskList: ## Running uncompress_target_dir...
07-03 22:06 DEBUG  TaskList: ## Finished uncompress_target_dir
07-03 22:06 DEBUG  TaskList: ## Running create_uninstaller...
07-03 22:06 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-03 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-03 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-03 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-03 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-03 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 22:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 22:06 DEBUG  TaskList: ## Finished create_uninstaller
07-03 22:06 DEBUG  TaskList: ## Running copy_installation_files...
07-03 22:06 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-03 22:06 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\winboot -> D:\ubuntu\winboot
07-03 22:06 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl1.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-03 22:06 DEBUG  TaskList: ## Finished copy_installation_files
07-03 22:06 DEBUG  TaskList: ## Running get_iso...
07-03 22:06 DEBUG  TaskList: New task copy_file
07-03 22:06 DEBUG  TaskList: ### Running copy_file...
07-03 22:10 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
07-03 22:10 DEBUG  TaskList: # Cancelling tasklist
07-03 22:10 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
07-03 22:10 DEBUG  TaskList: New task check_iso
07-03 22:10 DEBUG  CommonBackend: Searching for local ISO
07-03 22:10 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-03 22:10 DEBUG  TaskList: New task get_metalink
07-03 22:10 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 22:10 DEBUG  TaskList: # Cancelling tasklist
07-03 22:10 DEBUG  TaskList: # Finished tasklist
07-10 20:36 INFO   root: === wubi 10.04 rev189 ===
07-10 20:36 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
07-10 20:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
07-10 20:36 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\data
07-10 20:36 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\bin\7z.exe
07-10 20:36 DEBUG  CommonBackend: Fetching basic info...
07-10 20:36 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-10 20:36 DEBUG  CommonBackend: platform=win32
07-10 20:36 DEBUG  CommonBackend: osname=nt
07-10 20:36 DEBUG  CommonBackend: language=en_US
07-10 20:36 DEBUG  CommonBackend: encoding=cp1252
07-10 20:36 DEBUG  WindowsBackend: arch=amd64
07-10 20:36 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini
07-10 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-10 20:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-10 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-10 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-10 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-10 20:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-10 20:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-10 20:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-10 20:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-10 20:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-10 20:36 DEBUG  WindowsBackend: Fetching host info...
07-10 20:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-10 20:36 DEBUG  WindowsBackend: windows version=xp
07-10 20:36 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-10 20:36 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-10 20:36 DEBUG  WindowsBackend: windows_build=2600
07-10 20:36 DEBUG  WindowsBackend: gmt=5
07-10 20:36 DEBUG  WindowsBackend: country=US
07-10 20:36 DEBUG  WindowsBackend: timezone=America/New_York
07-10 20:36 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-10 20:36 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-10 20:36 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-10 20:36 DEBUG  WindowsBackend: windows_language_code=1033
07-10 20:36 DEBUG  WindowsBackend: windows_language=English
07-10 20:36 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-10 20:36 DEBUG  WindowsBackend: bootloader=xp
07-10 20:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6020.7578125 mb free ntfs)
07-10 20:36 DEBUG  WindowsBackend: drive=Drive(C: hd 6020.7578125 mb free ntfs)
07-10 20:36 DEBUG  WindowsBackend: drive=Drive(D: hd 59645.71875 mb free ntfs)
07-10 20:36 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-10 20:36 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-10 20:36 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-10 20:36 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-10 20:36 DEBUG  WindowsBackend: keyboard_id=67699721
07-10 20:36 DEBUG  WindowsBackend: keyboard_layout=us
07-10 20:36 DEBUG  WindowsBackend: keyboard_variant=
07-10 20:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-10 20:36 DEBUG  CommonBackend: locale=en_US.UTF-8
07-10 20:36 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-10 20:36 DEBUG  CommonBackend: Searching ISOs on USB devices
07-10 20:36 DEBUG  CommonBackend: Searching for local CDs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
07-10 20:36 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-10 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-10 20:36 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-10 20:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-10 20:36 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-10 20:36 INFO   root: Running the CD menu...
07-10 20:36 DEBUG  WindowsFrontend: __init__...
07-10 20:36 DEBUG  WindowsFrontend: on_init...
07-10 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-10 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-10 20:36 INFO   root: CD menu finished
07-10 20:36 INFO   root: Already installed, running the uninstaller...
07-10 20:36 INFO   root: Running the uninstaller...
07-10 20:36 INFO   CommonBackend: This is the uninstaller running
07-10 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-10 20:37 INFO   root: Received settings
07-10 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-10 20:37 DEBUG  TaskList: # Running tasklist...
07-10 20:37 DEBUG  TaskList: ## Running Backup ISO...
07-10 20:37 DEBUG  TaskList: ## Finished Backup ISO
07-10 20:37 DEBUG  TaskList: ## Running Remove bootloader entry...
07-10 20:37 ERROR  WindowsBackend: Cannot find bcdedit
07-10 20:37 DEBUG  WindowsBackend: undo_bootini C:
07-10 20:37 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 6020.7578125 mb free ntfs)
07-10 20:37 DEBUG  WindowsBackend: undo_bootini D:
07-10 20:37 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 59645.71875 mb free ntfs)
07-10 20:37 DEBUG  TaskList: ## Finished Remove bootloader entry
07-10 20:37 DEBUG  TaskList: ## Running Remove target dir...
07-10 20:37 DEBUG  CommonBackend: Deleting D:\ubuntu
07-10 20:37 DEBUG  TaskList: ## Finished Remove target dir
07-10 20:37 DEBUG  TaskList: ## Running Remove registry key...
07-10 20:37 DEBUG  TaskList: ## Finished Remove registry key
07-10 20:37 DEBUG  TaskList: # Finished tasklist
07-10 20:37 INFO   root: Almost finished uninstalling
07-10 20:37 INFO   root: Finished uninstallation
07-10 20:37 DEBUG  CommonBackend: Fetching basic info...
07-10 20:37 DEBUG  CommonBackend: original_exe=E:\wubi.exe
07-10 20:37 DEBUG  CommonBackend: platform=win32
07-10 20:37 DEBUG  CommonBackend: osname=nt
07-10 20:37 DEBUG  WindowsBackend: arch=amd64
07-10 20:37 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini
07-10 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-10 20:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-10 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-10 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-10 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-10 20:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-10 20:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-10 20:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-10 20:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-10 20:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-10 20:37 DEBUG  WindowsBackend: Fetching host info...
07-10 20:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-10 20:37 DEBUG  WindowsBackend: windows version=xp
07-10 20:37 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-10 20:37 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-10 20:37 DEBUG  WindowsBackend: windows_build=2600
07-10 20:37 DEBUG  WindowsBackend: gmt=5
07-10 20:37 DEBUG  WindowsBackend: country=US
07-10 20:37 DEBUG  WindowsBackend: timezone=America/New_York
07-10 20:37 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-10 20:37 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-10 20:37 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-10 20:37 DEBUG  WindowsBackend: windows_language_code=1033
07-10 20:37 DEBUG  WindowsBackend: windows_language=English
07-10 20:37 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-10 20:37 DEBUG  WindowsBackend: bootloader=xp
07-10 20:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6020.75 mb free ntfs)
07-10 20:37 DEBUG  WindowsBackend: drive=Drive(C: hd 6020.75 mb free ntfs)
07-10 20:37 DEBUG  WindowsBackend: drive=Drive(D: hd 60164.8085938 mb free ntfs)
07-10 20:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-10 20:37 DEBUG  WindowsBackend: uninstaller_path=None
07-10 20:37 DEBUG  WindowsBackend: previous_target_dir=None
07-10 20:37 DEBUG  WindowsBackend: previous_distro_name=None
07-10 20:37 DEBUG  WindowsBackend: keyboard_id=67699721
07-10 20:37 DEBUG  WindowsBackend: keyboard_layout=us
07-10 20:37 DEBUG  WindowsBackend: keyboard_variant=
07-10 20:37 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-10 20:37 DEBUG  CommonBackend: Searching ISOs on USB devices
07-10 20:37 DEBUG  CommonBackend: Searching for local CDs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
07-10 20:37 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-10 20:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-10 20:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-10 20:37 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-10 20:37 INFO   root: Running the installer...
07-10 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-10 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-10 20:37 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karthikeyan
07-10 20:37 INFO   root: Received settings
07-10 20:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-10 20:37 DEBUG  TaskList: # Running tasklist...
07-10 20:37 DEBUG  TaskList: ## Running select_target_dir...
07-10 20:37 INFO   WindowsBackend: Installing into D:\ubuntu
07-10 20:37 DEBUG  TaskList: ## Finished select_target_dir
07-10 20:37 DEBUG  TaskList: ## Running create_dir_structure...
07-10 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-10 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-10 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-10 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-10 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-10 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-10 20:37 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-10 20:37 DEBUG  TaskList: ## Finished create_dir_structure
07-10 20:37 DEBUG  TaskList: ## Running uncompress_target_dir...
07-10 20:37 DEBUG  TaskList: ## Finished uncompress_target_dir
07-10 20:37 DEBUG  TaskList: ## Running create_uninstaller...
07-10 20:37 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-10 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-10 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-10 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-10 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-10 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-10 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-10 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-10 20:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-10 20:37 DEBUG  TaskList: ## Finished create_uninstaller
07-10 20:37 DEBUG  TaskList: ## Running copy_installation_files...
07-10 20:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-10 20:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\winboot -> D:\ubuntu\winboot
07-10 20:37 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl18.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-10 20:37 DEBUG  TaskList: ## Finished copy_installation_files
07-10 20:37 DEBUG  TaskList: ## Running get_iso...
07-10 20:37 DEBUG  TaskList: New task copy_file
07-10 20:37 DEBUG  TaskList: ### Running copy_file...
07-10 20:38 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
07-10 20:38 DEBUG  TaskList: # Cancelling tasklist
07-10 20:38 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
07-10 20:38 DEBUG  TaskList: New task check_iso
07-10 20:38 DEBUG  CommonBackend: Searching for local ISO
07-10 20:38 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-10 20:38 DEBUG  TaskList: New task get_metalink
07-10 20:38 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-10 20:38 DEBUG  TaskList: # Cancelling tasklist
07-10 20:38 DEBUG  TaskList: # Finished tasklist
07-12 20:15 INFO   root: === wubi 10.04 rev189 ===
07-12 20:15 DEBUG  root: Logfile is c:\docume~1\karthi~1\locals~1\temp\wubi-10.04-rev189.log
07-12 20:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\KARTHIKEYAN\\My Documents\\Downloads\\wubi.exe"']
07-12 20:15 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\data
07-12 20:15 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\bin\7z.exe
07-12 20:15 DEBUG  CommonBackend: Fetching basic info...
07-12 20:15 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\KARTHIKEYAN\My Documents\Downloads\wubi.exe
07-12 20:15 DEBUG  CommonBackend: platform=win32
07-12 20:15 DEBUG  CommonBackend: osname=nt
07-12 20:15 DEBUG  CommonBackend: language=en_US
07-12 20:15 DEBUG  CommonBackend: encoding=cp1252
07-12 20:15 DEBUG  WindowsBackend: arch=amd64
07-12 20:15 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\data\isolist.ini
07-12 20:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-12 20:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-12 20:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-12 20:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-12 20:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-12 20:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-12 20:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-12 20:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-12 20:15 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-12 20:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-12 20:15 DEBUG  WindowsBackend: Fetching host info...
07-12 20:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-12 20:15 DEBUG  WindowsBackend: windows version=xp
07-12 20:15 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-12 20:15 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-12 20:15 DEBUG  WindowsBackend: windows_build=2600
07-12 20:15 DEBUG  WindowsBackend: gmt=5
07-12 20:15 DEBUG  WindowsBackend: country=US
07-12 20:15 DEBUG  WindowsBackend: timezone=America/New_York
07-12 20:15 DEBUG  WindowsBackend: windows_username=KARTHIKEYAN
07-12 20:15 DEBUG  WindowsBackend: user_full_name=KARTHIKEYAN
07-12 20:15 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARTHIKEYAN
07-12 20:15 DEBUG  WindowsBackend: windows_language_code=1033
07-12 20:15 DEBUG  WindowsBackend: windows_language=English
07-12 20:15 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.66GHz
07-12 20:15 DEBUG  WindowsBackend: bootloader=xp
07-12 20:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 5514.65234375 mb free ntfs)
07-12 20:15 DEBUG  WindowsBackend: drive=Drive(C: hd 5514.65234375 mb free ntfs)
07-12 20:15 DEBUG  WindowsBackend: drive=Drive(D: hd 59870.2382813 mb free ntfs)
07-12 20:15 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-12 20:15 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-12 20:15 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-12 20:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-12 20:15 DEBUG  WindowsBackend: keyboard_id=67699721
07-12 20:15 DEBUG  WindowsBackend: keyboard_layout=us
07-12 20:15 DEBUG  WindowsBackend: keyboard_variant=
07-12 20:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-12 20:15 DEBUG  CommonBackend: locale=en_US.UTF-8
07-12 20:15 DEBUG  WindowsBackend: total_memory_mb=1014.421875
07-12 20:15 DEBUG  CommonBackend: Searching ISOs on USB devices
07-12 20:15 DEBUG  CommonBackend: Searching for local CDs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Ubuntu Netbook CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Kubuntu Netbook CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Xubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Xubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Mythbuntu CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp is a valid Mythbuntu CD
07-12 20:15 DEBUG  Distro:     does not contain C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-12 20:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-12 20:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-12 20:15 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-12 20:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-12 20:15 INFO   Distro: Found a valid CD for Ubuntu: E:\
07-12 20:15 INFO   root: Running the CD menu...
07-12 20:15 DEBUG  WindowsFrontend: __init__...
07-12 20:15 DEBUG  WindowsFrontend: on_init...
07-12 20:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
07-12 20:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
07-12 20:15 INFO   root: CD menu finished
07-12 20:15 INFO   root: Already installed, running the uninstaller...
07-12 20:15 INFO   root: Running the uninstaller...
07-12 20:15 INFO   CommonBackend: This is the uninstaller running
07-12 20:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARTHI~1\LOCALS~1\Temp\pyl21.tmp\translations, languages=['en_US', 'en']
07-12 20:15 INFO   WindowsFrontend: Operation cancelled
07-12 20:15 DEBUG  WindowsFrontend: frontend.quit
07-12 20:15 DEBUG  WindowsFrontend: frontend.on_quit
07-12 20:15 DEBUG  root: application.on_quit
07-12 20:15 INFO   root: sys.exit

---

### Post by libssd on 2010-07-13
Stop trying to install WUBI. 

Before installing Ubuntu, run chkdisk and make sure that your Windows HDD is in good shape. Then defrag. Then run chkdisk again just to be safe.

Install 32-bit Ubuntu in a partition. When the installer gets to the partitioning stage, chose MANUAL, and then create an EXT4 partition of whatever size you want (unless you expect to create/store a lot of data files, 32gb is more than adequate for Ubuntu), with / as the mount point. Then create a second new partition at least as big as your RAM (unless disk space is very tight), and use it for swap.

I have installed Ubuntu in new partitions on Windows drives several times, using three different versions of Ubuntu, without ever damaging anything in Windows. 

The best Ubuntu guide that I have found to date is free: *Ubuntu Pocket Guide and Reference*, by Keir Thomas. If everybody read (and understood) "CHAPTER ONE: Installing Ubuntu," before attempting to install, there would be far fewer install questions on this forum. Don't worry about the fact that this book was written for Ubuntu 8; the installer works basically the same way in later editions.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Also good (less technical, but applicable to 10.04) is *Getting Started with Ubuntu 10.04*. If feel rather strongly that this guide, and Canonical in general, do not devote enough resources to pre-installation preparation and possible installation glitches. In particular, you should be 100% certain that you have a restorable backup of your present system. Accidents can happen to anybody; for those who are prepared, they are usually just annoying.

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by bcbc on 2010-07-14
The log file doesn't point to a clear cause. the first  couple of permission denied were that it couldn't download the md5 checksums to verify the cd. But you also get permission denied on the copy of the .iso later.

I can't say for sure, but make sure you have an active internet connection when you install.

Re. libssd's comment, a proper install is always better. However, wubi does allow you to try out ubuntu (with a persistent install, not just in a live environment) and see if it works, without partitioning. If you still have problems installing wubi, it might be easier to go with the regular install. However, I've installed wubi many times on xp and never had a permission problem. I just make sure I'm running as an admin and have internet access.

Also, while you can use the Ubuntu installer to partition an XP windows partition (ie applies to you), but the same isn't true for Vista/7 as this can break windows (apparently it puts some system files mid partition that can get destroyed).

---

### Post by mkarthik90 on 2010-07-14
I am having an active unlimited internet connection.  what else can be the problem ?

---

### Post by bcbc on 2010-07-14
> **mkarthik90 said:**
> I am having an active unlimited internet connection.  what else can be the problem ?
This is my analysis from the log file...
```
20:11pm june30 
1. ran wubi.exe from exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe" on c: (do you have the cd mounted locally or you copied the files from the cd into a directory?)
downloaded checksums 
tried to download amd64 version - operation canceled (quit by user?)

20.19
2.  ran from exefile="C:\\ubuntu-10.04-desktop-i386\\wubi.exe" on c:
uninstalled
downloaded checksums
tried to download amd64 version - operation canceled (quit by user?)

20:20
3. same
but quit after uninstalling

20:21
4.  same wubi.exe as above, no uninstall required
downloaded checksums and quit during download of amd64 .iso

20:22
4. same
quit after uninstalling

20:31
5. same file but quit early
20:31 
6. run again
20:54
7.  same
etc. goes on

later on July 1 the D:\ubuntu\uninstall\wubi.exe was executed (probably means you used the add/remove programs to remove Ubuntu)

July 3rd you started running from a CD 
This is when you started getting a permission denied on copy of the .iso

```

In my opinion, there is probably some left over remnant from all the installs being canceled, and that file is 'broken', and windows cannot copy over it. So run chkdsk /r. You should get a FOUND.000 folder afterwards. If that doesn't fix it, boot from the 10.04 install cd in live cd mode ('try without changing...') and view the D: partition in Ubuntu (sometimes windows hides stuff) and delete the remnants of the install. Or else try installing  to another partition (windows drive).

PS for chkdsk, you can right click on the drive, properties, disk tools (or something) and run it from there. Specify to automatically repair.

---

### Post by mkarthik90 on 2010-07-15
when i use chkdsk /r i am getting check disk cannot run the process since it is being used by another process. what can be done? what is the use of chksdsk /r ?

---

### Post by bcbc on 2010-07-15
> **mkarthik90 said:**
> when i use chkdsk /r i am getting check disk cannot run the process since it is being used by another process. what can be done? what is the use of chksdsk /r ?

Go to My Computer, right click on the d: drive, select properties, tools tab, check disk for errors, click on automatically repair. It will tell you it needs to reboot to continue. Say yes.

Chkdsk fixes broken/corrupted files. certain things can cause files  to become corrupted.

---

### Post by mkarthik90 on 2010-07-15
HI,
    I did the steps as you have mentioned in the previous steps and disk checking completed for D:\ but the system doesn't request for any restart option . Can i start installing UBUNTU now using my compact disk.

---

### Post by bcbc on 2010-07-15
> **mkarthik90 said:**
> HI,
    I did the steps as you have mentioned in the previous steps and disk checking completed for D:\ but the system doesn't request for any restart option . Can i start installing UBUNTU now using my compact disk.

first check whether you can boot your ubuntu cd in 'live mode'. (Select 'try without making any changes'). If ubuntu loads up without any problems then you can try installing.

---

### Post by mkarthik90 on 2010-07-17
Does Live mode refers booting the disk at the start up and not storing the OS files in the permanent disks?

---

### Post by bcbc on 2010-07-17
> **mkarthik90 said:**
> Does Live mode refers booting the disk at the start up and not storing the OS files in the permanent disks?

yes, boot from the cd, when you see a tiny keyboard and man icon on the bottom of the screen, press the spacebar. Then select your language and you'll see a menu. Then select 'Try without installing'. If you have any problems you can boot the cd again and select 'Check disk for defects'.

---

### Post by mkarthik90 on 2010-07-24
thanks a lot.. the problem has been solved .

---

