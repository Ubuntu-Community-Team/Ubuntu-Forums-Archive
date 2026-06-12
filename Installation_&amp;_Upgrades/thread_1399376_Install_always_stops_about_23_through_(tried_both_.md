---
title: "Install always stops about 2/3 through (tried both 9.04 and 9.10)"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by winter123 on 2010-02-05
I first tried to install 32 bit Kubuntu 9.04 (which had installed successfully on this exact machine about a year and a half ago and I have not made any hardware changes... but i cannot remember if I used the install from windows method or not). I went through the pre-install screens such as setting the clock and username, and it was EXTREMELY slow (about 40 minutes), is this normal? But, it worked. It went to about 60% then gave me an I/0 device error, and basically said anything could be the problem (I should have taken a picture, but it said the dvd could have an error, the hard drive could have an error, the dvd reader could have an error, or the environment could be too warm)

Next, I burned a brand new dvd with only a few barely visible scratches, with Kubuntu 9.10 x64. I used poweriso, and the only speed i could choose was 22x. I even did a validity check afterwards using poweriso. So I thought that took the disk error out of the equation. Apparently not. It stopped at 78%. I thought I'd try again, and I opened the window to test if a "cooler environment" would help as they suggested. It stopped at exactly 78% again. So what does this mean? 

I tried to boot off a flash drive as well, but it just continued on to  windows. 

I also noticed a bunch of errors scroll down the screen before every pre-install, with every installation, too fast to read. I re-burned 9.10 on the same disk, and it failed again at a different percentage. If you want me to try and get a picture of these errors, I could, or the error when the install stops... It just takes a very long time and I will not try it again unless there's a sure fire solution. For now, I'm trying to install "as a windows app" or whatever, performance takes a hit but if it works I'd be happy. If it really doesn't work that way, I'll try mounting a virtual disk.

In short, every version of Kubuntu fails at about 2/3, different disks fail at different percentages, but running the same disk multiple times produces the same percent that it fails at. Any ideas??

---

### Post by USB_NL on 2010-02-05
do you have a 32 or 64bit machine?
you seem to have tried them both......
and
can you press a button to go to a bootmenu at start?
or
can you set boot priority at start by changing bios settings?

maby this awnsers can help you

---

### Post by winter123 on 2010-02-05
I have 64 bit... I am running 64 bit windows 7 right now. 

To boot, I just hit f12 as the bios is loading, and it gives me a list and I hit enter on the device I want, that's what I did to boot from cd. For a flash drive it didn't work.

---

### Post by USB_NL on 2010-02-05
here you can get ubuntu running from usb
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

but check 64bit

---

### Post by winter123 on 2010-02-05
I tried that yesterday, and nothing happened. Besides, I don't want to run Kubuntu off the USB drive, I want to install it on my main hard drive! I want to install it FROM a flash drive, not TO. I don't even know if this will work! I wish someone that knew something about how the installation process works could tell me why it won't work in my case.

Tried this too, just for sh*ts and giggles - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) - Same thing, just bypasses it and continues to windows.

---

### Post by winter123 on 2010-02-06
I cannot believe this. I gave up and tried to install within windows. I tried to mount the 64 bit 9.10 on a virtual drive to install it as a windows app, and it started downloading the 32 bit through a torrent, while still in the installer, and it was going to take 36 hours! Then I tried both the 32 bit 9.04 and the 64 bit 9.10 cds while in windows, and they both said access denied, and told me to see a log file at a location that doesn;t exist! This is ridiculous. I wasted 20 hours of my life on this and some omnipotent being just doesn't want me to have ubuntu. I'm trying a different distro unless someone has some brilliant reply to get this to work.

Ok i found the log. If anyone can make sense of this, please do.

02-06 00:18 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-06 00:18 DEBUG  root: Logfile is c:\users\eric\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-06 00:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
02-06 00:18 DEBUG  CommonBackend: data_dir=C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\data
02-06 00:18 DEBUG  WindowsBackend: 7z=C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\bin\7z.exe
02-06 00:18 DEBUG  CommonBackend: Fetching basic info...
02-06 00:18 DEBUG  CommonBackend: original_exe=H:\wubi.exe
02-06 00:18 DEBUG  CommonBackend: platform=win32
02-06 00:18 DEBUG  CommonBackend: osname=nt
02-06 00:18 DEBUG  CommonBackend: language=en_US
02-06 00:18 DEBUG  CommonBackend: encoding=cp1252
02-06 00:18 DEBUG  WindowsBackend: arch=amd64
02-06 00:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\data\isolist.ini
02-06 00:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-06 00:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-06 00:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-06 00:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-06 00:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-06 00:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-06 00:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-06 00:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-06 00:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-06 00:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-06 00:18 DEBUG  WindowsBackend: Fetching host info...
02-06 00:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-06 00:18 DEBUG  WindowsBackend: windows version=vista
02-06 00:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
02-06 00:18 DEBUG  WindowsBackend: windows_sp=None
02-06 00:18 DEBUG  WindowsBackend: windows_build=7600
02-06 00:18 DEBUG  WindowsBackend: gmt=-5
02-06 00:18 DEBUG  WindowsBackend: country=US
02-06 00:18 DEBUG  WindowsBackend: timezone=America/New_York
02-06 00:18 DEBUG  WindowsBackend: windows_username=Eric
02-06 00:18 DEBUG  WindowsBackend: user_full_name=Eric
02-06 00:18 DEBUG  WindowsBackend: user_directory=C:\Users\Eric
02-06 00:18 DEBUG  WindowsBackend: windows_language_code=1033
02-06 00:18 DEBUG  WindowsBackend: windows_language=English
02-06 00:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
02-06 00:18 DEBUG  WindowsBackend: bootloader=vista
02-06 00:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 682691.007813 mb free ntfs)
02-06 00:18 DEBUG  WindowsBackend: drive=Drive(C: hd 682691.007813 mb free ntfs)
02-06 00:18 DEBUG  WindowsBackend: drive=Drive(D: hd 38535.09375 mb free ntfs)
02-06 00:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-06 00:18 DEBUG  WindowsBackend: drive=Drive(F: hd 78372.7460938 mb free ntfs)
02-06 00:18 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
02-06 00:18 DEBUG  WindowsBackend: uninstaller_path=None
02-06 00:18 DEBUG  WindowsBackend: previous_target_dir=None
02-06 00:18 DEBUG  WindowsBackend: previous_distro_name=None
02-06 00:18 DEBUG  WindowsBackend: keyboard_id=67699721
02-06 00:18 DEBUG  WindowsBackend: keyboard_layout=us
02-06 00:18 DEBUG  WindowsBackend: keyboard_variant=
02-06 00:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-06 00:18 DEBUG  CommonBackend: locale=en_US.UTF-8
02-06 00:18 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
02-06 00:18 DEBUG  CommonBackend: Searching ISOs on USB devices
02-06 00:18 DEBUG  CommonBackend: Searching for local CDs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Ubuntu Netbook Remix CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Kubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Kubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Kubuntu Netbook CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Xubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Xubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Mythbuntu CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp is a valid Mythbuntu CD
02-06 00:18 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-06 00:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-06 00:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-06 00:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
02-06 00:18 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
02-06 00:18 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
02-06 00:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-06 00:18 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
02-06 00:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
02-06 00:18 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
02-06 00:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-06 00:18 INFO   Distro: Found a valid CD for Kubuntu: H:\
02-06 00:18 INFO   root: Running the CD menu...
02-06 00:18 DEBUG  WindowsFrontend: __init__...
02-06 00:18 DEBUG  WindowsFrontend: on_init...
02-06 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\translations, languages=['en_US', 'en']
02-06 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\translations, languages=['en_US', 'en']
02-06 00:18 INFO   root: CD menu finished
02-06 00:18 INFO   root: Running the installer...
02-06 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\translations, languages=['en_US', 'en']
02-06 00:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\translations, languages=['en_US', 'en']
02-06 00:21 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=eric
02-06 00:21 INFO   root: Received settings
02-06 00:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\translations, languages=['en_US', 'en']
02-06 00:21 DEBUG  TaskList: # Running tasklist...
02-06 00:21 DEBUG  TaskList: ## Running select_target_dir...
02-06 00:21 INFO   WindowsBackend: Installing into C:\ubuntu
02-06 00:21 DEBUG  TaskList: ## Finished select_target_dir
02-06 00:21 DEBUG  TaskList: ## Running create_dir_structure...
02-06 00:21 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-06 00:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-06 00:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-06 00:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-06 00:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-06 00:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-06 00:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-06 00:21 DEBUG  TaskList: ## Finished create_dir_structure
02-06 00:21 DEBUG  TaskList: ## Running uncompress_target_dir...
02-06 00:21 DEBUG  TaskList: ## Finished uncompress_target_dir
02-06 00:21 DEBUG  TaskList: ## Running create_uninstaller...
02-06 00:21 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-06 00:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-06 00:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-06 00:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
02-06 00:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
02-06 00:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-06 00:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
02-06 00:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
02-06 00:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-06 00:21 DEBUG  TaskList: ## Finished create_uninstaller
02-06 00:21 DEBUG  TaskList: ## Running copy_installation_files...
02-06 00:21 DEBUG  WindowsBackend: Copying C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-06 00:21 DEBUG  WindowsBackend: Copying C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\winboot -> C:\ubuntu\winboot
02-06 00:21 DEBUG  WindowsBackend: Copying C:\Users\Eric\AppData\Local\Temp\pyl8875.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
02-06 00:21 DEBUG  TaskList: ## Finished copy_installation_files
02-06 00:21 DEBUG  TaskList: ## Running get_iso...
02-06 00:21 DEBUG  TaskList: New task copy_file
02-06 00:21 DEBUG  TaskList: ### Running copy_file...
02-06 00:21 DEBUG  TaskList: ### Finished copy_file
02-06 00:21 DEBUG  TaskList: New task check_iso
02-06 00:21 DEBUG  TaskList: ### Running check_iso...
02-06 00:21 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
02-06 00:21 DEBUG  Distro:   checking Kubuntu ISO C:\ubuntu\install\installation.iso
02-06 00:21 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
02-06 00:21 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
02-06 00:21 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
02-06 00:21 INFO   Distro: Found a valid iso for Kubuntu: C:\ubuntu\install\installation.iso
02-06 00:21 DEBUG  TaskList: New task get_metalink
02-06 00:21 DEBUG  TaskList: #### Running get_metalink...
02-06 00:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink) > C:\ubuntu\install
02-06 00:21 DEBUG  downloader: Download start filename=C:\ubuntu\install\kubuntu-9.10-desktop-i386.metalink, url=http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.metalink, basename=kubuntu-9.10-desktop-i386.metalink, length=28219, text=None
02-06 00:21 DEBUG  downloader: download finished (read 28219 bytes)
02-06 00:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink](http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink) > C:\ubuntu\install
02-06 00:21 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=282, text=None
02-06 00:21 DEBUG  downloader: download finished (read 282 bytes)
02-06 00:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
02-06 00:21 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/kubuntu/9.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
02-06 00:21 DEBUG  downloader: download finished (read 189 bytes)
02-06 00:21 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
02-06 00:21 INFO   saplog: Checking block bindings..
02-06 00:21 INFO   saplog: Key verified successfully.
02-06 00:21 DEBUG  CommonBackend: metalink md5sums:
900cf707b1fd37ff8eb6f8e7c6518090  kubuntu-9.10-alternate-amd64.metalink
539eb2637eb1519f474b315af2b02fd2  kubuntu-9.10-alternate-i386.metalink
9fd91ccd34288d0f9e804eb3bd13d202  kubuntu-9.10-desktop-amd64.metalink
59f61e753d5b315befc131896d34145d  kubuntu-9.10-desktop-i386.metalink

02-06 00:21 DEBUG  TaskList: #### Finished get_metalink
02-06 00:21 DEBUG  TaskList: New task get_file_md5
02-06 00:21 DEBUG  TaskList: #### Running get_file_md5...
02-06 00:21 DEBUG  TaskList: #### Finished get_file_md5
02-06 00:21 ERROR  CommonBackend: Invalid md5 for ISO C:\ubuntu\install\installation.iso (18ecb71bff567ce7a91443720a86473e != 5a996e0d794e35509d0275d411a3e737)
None
02-06 00:21 DEBUG  TaskList: ### Finished check_iso
02-06 00:21 DEBUG  CommonBackend: Searching for local ISO
02-06 00:21 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-06 00:21 DEBUG  TaskList: New task download
02-06 00:21 DEBUG  TaskList: ### Running download...
02-06 00:21 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.iso.torrent](http://releases.ubuntu.com/kubuntu/9.10/kubuntu-9.10-desktop-i386.iso.torrent) > C:\ubuntu\install\kubuntu-9.10-desktop-i386.iso
02-06 00:25 INFO   WindowsFrontend: Operation cancelled
02-06 00:25 DEBUG  WindowsFrontend: frontend.quit
02-06 00:25 DEBUG  WindowsFrontend: frontend.on_quit
02-06 00:25 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
02-06 00:25 DEBUG  TaskList: # Cancelling tasklist
02-06 00:25 DEBUG  TaskList: ### Finished download
02-06 00:25 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
02-06 00:25 DEBUG  root: application.on_quit
02-06 00:25 DEBUG  root: Forceful exit
02-06 00:25 INFO   root: sys.exit
02-06 00:26 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-06 00:26 DEBUG  root: Logfile is c:\users\eric\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-06 00:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
02-06 00:26 DEBUG  CommonBackend: data_dir=C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\data
02-06 00:26 DEBUG  WindowsBackend: 7z=C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\bin\7z.exe
02-06 00:26 DEBUG  CommonBackend: Fetching basic info...
02-06 00:26 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-06 00:26 DEBUG  CommonBackend: platform=win32
02-06 00:26 DEBUG  CommonBackend: osname=nt
02-06 00:26 DEBUG  CommonBackend: language=en_US
02-06 00:26 DEBUG  CommonBackend: encoding=cp1252
02-06 00:26 DEBUG  WindowsBackend: arch=amd64
02-06 00:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\data\isolist.ini
02-06 00:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-06 00:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-06 00:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-06 00:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-06 00:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-06 00:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-06 00:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-06 00:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-06 00:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-06 00:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-06 00:26 DEBUG  WindowsBackend: Fetching host info...
02-06 00:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-06 00:26 DEBUG  WindowsBackend: windows version=vista
02-06 00:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
02-06 00:26 DEBUG  WindowsBackend: windows_sp=None
02-06 00:26 DEBUG  WindowsBackend: windows_build=7600
02-06 00:26 DEBUG  WindowsBackend: gmt=-5
02-06 00:26 DEBUG  WindowsBackend: country=US
02-06 00:26 DEBUG  WindowsBackend: timezone=America/New_York
02-06 00:26 DEBUG  WindowsBackend: windows_username=Eric
02-06 00:26 DEBUG  WindowsBackend: user_full_name=Eric
02-06 00:26 DEBUG  WindowsBackend: user_directory=C:\Users\Eric
02-06 00:26 DEBUG  WindowsBackend: windows_language_code=1033
02-06 00:26 DEBUG  WindowsBackend: windows_language=English
02-06 00:26 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
02-06 00:26 DEBUG  WindowsBackend: bootloader=vista
02-06 00:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 681981.355469 mb free ntfs)
02-06 00:26 DEBUG  WindowsBackend: drive=Drive(C: hd 681981.355469 mb free ntfs)
02-06 00:26 DEBUG  WindowsBackend: drive=Drive(D: hd 38535.09375 mb free ntfs)
02-06 00:26 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
02-06 00:26 DEBUG  WindowsBackend: drive=Drive(F: hd 78372.7460938 mb free ntfs)
02-06 00:26 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
02-06 00:26 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-06 00:26 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-06 00:26 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
02-06 00:26 DEBUG  WindowsBackend: keyboard_id=67699721
02-06 00:26 DEBUG  WindowsBackend: keyboard_layout=us
02-06 00:26 DEBUG  WindowsBackend: keyboard_variant=
02-06 00:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-06 00:26 DEBUG  CommonBackend: locale=en_US.UTF-8
02-06 00:26 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
02-06 00:26 DEBUG  CommonBackend: Searching ISOs on USB devices
02-06 00:26 DEBUG  CommonBackend: Searching for local CDs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Ubuntu Netbook Remix CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Kubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Kubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Kubuntu Netbook CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Xubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Xubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Mythbuntu CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp is a valid Mythbuntu CD
02-06 00:26 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-06 00:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-06 00:26 DEBUG  Distro:     does not contain E:\casper\initrd.lz
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-06 00:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-06 00:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
02-06 00:26 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
02-06 00:26 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
02-06 00:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-06 00:26 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
02-06 00:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
02-06 00:26 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
02-06 00:26 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-06 00:26 INFO   Distro: Found a valid CD for Kubuntu: H:\
02-06 00:26 INFO   root: Running the uninstaller...
02-06 00:26 INFO   CommonBackend: This is the uninstaller running
02-06 00:26 DEBUG  WindowsFrontend: __init__...
02-06 00:26 DEBUG  WindowsFrontend: on_init...
02-06 00:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\translations, languages=['en_US', 'en']
02-06 00:26 INFO   root: Received settings
02-06 00:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\translations, languages=['en_US', 'en']
02-06 00:26 DEBUG  TaskList: # Running tasklist...
02-06 00:26 DEBUG  TaskList: ## Running Backup ISO...
02-06 00:26 DEBUG  TaskList: ## Finished Backup ISO
02-06 00:26 DEBUG  TaskList: ## Running Remove bootloader entry...
02-06 00:26 DEBUG  WindowsBackend: Could not find bcd id
02-06 00:26 DEBUG  WindowsBackend: undo_bootini C:
02-06 00:26 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 681981.355469 mb free ntfs)
02-06 00:26 DEBUG  WindowsBackend: undo_bootini D:
02-06 00:26 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 38535.09375 mb free ntfs)
02-06 00:26 DEBUG  WindowsBackend: undo_bootini F:
02-06 00:26 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 78372.7460938 mb free ntfs)
02-06 00:26 DEBUG  TaskList: ## Finished Remove bootloader entry
02-06 00:26 DEBUG  TaskList: ## Running Remove target dir...
02-06 00:26 DEBUG  CommonBackend: Deleting C:\ubuntu
02-06 00:26 DEBUG  TaskList: ## Finished Remove target dir
02-06 00:26 DEBUG  TaskList: ## Running Remove registry key...
02-06 00:26 DEBUG  TaskList: ## Finished Remove registry key
02-06 00:26 DEBUG  TaskList: # Finished tasklist
02-06 00:26 INFO   root: Almost finished uninstalling
02-06 00:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl9F9D.tmp\translations, languages=['en_US', 'en']
02-06 00:26 INFO   root: Finished uninstallation
02-06 00:26 DEBUG  root: application.quit
02-06 00:26 DEBUG  WindowsFrontend: frontend.quit
02-06 00:26 DEBUG  WindowsFrontend: frontend.on_quit
02-06 00:26 DEBUG  root: application.on_quit
02-06 00:26 INFO   root: sys.exit
02-06 00:30 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-06 00:30 DEBUG  root: Logfile is c:\users\eric\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-06 00:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
02-06 00:30 DEBUG  CommonBackend: data_dir=C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\data
02-06 00:30 DEBUG  WindowsBackend: 7z=C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\bin\7z.exe
02-06 00:30 DEBUG  CommonBackend: Fetching basic info...
02-06 00:30 DEBUG  CommonBackend: original_exe=E:\wubi.exe
02-06 00:30 DEBUG  CommonBackend: platform=win32
02-06 00:30 DEBUG  CommonBackend: osname=nt
02-06 00:30 DEBUG  CommonBackend: language=en_US
02-06 00:30 DEBUG  CommonBackend: encoding=cp1252
02-06 00:30 DEBUG  WindowsBackend: arch=amd64
02-06 00:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\data\isolist.ini
02-06 00:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-06 00:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-06 00:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-06 00:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-06 00:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-06 00:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-06 00:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-06 00:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-06 00:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-06 00:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-06 00:30 DEBUG  WindowsBackend: Fetching host info...
02-06 00:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-06 00:30 DEBUG  WindowsBackend: windows version=vista
02-06 00:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
02-06 00:30 DEBUG  WindowsBackend: windows_sp=None
02-06 00:30 DEBUG  WindowsBackend: windows_build=7600
02-06 00:30 DEBUG  WindowsBackend: gmt=-5
02-06 00:30 DEBUG  WindowsBackend: country=US
02-06 00:30 DEBUG  WindowsBackend: timezone=America/New_York
02-06 00:30 DEBUG  WindowsBackend: windows_username=Eric
02-06 00:30 DEBUG  WindowsBackend: user_full_name=Eric
02-06 00:30 DEBUG  WindowsBackend: user_directory=C:\Users\Eric
02-06 00:30 DEBUG  WindowsBackend: windows_language_code=1033
02-06 00:30 DEBUG  WindowsBackend: windows_language=English
02-06 00:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
02-06 00:30 DEBUG  WindowsBackend: bootloader=vista
02-06 00:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 682673.539063 mb free ntfs)
02-06 00:30 DEBUG  WindowsBackend: drive=Drive(C: hd 682673.539063 mb free ntfs)
02-06 00:30 DEBUG  WindowsBackend: drive=Drive(D: hd 38535.09375 mb free ntfs)
02-06 00:30 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
02-06 00:30 DEBUG  WindowsBackend: drive=Drive(F: hd 78372.7460938 mb free ntfs)
02-06 00:30 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
02-06 00:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-06 00:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-06 00:30 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
02-06 00:30 DEBUG  WindowsBackend: keyboard_id=67699721
02-06 00:30 DEBUG  WindowsBackend: keyboard_layout=us
02-06 00:30 DEBUG  WindowsBackend: keyboard_variant=
02-06 00:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-06 00:30 DEBUG  CommonBackend: locale=en_US.UTF-8
02-06 00:30 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
02-06 00:30 DEBUG  CommonBackend: Searching ISOs on USB devices
02-06 00:30 DEBUG  CommonBackend: Searching for local CDs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Ubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Ubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Ubuntu Netbook Remix CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Kubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Kubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Kubuntu Netbook CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Xubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Xubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Mythbuntu CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp is a valid Mythbuntu CD
02-06 00:30 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-06 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-06 00:30 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
02-06 00:30 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
02-06 00:30 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
02-06 00:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-06 00:30 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
02-06 00:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-06 00:30 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
02-06 00:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-06 00:30 INFO   Distro: Found a valid CD for Kubuntu: E:\
02-06 00:30 INFO   root: Running the CD menu...
02-06 00:30 DEBUG  WindowsFrontend: __init__...
02-06 00:30 DEBUG  WindowsFrontend: on_init...
02-06 00:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\translations, languages=['en_US', 'en']
02-06 00:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pylCE7A.tmp\translations, languages=['en_US', 'en']
02-06 00:31 INFO   root: CD menu finished
02-06 00:31 INFO   root: Already installed, running the uninstaller...
02-06 00:31 INFO   root: Running the uninstaller...
02-06 00:31 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
02-06 00:31 DEBUG  root: application.quit
02-06 00:31 DEBUG  WindowsFrontend: frontend.quit
02-06 00:31 DEBUG  WindowsFrontend: frontend.on_quit
02-06 00:31 DEBUG  root: application.on_quit
02-06 00:31 INFO   root: sys.exit
02-06 00:31 INFO   root: === wubi 9.10ubuntu1 rev160 ===
02-06 00:31 DEBUG  root: Logfile is c:\users\eric\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
02-06 00:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
02-06 00:31 DEBUG  CommonBackend: data_dir=C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\data
02-06 00:31 DEBUG  WindowsBackend: 7z=C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\bin\7z.exe
02-06 00:31 DEBUG  CommonBackend: Fetching basic info...
02-06 00:31 DEBUG  CommonBackend: original_exe=E:\wubi.exe
02-06 00:31 DEBUG  CommonBackend: platform=win32
02-06 00:31 DEBUG  CommonBackend: osname=nt
02-06 00:31 DEBUG  CommonBackend: language=en_US
02-06 00:31 DEBUG  CommonBackend: encoding=cp1252
02-06 00:31 DEBUG  WindowsBackend: arch=amd64
02-06 00:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\data\isolist.ini
02-06 00:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-06 00:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-06 00:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-06 00:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-06 00:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-06 00:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-06 00:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-06 00:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-06 00:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-06 00:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
02-06 00:31 DEBUG  WindowsBackend: Fetching host info...
02-06 00:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-06 00:31 DEBUG  WindowsBackend: windows version=vista
02-06 00:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
02-06 00:31 DEBUG  WindowsBackend: windows_sp=None
02-06 00:31 DEBUG  WindowsBackend: windows_build=7600
02-06 00:31 DEBUG  WindowsBackend: gmt=-5
02-06 00:31 DEBUG  WindowsBackend: country=US
02-06 00:31 DEBUG  WindowsBackend: timezone=America/New_York
02-06 00:31 DEBUG  WindowsBackend: windows_username=Eric
02-06 00:31 DEBUG  WindowsBackend: user_full_name=Eric
02-06 00:31 DEBUG  WindowsBackend: user_directory=C:\Users\Eric
02-06 00:31 DEBUG  WindowsBackend: windows_language_code=1033
02-06 00:31 DEBUG  WindowsBackend: windows_language=English
02-06 00:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
02-06 00:31 DEBUG  WindowsBackend: bootloader=vista
02-06 00:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 682687.25 mb free ntfs)
02-06 00:31 DEBUG  WindowsBackend: drive=Drive(C: hd 682687.25 mb free ntfs)
02-06 00:31 DEBUG  WindowsBackend: drive=Drive(D: hd 38535.09375 mb free ntfs)
02-06 00:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
02-06 00:31 DEBUG  WindowsBackend: drive=Drive(F: hd 78372.7460938 mb free ntfs)
02-06 00:31 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
02-06 00:31 DEBUG  WindowsBackend: uninstaller_path=None
02-06 00:31 DEBUG  WindowsBackend: previous_target_dir=None
02-06 00:31 DEBUG  WindowsBackend: previous_distro_name=None
02-06 00:31 DEBUG  WindowsBackend: keyboard_id=67699721
02-06 00:31 DEBUG  WindowsBackend: keyboard_layout=us
02-06 00:31 DEBUG  WindowsBackend: keyboard_variant=
02-06 00:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-06 00:31 DEBUG  CommonBackend: locale=en_US.UTF-8
02-06 00:31 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
02-06 00:31 DEBUG  CommonBackend: Searching ISOs on USB devices
02-06 00:31 DEBUG  CommonBackend: Searching for local CDs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Ubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Ubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Ubuntu Netbook Remix CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Kubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Kubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Kubuntu Netbook CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Xubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Xubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Mythbuntu CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp is a valid Mythbuntu CD
02-06 00:31 DEBUG  Distro:     does not contain C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-06 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-06 00:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-06 00:31 DEBUG  Distro:   parsing info from str=Kubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
02-06 00:31 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
02-06 00:31 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
02-06 00:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-06 00:31 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
02-06 00:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
02-06 00:31 DEBUG  Distro: wrong name: Kubuntu != Ubuntu Netbook Remix
02-06 00:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-06 00:31 INFO   Distro: Found a valid CD for Kubuntu: E:\
02-06 00:31 INFO   root: Running the CD menu...
02-06 00:31 DEBUG  WindowsFrontend: __init__...
02-06 00:31 DEBUG  WindowsFrontend: on_init...
02-06 00:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\translations, languages=['en_US', 'en']
02-06 00:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\translations, languages=['en_US', 'en']
02-06 00:31 INFO   root: CD menu finished
02-06 00:31 INFO   root: Running the installer...
02-06 00:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\translations, languages=['en_US', 'en']
02-06 00:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\translations, languages=['en_US', 'en']
02-06 00:31 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=eric
02-06 00:31 INFO   root: Received settings
02-06 00:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\translations, languages=['en_US', 'en']
02-06 00:31 DEBUG  TaskList: # Running tasklist...
02-06 00:31 DEBUG  TaskList: ## Running select_target_dir...
02-06 00:31 INFO   WindowsBackend: Installing into C:\ubuntu
02-06 00:31 DEBUG  TaskList: ## Finished select_target_dir
02-06 00:31 DEBUG  TaskList: ## Running create_dir_structure...
02-06 00:31 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-06 00:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-06 00:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-06 00:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-06 00:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-06 00:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-06 00:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-06 00:31 DEBUG  TaskList: ## Finished create_dir_structure
02-06 00:31 DEBUG  TaskList: ## Running uncompress_target_dir...
02-06 00:31 DEBUG  TaskList: ## Finished uncompress_target_dir
02-06 00:31 DEBUG  TaskList: ## Running create_uninstaller...
02-06 00:31 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-06 00:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-06 00:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-06 00:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
02-06 00:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
02-06 00:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
02-06 00:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
02-06 00:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
02-06 00:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-06 00:31 DEBUG  TaskList: ## Finished create_uninstaller
02-06 00:31 DEBUG  TaskList: ## Running copy_installation_files...
02-06 00:31 DEBUG  WindowsBackend: Copying C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-06 00:31 DEBUG  WindowsBackend: Copying C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\winboot -> C:\ubuntu\winboot
02-06 00:31 DEBUG  WindowsBackend: Copying C:\Users\Eric\AppData\Local\Temp\pyl8CB9.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
02-06 00:31 DEBUG  TaskList: ## Finished copy_installation_files
02-06 00:31 DEBUG  TaskList: ## Running get_iso...
02-06 00:31 DEBUG  TaskList: New task copy_file
02-06 00:31 DEBUG  TaskList: ### Running copy_file...
02-06 00:32 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-06 00:32 DEBUG  TaskList: # Cancelling tasklist
02-06 00:32 DEBUG  TaskList: New task check_iso
02-06 00:32 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
02-06 00:32 DEBUG  CommonBackend: Searching for local ISO
02-06 00:32 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-06 00:32 DEBUG  TaskList: New task get_metalink
02-06 00:32 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
02-06 00:32 DEBUG  TaskList: # Cancelling tasklist
02-06 00:32 DEBUG  TaskList: # Finished tasklist

---

### Post by mushwars on 2010-02-06
IOError: [Errno 13] Permission denied

there is your problem.

Are you trying to install within win 7? you should really burn to a cd then boot it, resize windoesnt and then install ubuntu in a new partition. 

I dont know much about winblows but perhaps you are not running the installer as administrator so that is why it fails.

---

### Post by amsterdamharu on 2010-02-06
Only the op's last try was wubi because normal install takes a long time and fails. 

I would suggest trying unetbootin, put the files on C:, not the usb stick and boot from HD (you should get a menu). 

Installation might take some time because files are downloaded very slow, I am in China and indicating I am in China caused the install to try and download stuff from a slow Chinese server. Saying I am in the US fixed it.

You could try unplugging the Internet and see if it skips the lengthy download, you can run an update later anyway I assume.

I assume you've made some space for Ubuntu to install on, an unused partition that it can use.

---

### Post by winter123 on 2010-02-06
Great. two more replies from people who have no idea what they're talking about. Originially (the first 5 install attempts that failed) It was booting from a CD and installing on a created partition. the USB install was a last attempt and never worked. 3 different kubuntu cd's and 2 different versions all failed at 2/3 percent. So I don't know what is wrong or what to do. Maybe windows 7 is in fact causing these problems but I like windows 7 so I am not downgrading to a different windows. I am trying to install kubuntu by booting from cd on an unoccupied partition so I don't know what's wrong.

---

### Post by amsterdamharu on 2010-02-06
> Great. two more replies from people who have no idea what they're talking about.I feel your frustration but what I suggested is something you haven't tried yet. The following should not take more than 30 minutes to complete or fail. But lets hope it completes.

Let unetbootin put the files on your C: drive and boot from C:, installation will run off your harddrive as if it was the CD. Do not let unetbootin download the iso, it is already on your drive just choose iso and point to the iso file.

Unplug the network cable so the install does not go through a lengthy file download during setup.

And no it is not normal to take 40 minuts unless it's checking the CD. Unetbootin should be done with extracting the files within 5 minutes (progress bar can be off because the cd contains one giant file).

There might be something wrong with the DVD, unetbootin only needs the iso, will extract the files to C:, change your boot sector and makes a startup menu. Next time you start you get an option to start unetbootin (which is the install cd) or windows. If you start windows unetbootin will start on windows startup and askes you if it's ok to remove the files (CD files, boot partition restore and menu). I think you can add-remove progams to remove this files as well but never tried that because I am lucky enough to have it working on first try on several dual boot machines.

Since installing from USB didn't boot all your failed installations have one thing in common: CD media.

---

### Post by winter123 on 2010-02-06
Sorry. I just wasted so much time on this. I did manage to use unetbootin and then it gave me a choice to boot either windows, or that. I went through the installation, it didnt download anything, but took at least 30 minutes to go through the clock/keyboard/etc settings, and near an hour for the installation. It was crazy too, it would be at 90%, then drop back down to like 76% and sit there for 5 minutes. Anyway, I was up till past 5am but it did finish. 

But I must have done something wrong, because I tried making a file on the desktop and restarting and it's gone. I still have the choice of windows or unetbootin (not the actual os). So we've already established cd's don't work for whatever reason... This is just as slow or even possibly slower, but it works. So what did I do wrong?

Edit: I tried restarting just now, the unetboot choice is just gone. I must have overwritten it by trying other versions of Linux last night as well. Mandriva froze and another one apparently tried to install to my non-main hard drive. It's like I'm destined to not have Linux. But this c: boot of kubuntu was the closest I've gotten so I'd like to try that again, except correctly.

Edit again: After screwing around for a while deleting partitions, I realized I had an old xbox hard drive in there with games as Disk0, but my xbox had broken so I put it in here, but it was being recognized as "unallocated space" but I don't want to delete all the games, who knows, one day I might be able to use them. ANYWAY, The disk management tool in win7 was trying to boot it and i got an i/o device error... So I have a feeling the kubuntu installer was trying to do something with disk0 simply because it was the first disk, and getting the same i/o device error. I'm going to take a break and do homework now, but I'll try again later  tonight. Any ideas to support/reject that it was that disk causing the errors?

---

### Post by amsterdamharu on 2010-02-06
The first time you installed kubuntu it might have put grub on a harddisk that is not used for booting in your bios.

You want to install kubuntu on the same harddisk as windows then I suggest maybe unplugging the other harddisks and CD rom might speed up things. Set the windows hd as the first boot device (maybe after CD or USB but not after any other harddisks),

If ubuntu doesn't boot after installing it you might use unetbootin to run kubuntu as live CD (not sure if it's possible it should have a try ubuntu option when starting up NOT the wubi install).

I am used to installing the alternate ubuntu CD and never used the normal/graphical one because it never worked for me. But on most installs downloading extra install files took the longest time. Pressing control + alt + F1 to F8(or F7) gives you different tty's, one of them is output from the installer so you can see what it's up to.

---

### Post by winter123 on 2010-02-07
Yes, I unplugged the drive and now the Windows HDD is disk0, and just to be absolutely sure, I deleted "floppy disk" as the first boot device (I mean come on, do people still use those?) and hard drive as first boot item. I don't think I had the option to choose which, but since it is disk0 it should start first, right? I'm going to try kubuntu again during the super bowl (cause I'm lame like that :popcorn: ) and if that fails, try the latest mandriva, and if THAT fails either just boot every time from unetbootin or cd.

REALLY hope this works, because I wasted a good 2 days on this, and am likely going to bomb a quiz tomorrow because of it (Ironically, a Linux class. I wanted to install it on my own system so I could use it all the time and learn it better and have more freedom). Also, if it works now, I will likely burn this hard drive along with the retarded Xbox it came from.

---

### Post by winter123 on 2010-02-10
Ok, super bowl was a bit too enthralling... I will likely try it tonight (nothing better to do) or definitely some time this weekend. I am really convinced mentally it will work and that the hard drive was the issue. I am also downloading the alternate text installer, because, who knows, I could try that as an absolute last step before simply booting off cd or unetboot (because cd boot should be adequate for my purposes, if all else fails).

---

