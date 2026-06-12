---
title: "Cant install Wubi  on window 7"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by withmanu on 2010-07-07
I was trying to install Wubi on windows 7 64 bit.. But at the end of the installation, im getting a permission denied error and the installtion is getting aborted..
 
Can somebody help me to fix this and get the new Wubi installed on my Laptop
 
===============================
Installation log
===============================
07-05 22:27 INFO root: === wubi 10.04 rev189 ===
07-05 22:27 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-05 22:27 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
07-05 22:27 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\data
07-05 22:27 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\bin\7z.exe
07-05 22:27 DEBUG CommonBackend: Fetching basic info...
07-05 22:27 DEBUG CommonBackend: original_exe=C:\wubi.exe
07-05 22:27 DEBUG CommonBackend: platform=win32
07-05 22:27 DEBUG CommonBackend: osname=nt
07-05 22:27 DEBUG CommonBackend: language=en_US
07-05 22:27 DEBUG CommonBackend: encoding=cp1252
07-05 22:27 DEBUG WindowsBackend: arch=amd64
07-05 22:27 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\data\isolist.ini
07-05 22:27 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-05 22:27 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-05 22:27 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-05 22:27 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-05 22:27 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-05 22:27 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-05 22:27 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-05 22:27 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-05 22:27 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-05 22:27 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-05 22:27 DEBUG WindowsBackend: Fetching host info...
07-05 22:27 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-05 22:27 DEBUG WindowsBackend: windows version=vista
07-05 22:27 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-05 22:27 DEBUG WindowsBackend: windows_sp=None
07-05 22:27 DEBUG WindowsBackend: windows_build=7600
07-05 22:27 DEBUG WindowsBackend: gmt=5
07-05 22:27 DEBUG WindowsBackend: country=US
07-05 22:27 DEBUG WindowsBackend: timezone=America/New_York
07-05 22:27 DEBUG WindowsBackend: windows_username=Manu
07-05 22:27 DEBUG WindowsBackend: user_full_name=Manu
07-05 22:27 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-05 22:27 DEBUG WindowsBackend: windows_language_code=1033
07-05 22:27 DEBUG WindowsBackend: windows_language=English
07-05 22:27 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-05 22:27 DEBUG WindowsBackend: bootloader=vista
07-05 22:27 DEBUG WindowsBackend: system_drive=Drive(C: hd 22276.8320313 mb free ntfs)
07-05 22:27 DEBUG WindowsBackend: drive=Drive(C: hd 22276.8320313 mb free ntfs)
07-05 22:27 DEBUG WindowsBackend: drive=Drive(D: hd 47153.4296875 mb free ntfs)
07-05 22:27 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-05 22:27 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3828125 mb free ntfs)
07-05 22:27 DEBUG WindowsBackend: drive=Drive(G: hd 8695.29296875 mb free ntfs)
07-05 22:27 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-05 22:27 DEBUG WindowsBackend: uninstaller_path=None
07-05 22:27 DEBUG WindowsBackend: previous_target_dir=None
07-05 22:27 DEBUG WindowsBackend: previous_distro_name=None
07-05 22:27 DEBUG WindowsBackend: keyboard_id=67699721
07-05 22:27 DEBUG WindowsBackend: keyboard_layout=us
07-05 22:27 DEBUG WindowsBackend: keyboard_variant=
07-05 22:27 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-05 22:27 DEBUG CommonBackend: locale=en_US.UTF-8
07-05 22:27 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-05 22:27 DEBUG CommonBackend: Searching ISOs on USB devices
07-05 22:27 DEBUG CommonBackend: Searching for local CDs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Ubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Kubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-05 22:27 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:27 INFO root: Running the installer...
07-05 22:27 DEBUG WindowsFrontend: __init__...
07-05 22:27 DEBUG WindowsFrontend: on_init...
07-05 22:27 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\translations, languages=['en_US', 'en']
07-05 22:27 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\translations, languages=['en_US', 'en']
07-05 22:29 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=manu
07-05 22:29 INFO root: Received settings
07-05 22:29 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\translations, languages=['en_US', 'en']
07-05 22:29 DEBUG TaskList: # Running tasklist...
07-05 22:29 DEBUG TaskList: ## Running select_target_dir...
07-05 22:29 INFO WindowsBackend: Installing into D:\ubuntu
07-05 22:29 DEBUG TaskList: ## Finished select_target_dir
07-05 22:29 DEBUG TaskList: ## Running create_dir_structure...
07-05 22:29 DEBUG CommonBackend: Creating dir D:\ubuntu
07-05 22:29 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
07-05 22:29 DEBUG CommonBackend: Creating dir D:\ubuntu\install
07-05 22:29 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
07-05 22:29 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
07-05 22:29 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-05 22:29 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-05 22:29 DEBUG TaskList: ## Finished create_dir_structure
07-05 22:29 DEBUG TaskList: ## Running uncompress_target_dir...
07-05 22:29 DEBUG TaskList: ## Finished uncompress_target_dir
07-05 22:29 DEBUG TaskList: ## Running create_uninstaller...
07-05 22:29 DEBUG WindowsBackend: Copying uninstaller C:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-05 22:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-05 22:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-05 22:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
07-05 22:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Kubuntu.ico
07-05 22:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-05 22:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
07-05 22:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
07-05 22:29 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-05 22:29 DEBUG TaskList: ## Finished create_uninstaller
07-05 22:29 DEBUG TaskList: ## Running copy_installation_files...
07-05 22:29 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-05 22:29 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\winboot -> D:\ubuntu\winboot
07-05 22:29 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\data\images\Kubuntu.ico -> D:\ubuntu\Kubuntu.ico
07-05 22:29 DEBUG TaskList: ## Finished copy_installation_files
07-05 22:29 DEBUG TaskList: ## Running get_iso...
07-05 22:29 DEBUG CommonBackend: Searching for local CD
07-05 22:29 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp is a valid Kubuntu CD
07-05 22:29 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\casper\filesystem.squashfs
07-05 22:29 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-05 22:29 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-05 22:29 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-05 22:29 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-05 22:29 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-05 22:29 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-05 22:29 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-05 22:29 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-05 22:29 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-05 22:29 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-05 22:29 DEBUG CommonBackend: Searching for local ISO
07-05 22:29 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-05 22:29 DEBUG TaskList: New task get_metalink
07-05 22:29 DEBUG TaskList: ### Running get_metalink...
07-05 22:29 DEBUG downloader: downloading [http://releases.ubuntu.com/kubuntu/10.04/kubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/kubuntu/10.04/kubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
07-05 22:29 DEBUG downloader: Download start filename=D:\ubuntu\install\kubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/kubuntu/10.04/kubuntu-10.04-desktop-amd64.metalink, basename=kubuntu-10.04-desktop-amd64.metalink, length=7940, text=None
07-05 22:29 DEBUG downloader: download finished (read 7940 bytes)
07-05 22:29 DEBUG downloader: downloading [http://releases.ubuntu.com/kubuntu/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/kubuntu/10.04/MD5SUMS-metalink) > D:\ubuntu\install
07-05 22:29 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/kubuntu/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=657, text=None
07-05 22:29 DEBUG downloader: download finished (read 657 bytes)
07-05 22:29 DEBUG downloader: downloading [http://releases.ubuntu.com/kubuntu/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/kubuntu/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-05 22:29 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/kubuntu/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-05 22:29 DEBUG downloader: download finished (read 189 bytes)
07-05 22:29 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
07-05 22:29 INFO saplog: Checking block bindings..
07-05 22:29 INFO saplog: Key verified successfully.
07-05 22:29 DEBUG CommonBackend: metalink md5sums:
d9060ce229ed262e6034f4924de83cbe kubuntu-10.04-alternate-amd64.metalink
8091578560623c461309c78ec3e10530 kubuntu-10.04-alternate-i386.metalink
404cf370557577ad8247e9982c6fa90f kubuntu-10.04-desktop-amd64.metalink
e97b782133580127aa7e9a53afdd963a kubuntu-10.04-desktop-i386.metalink
4c60ea68c2bc7ffa22fbea46d90271ca kubuntu-10.04-rc-alternate-amd64.metalink
ad86fc4ae4acd3da562da8e4c553d429 kubuntu-10.04-rc-alternate-i386.metalink
0018caff45c1df4ba8f527559970fddd kubuntu-10.04-rc-desktop-amd64.metalink
f3ddda7875599bda4391e0893eb353c5 kubuntu-10.04-rc-desktop-i386.metalink
70f4bcf6c5c39f49215999342d34be57 kubuntu-10.04-rc-netbook-i386.metalink
07-05 22:29 DEBUG TaskList: ### Finished get_metalink
07-05 22:29 DEBUG TaskList: New task download
07-05 22:29 DEBUG TaskList: ### Running download...
07-05 22:29 DEBUG btdownloader: downloading [http://releases.ubuntu.com/kubuntu/10.04/kubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/kubuntu/10.04/kubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG TaskList: ### Finished download
07-06 00:10 DEBUG TaskList: New task check_iso
07-06 00:10 DEBUG TaskList: ### Running check_iso...
07-06 00:10 DEBUG CommonBackend: Checking D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG Distro: checking Kubuntu ISO D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG WindowsBackend: extracting .disk\info from D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG Distro: parsing info from str=Kubuntu 10.04 LTS "Lucid Lynx" - Release amd64 (20100427)
07-06 00:10 DEBUG Distro: parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100427', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
07-06 00:10 INFO Distro: Found a valid iso for Kubuntu: D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG TaskList: New task get_file_md5
07-06 00:10 DEBUG TaskList: #### Running get_file_md5...
07-06 00:10 DEBUG TaskList: #### Finished get_file_md5
07-06 00:10 DEBUG TaskList: ### Finished check_iso
07-06 00:10 DEBUG TaskList: ## Finished get_iso
07-06 00:10 DEBUG TaskList: ## Running extract_kernel...
07-06 00:10 DEBUG CommonBackend: Extracting files from ISO D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG WindowsBackend: extracting md5sum.txt from D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG WindowsBackend: extracting casper\vmlinuz from D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG WindowsBackend: extracting casper\initrd.lz from D:\ubuntu\install\kubuntu-10.04-desktop-amd64.iso
07-06 00:10 DEBUG CommonBackend: Checking kernel, initrd and md5sums
07-06 00:10 DEBUG CommonBackend: checking D:\ubuntu\install\boot\vmlinuz
07-06 00:10 DEBUG CommonBackend: D:\ubuntu\install\boot\vmlinuz md5 = 135737a6c8608631a2cde5a8aad7995c == 135737a6c8608631a2cde5a8aad7995c
07-06 00:10 DEBUG CommonBackend: checking D:\ubuntu\install\boot\initrd.lz
07-06 00:10 DEBUG CommonBackend: D:\ubuntu\install\boot\initrd.lz md5 = 57e10d0f16d32afbcf54944089f184d2 == 57e10d0f16d32afbcf54944089f184d2
07-06 00:10 DEBUG TaskList: ## Finished extract_kernel
07-06 00:10 DEBUG TaskList: ## Running choose_disk_sizes...
07-06 00:10 DEBUG WindowsBackend: total size=12000
root=11744
swap=256
home=0
usr=0
07-06 00:10 DEBUG TaskList: ## Finished choose_disk_sizes
07-06 00:10 DEBUG TaskList: ## Running create_preseed...
07-06 00:10 DEBUG TaskList: ## Finished create_preseed
07-06 00:10 DEBUG TaskList: ## Running modify_bootloader...
07-06 00:10 DEBUG TaskList: New task modify_bcd
07-06 00:10 DEBUG TaskList: ### Running modify_bcd...
07-06 00:10 DEBUG WindowsBackend: modify_bcd Drive(C: hd 22276.8320313 mb free ntfs)
07-06 00:10 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {12dec93c-7996-11df-99dd-b4e0356661f7}
07-06 00:10 DEBUG TaskList: ### Finished modify_bcd
07-06 00:10 DEBUG TaskList: New task modify_bcd
07-06 00:10 DEBUG TaskList: ### Running modify_bcd...
07-06 00:10 DEBUG WindowsBackend: modify_bcd Drive(D: hd 47153.4296875 mb free ntfs)
07-06 00:10 DEBUG WindowsBackend: BCD has already been modified
07-06 00:10 DEBUG TaskList: ### Finished modify_bcd
07-06 00:10 DEBUG TaskList: New task modify_bcd
07-06 00:10 DEBUG TaskList: ### Running modify_bcd...
07-06 00:10 DEBUG WindowsBackend: modify_bcd Drive(E: hd 17628.171875 mb free ntfs)
07-06 00:10 DEBUG WindowsBackend: BCD has already been modified
07-06 00:10 DEBUG TaskList: ### Finished modify_bcd
07-06 00:10 DEBUG TaskList: New task modify_bcd
07-06 00:10 DEBUG TaskList: ### Running modify_bcd...
07-06 00:10 DEBUG WindowsBackend: modify_bcd Drive(F: hd 23888.3828125 mb free ntfs)
07-06 00:10 DEBUG WindowsBackend: BCD has already been modified
07-06 00:10 DEBUG TaskList: ### Finished modify_bcd
07-06 00:10 DEBUG TaskList: New task modify_bcd
07-06 00:10 DEBUG TaskList: ### Running modify_bcd...
07-06 00:10 DEBUG WindowsBackend: modify_bcd Drive(G: hd 8695.29296875 mb free ntfs)
07-06 00:10 DEBUG WindowsBackend: BCD has already been modified
07-06 00:10 DEBUG TaskList: ### Finished modify_bcd
07-06 00:10 DEBUG TaskList: ## Finished modify_bootloader
07-06 00:10 DEBUG TaskList: ## Running modify_grub_configuration...
07-06 00:10 DEBUG TaskList: ## Finished modify_grub_configuration
07-06 00:10 DEBUG TaskList: ## Running create_virtual_disks...
07-06 00:10 DEBUG Virtualdisk: Creating virtual disk D:\ubuntu\disks\root.disk of 11744MB
07-06 00:10 DEBUG Virtualdisk: Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
07-06 00:10 DEBUG TaskList: ## Finished create_virtual_disks
07-06 00:10 DEBUG TaskList: ## Running uncompress_files...
07-06 00:10 DEBUG WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
07-06 00:10 DEBUG WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
07-06 00:10 DEBUG TaskList: ## Finished uncompress_files
07-06 00:10 DEBUG TaskList: ## Running eject_cd...
07-06 00:10 DEBUG TaskList: ## Finished eject_cd
07-06 00:10 DEBUG TaskList: # Finished tasklist
07-06 00:10 INFO root: Almost finished installing
07-06 00:10 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl8C93.tmp\translations, languages=['en_US', 'en']
07-06 00:19 INFO root: Finished installation
07-06 00:19 INFO root: Rebooting
07-06 00:19 DEBUG TaskList: # Running tasklist...
07-06 00:19 DEBUG TaskList: ## Running reboot...
07-06 00:19 DEBUG TaskList: ## Finished reboot
07-06 00:19 DEBUG TaskList: # Finished tasklist
07-06 00:19 DEBUG root: application.quit
07-06 00:19 DEBUG WindowsFrontend: frontend.quit
07-06 00:19 DEBUG WindowsFrontend: frontend.on_quit
07-06 00:19 DEBUG root: application.on_quit
07-06 00:19 INFO root: sys.exit
07-06 09:18 INFO root: === wubi 10.04 rev189 ===
07-06 09:18 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-06 09:18 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-06 09:18 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\data
07-06 09:18 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\bin\7z.exe
07-06 09:18 DEBUG CommonBackend: Fetching basic info...
07-06 09:18 DEBUG CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-06 09:18 DEBUG CommonBackend: platform=win32
07-06 09:18 DEBUG CommonBackend: osname=nt
07-06 09:18 DEBUG CommonBackend: language=en_US
07-06 09:18 DEBUG CommonBackend: encoding=cp1252
07-06 09:18 DEBUG WindowsBackend: arch=amd64
07-06 09:18 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\data\isolist.ini
07-06 09:18 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-06 09:18 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-06 09:18 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-06 09:18 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-06 09:18 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-06 09:18 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-06 09:18 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-06 09:18 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-06 09:18 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-06 09:18 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-06 09:18 DEBUG WindowsBackend: Fetching host info...
07-06 09:18 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-06 09:18 DEBUG WindowsBackend: windows version=vista
07-06 09:18 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-06 09:18 DEBUG WindowsBackend: windows_sp=None
07-06 09:18 DEBUG WindowsBackend: windows_build=7600
07-06 09:18 DEBUG WindowsBackend: gmt=5
07-06 09:18 DEBUG WindowsBackend: country=US
07-06 09:18 DEBUG WindowsBackend: timezone=America/New_York
07-06 09:18 DEBUG WindowsBackend: windows_username=Manu
07-06 09:18 DEBUG WindowsBackend: user_full_name=Manu
07-06 09:18 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-06 09:18 DEBUG WindowsBackend: windows_language_code=1033
07-06 09:18 DEBUG WindowsBackend: windows_language=English
07-06 09:18 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-06 09:18 DEBUG WindowsBackend: bootloader=vista
07-06 09:18 DEBUG WindowsBackend: system_drive=Drive(C: hd 21458.984375 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: drive=Drive(C: hd 21458.984375 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: drive=Drive(D: hd 34454.5351563 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3828125 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: drive=Drive(G: hd 8695.29296875 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-06 09:18 DEBUG WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-06 09:18 DEBUG WindowsBackend: previous_target_dir=D:\ubuntu
07-06 09:18 DEBUG WindowsBackend: previous_distro_name=Kubuntu
07-06 09:18 DEBUG WindowsBackend: keyboard_id=67699721
07-06 09:18 DEBUG WindowsBackend: keyboard_layout=us
07-06 09:18 DEBUG WindowsBackend: keyboard_variant=
07-06 09:18 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-06 09:18 DEBUG CommonBackend: locale=en_US.UTF-8
07-06 09:18 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-06 09:18 DEBUG CommonBackend: Searching ISOs on USB devices
07-06 09:18 DEBUG CommonBackend: Searching for local CDs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Ubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Kubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 09:18 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:18 INFO root: Running the uninstaller...
07-06 09:18 INFO CommonBackend: This is the uninstaller running
07-06 09:18 DEBUG WindowsFrontend: __init__...
07-06 09:18 DEBUG WindowsFrontend: on_init...
07-06 09:18 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\translations, languages=['en_US', 'en']
07-06 09:18 INFO root: Received settings
07-06 09:18 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\translations, languages=['en_US', 'en']
07-06 09:18 DEBUG TaskList: # Running tasklist...
07-06 09:18 DEBUG TaskList: ## Running Backup ISO...
07-06 09:18 DEBUG TaskList: ## Finished Backup ISO
07-06 09:18 DEBUG TaskList: ## Running Remove bootloader entry...
07-06 09:18 DEBUG WindowsBackend: Removing bcd entry {12dec93c-7996-11df-99dd-b4e0356661f7}
07-06 09:18 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
07-06 09:18 DEBUG WindowsBackend: undo_bootini C:
07-06 09:18 DEBUG WindowsBackend: undo_configsys Drive(C: hd 21458.984375 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: undo_bootini D:
07-06 09:18 DEBUG WindowsBackend: undo_configsys Drive(D: hd 34454.5351563 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: undo_bootini E:
07-06 09:18 DEBUG WindowsBackend: undo_configsys Drive(E: hd 17628.171875 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: undo_bootini F:
07-06 09:18 DEBUG WindowsBackend: undo_configsys Drive(F: hd 23888.3828125 mb free ntfs)
07-06 09:18 DEBUG WindowsBackend: undo_bootini G:
07-06 09:18 DEBUG WindowsBackend: undo_configsys Drive(G: hd 8695.29296875 mb free ntfs)
07-06 09:18 DEBUG TaskList: ## Finished Remove bootloader entry
07-06 09:18 DEBUG TaskList: ## Running Remove target dir...
07-06 09:18 DEBUG CommonBackend: Deleting D:\ubuntu
07-06 09:18 DEBUG TaskList: ## Finished Remove target dir
07-06 09:18 DEBUG TaskList: ## Running Remove registry key...
07-06 09:18 DEBUG TaskList: ## Finished Remove registry key
07-06 09:18 DEBUG TaskList: # Finished tasklist
07-06 09:18 INFO root: Almost finished uninstalling
07-06 09:18 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl4317.tmp\translations, languages=['en_US', 'en']
07-06 09:18 INFO root: Finished uninstallation
07-06 09:18 DEBUG root: application.quit
07-06 09:18 DEBUG WindowsFrontend: frontend.quit
07-06 09:18 DEBUG WindowsFrontend: frontend.on_quit
07-06 09:18 DEBUG root: application.on_quit
07-06 09:18 INFO root: sys.exit
07-06 09:19 INFO root: === wubi 10.04 rev189 ===
07-06 09:19 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-06 09:19 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
07-06 09:19 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\data
07-06 09:19 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\bin\7z.exe
07-06 09:19 DEBUG CommonBackend: Fetching basic info...
07-06 09:19 DEBUG CommonBackend: original_exe=C:\wubi.exe
07-06 09:19 DEBUG CommonBackend: platform=win32
07-06 09:19 DEBUG CommonBackend: osname=nt
07-06 09:19 DEBUG CommonBackend: language=en_US
07-06 09:19 DEBUG CommonBackend: encoding=cp1252
07-06 09:19 DEBUG WindowsBackend: arch=amd64
07-06 09:19 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\data\isolist.ini
07-06 09:19 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-06 09:19 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-06 09:19 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-06 09:19 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-06 09:19 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-06 09:19 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-06 09:19 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-06 09:19 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-06 09:19 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-06 09:19 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-06 09:19 DEBUG WindowsBackend: Fetching host info...
07-06 09:19 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-06 09:19 DEBUG WindowsBackend: windows version=vista
07-06 09:19 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-06 09:19 DEBUG WindowsBackend: windows_sp=None
07-06 09:19 DEBUG WindowsBackend: windows_build=7600
07-06 09:19 DEBUG WindowsBackend: gmt=5
07-06 09:19 DEBUG WindowsBackend: country=US
07-06 09:19 DEBUG WindowsBackend: timezone=America/New_York
07-06 09:19 DEBUG WindowsBackend: windows_username=Manu
07-06 09:19 DEBUG WindowsBackend: user_full_name=Manu
07-06 09:19 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-06 09:19 DEBUG WindowsBackend: windows_language_code=1033
07-06 09:19 DEBUG WindowsBackend: windows_language=English
07-06 09:19 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-06 09:19 DEBUG WindowsBackend: bootloader=vista
07-06 09:19 DEBUG WindowsBackend: system_drive=Drive(C: hd 21457.9453125 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(C: hd 21457.9140625 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(D: hd 47153.421875 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3828125 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(G: hd 8695.29296875 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-06 09:19 DEBUG WindowsBackend: uninstaller_path=None
07-06 09:19 DEBUG WindowsBackend: previous_target_dir=None
07-06 09:19 DEBUG WindowsBackend: previous_distro_name=None
07-06 09:19 DEBUG WindowsBackend: keyboard_id=67699721
07-06 09:19 DEBUG WindowsBackend: keyboard_layout=us
07-06 09:19 DEBUG WindowsBackend: keyboard_variant=
07-06 09:19 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-06 09:19 DEBUG CommonBackend: locale=en_US.UTF-8
07-06 09:19 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-06 09:19 DEBUG CommonBackend: Searching ISOs on USB devices
07-06 09:19 DEBUG CommonBackend: Searching for local CDs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 INFO root: Running the installer...
07-06 09:19 DEBUG WindowsFrontend: __init__...
07-06 09:19 DEBUG WindowsFrontend: on_init...
07-06 09:19 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\translations, languages=['en_US', 'en']
07-06 09:19 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\translations, languages=['en_US', 'en']
07-06 09:19 INFO root: === wubi 10.04 rev189 ===
07-06 09:19 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-06 09:19 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
07-06 09:19 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\data
07-06 09:19 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\bin\7z.exe
07-06 09:19 DEBUG CommonBackend: Fetching basic info...
07-06 09:19 DEBUG CommonBackend: original_exe=C:\wubi.exe
07-06 09:19 DEBUG CommonBackend: platform=win32
07-06 09:19 DEBUG CommonBackend: osname=nt
07-06 09:19 DEBUG CommonBackend: language=en_US
07-06 09:19 DEBUG CommonBackend: encoding=cp1252
07-06 09:19 DEBUG WindowsBackend: arch=amd64
07-06 09:19 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\data\isolist.ini
07-06 09:19 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-06 09:19 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-06 09:19 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-06 09:19 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-06 09:19 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-06 09:19 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-06 09:19 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-06 09:19 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-06 09:19 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-06 09:19 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-06 09:19 DEBUG WindowsBackend: Fetching host info...
07-06 09:19 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-06 09:19 DEBUG WindowsBackend: windows version=vista
07-06 09:19 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-06 09:19 DEBUG WindowsBackend: windows_sp=None
07-06 09:19 DEBUG WindowsBackend: windows_build=7600
07-06 09:19 DEBUG WindowsBackend: gmt=5
07-06 09:19 DEBUG WindowsBackend: country=US
07-06 09:19 DEBUG WindowsBackend: timezone=America/New_York
07-06 09:19 DEBUG WindowsBackend: windows_username=Manu
07-06 09:19 DEBUG WindowsBackend: user_full_name=Manu
07-06 09:19 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-06 09:19 DEBUG WindowsBackend: windows_language_code=1033
07-06 09:19 DEBUG WindowsBackend: windows_language=English
07-06 09:19 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-06 09:19 DEBUG WindowsBackend: bootloader=vista
07-06 09:19 DEBUG WindowsBackend: system_drive=Drive(C: hd 21452.28125 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(C: hd 21452.28125 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(D: hd 47153.421875 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3828125 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(G: hd 8695.29296875 mb free ntfs)
07-06 09:19 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-06 09:19 DEBUG WindowsBackend: uninstaller_path=None
07-06 09:19 DEBUG WindowsBackend: previous_target_dir=None
07-06 09:19 DEBUG WindowsBackend: previous_distro_name=None
07-06 09:19 DEBUG WindowsBackend: keyboard_id=67699721
07-06 09:19 DEBUG WindowsBackend: keyboard_layout=us
07-06 09:19 DEBUG WindowsBackend: keyboard_variant=
07-06 09:19 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-06 09:19 DEBUG CommonBackend: locale=en_US.UTF-8
07-06 09:19 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-06 09:19 DEBUG CommonBackend: Searching ISOs on USB devices
07-06 09:19 DEBUG CommonBackend: Searching for local CDs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 INFO root: Running the installer...
07-06 09:19 DEBUG WindowsFrontend: __init__...
07-06 09:19 DEBUG WindowsFrontend: on_init...
07-06 09:19 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\translations, languages=['en_US', 'en']
07-06 09:19 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylBE4F.tmp\translations, languages=['en_US', 'en']
07-06 09:19 DEBUG WindowsFrontend: frontend.on_quit
07-06 09:19 DEBUG root: application.on_quit
07-06 09:19 INFO root: sys.exit
07-06 09:19 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=manu
07-06 09:19 INFO root: Received settings
07-06 09:19 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\translations, languages=['en_US', 'en']
07-06 09:19 DEBUG TaskList: # Running tasklist...
07-06 09:19 DEBUG TaskList: ## Running select_target_dir...
07-06 09:19 INFO WindowsBackend: Installing into D:\ubuntu
07-06 09:19 DEBUG TaskList: ## Finished select_target_dir
07-06 09:19 DEBUG TaskList: ## Running create_dir_structure...
07-06 09:19 DEBUG CommonBackend: Creating dir D:\ubuntu
07-06 09:19 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
07-06 09:19 DEBUG CommonBackend: Creating dir D:\ubuntu\install
07-06 09:19 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
07-06 09:19 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
07-06 09:19 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-06 09:19 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-06 09:19 DEBUG TaskList: ## Finished create_dir_structure
07-06 09:19 DEBUG TaskList: ## Running uncompress_target_dir...
07-06 09:19 DEBUG TaskList: ## Finished uncompress_target_dir
07-06 09:19 DEBUG TaskList: ## Running create_uninstaller...
07-06 09:19 DEBUG WindowsBackend: Copying uninstaller C:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-06 09:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-06 09:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-06 09:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-06 09:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-06 09:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-06 09:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-06 09:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-06 09:19 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-06 09:19 DEBUG TaskList: ## Finished create_uninstaller
07-06 09:19 DEBUG TaskList: ## Running copy_installation_files...
07-06 09:19 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-06 09:19 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\winboot -> D:\ubuntu\winboot
07-06 09:19 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-06 09:19 DEBUG TaskList: ## Finished copy_installation_files
07-06 09:19 DEBUG TaskList: ## Running get_iso...
07-06 09:19 DEBUG CommonBackend: Searching for local CD
07-06 09:19 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylB50B.tmp\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 09:19 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 09:19 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 09:19 DEBUG CommonBackend: Searching for local ISO
07-06 09:19 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-06 09:19 DEBUG TaskList: New task get_metalink
07-06 09:19 DEBUG TaskList: ### Running get_metalink...
07-06 09:19 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
07-06 09:19 DEBUG downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-06 09:19 DEBUG downloader: download finished (read 7472 bytes)
07-06 09:19 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
07-06 09:19 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-06 09:19 DEBUG downloader: download finished (read 639 bytes)
07-06 09:19 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-06 09:19 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-06 09:19 DEBUG downloader: download finished (read 189 bytes)
07-06 09:19 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
07-06 09:19 INFO saplog: Checking block bindings..
07-06 09:19 INFO saplog: Key verified successfully.
07-06 09:19 DEBUG CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5 ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83 ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882 ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6 ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5 ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0 ubuntu-10.04-server-i386.metalink
07-06 09:19 DEBUG TaskList: ### Finished get_metalink
07-06 09:19 DEBUG TaskList: New task download
07-06 09:19 DEBUG TaskList: ### Running download...
07-06 09:19 DEBUG btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-06 11:49 ERROR TaskList: Traceback (most recent call last):
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
 
07-06 11:49 ERROR TaskList: Non fatal error Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request
in task download
07-06 11:49 DEBUG TaskList: ### Finished download
07-06 11:49 ERROR TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-06 11:49 DEBUG TaskList: # Cancelling tasklist
07-06 11:49 DEBUG TaskList: # Finished tasklist
07-06 11:49 ERROR root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 130, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-06 12:47 INFO root: === wubi 10.04 rev189 ===
07-06 12:47 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-06 12:47 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
07-06 12:47 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\data
07-06 12:47 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\bin\7z.exe
07-06 12:47 DEBUG CommonBackend: Fetching basic info...
07-06 12:47 DEBUG CommonBackend: original_exe=C:\wubi.exe
07-06 12:47 DEBUG CommonBackend: platform=win32
07-06 12:47 DEBUG CommonBackend: osname=nt
07-06 12:47 DEBUG CommonBackend: language=en_US
07-06 12:47 DEBUG CommonBackend: encoding=cp1252
07-06 12:47 DEBUG WindowsBackend: arch=amd64
07-06 12:47 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\data\isolist.ini
07-06 12:47 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-06 12:47 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-06 12:47 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-06 12:47 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-06 12:47 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-06 12:47 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-06 12:47 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-06 12:47 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-06 12:47 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-06 12:47 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-06 12:47 DEBUG WindowsBackend: Fetching host info...
07-06 12:47 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-06 12:47 DEBUG WindowsBackend: windows version=vista
07-06 12:47 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-06 12:47 DEBUG WindowsBackend: windows_sp=None
07-06 12:47 DEBUG WindowsBackend: windows_build=7600
07-06 12:47 DEBUG WindowsBackend: gmt=5
07-06 12:47 DEBUG WindowsBackend: country=US
07-06 12:47 DEBUG WindowsBackend: timezone=America/New_York
07-06 12:47 DEBUG WindowsBackend: windows_username=Manu
07-06 12:47 DEBUG WindowsBackend: user_full_name=Manu
07-06 12:47 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-06 12:47 DEBUG WindowsBackend: windows_language_code=1033
07-06 12:47 DEBUG WindowsBackend: windows_language=English
07-06 12:47 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-06 12:47 DEBUG WindowsBackend: bootloader=vista
07-06 12:47 DEBUG WindowsBackend: system_drive=Drive(C: hd 21238.6015625 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(C: hd 21238.6015625 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(D: hd 46647.328125 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3828125 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(G: hd 8695.29296875 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-06 12:47 DEBUG WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-06 12:47 DEBUG WindowsBackend: previous_target_dir=D:\ubuntu
07-06 12:47 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-06 12:47 DEBUG WindowsBackend: keyboard_id=67699721
07-06 12:47 DEBUG WindowsBackend: keyboard_layout=us
07-06 12:47 DEBUG WindowsBackend: keyboard_variant=
07-06 12:47 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-06 12:47 DEBUG CommonBackend: locale=en_US.UTF-8
07-06 12:47 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-06 12:47 DEBUG CommonBackend: Searching ISOs on USB devices
07-06 12:47 DEBUG CommonBackend: Searching for local CDs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 INFO root: Already installed, running the uninstaller...
07-06 12:47 INFO root: Running the uninstaller...
07-06 12:47 INFO CommonBackend: This is the uninstaller running
07-06 12:47 DEBUG WindowsFrontend: __init__...
07-06 12:47 DEBUG WindowsFrontend: on_init...
07-06 12:47 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\translations, languages=['en_US', 'en']
07-06 12:47 INFO root: Received settings
07-06 12:47 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\translations, languages=['en_US', 'en']
07-06 12:47 DEBUG TaskList: # Running tasklist...
07-06 12:47 DEBUG TaskList: ## Running Backup ISO...
07-06 12:47 DEBUG TaskList: ## Finished Backup ISO
07-06 12:47 DEBUG TaskList: ## Running Remove bootloader entry...
07-06 12:47 DEBUG WindowsBackend: Could not find bcd id
07-06 12:47 DEBUG WindowsBackend: undo_bootini C:
07-06 12:47 DEBUG WindowsBackend: undo_configsys Drive(C: hd 21238.6015625 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: undo_bootini D:
07-06 12:47 DEBUG WindowsBackend: undo_configsys Drive(D: hd 46647.328125 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: undo_bootini E:
07-06 12:47 DEBUG WindowsBackend: undo_configsys Drive(E: hd 17628.171875 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: undo_bootini F:
07-06 12:47 DEBUG WindowsBackend: undo_configsys Drive(F: hd 23888.3828125 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: undo_bootini G:
07-06 12:47 DEBUG WindowsBackend: undo_configsys Drive(G: hd 8695.29296875 mb free ntfs)
07-06 12:47 DEBUG TaskList: ## Finished Remove bootloader entry
07-06 12:47 DEBUG TaskList: ## Running Remove target dir...
07-06 12:47 DEBUG CommonBackend: Deleting D:\ubuntu
07-06 12:47 DEBUG TaskList: ## Finished Remove target dir
07-06 12:47 DEBUG TaskList: ## Running Remove registry key...
07-06 12:47 DEBUG TaskList: ## Finished Remove registry key
07-06 12:47 DEBUG TaskList: # Finished tasklist
07-06 12:47 INFO root: Almost finished uninstalling
07-06 12:47 INFO root: Finished uninstallation
07-06 12:47 DEBUG CommonBackend: Fetching basic info...
07-06 12:47 DEBUG CommonBackend: original_exe=C:\wubi.exe
07-06 12:47 DEBUG CommonBackend: platform=win32
07-06 12:47 DEBUG CommonBackend: osname=nt
07-06 12:47 DEBUG WindowsBackend: arch=amd64
07-06 12:47 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\data\isolist.ini
07-06 12:47 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-06 12:47 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-06 12:47 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-06 12:47 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-06 12:47 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-06 12:47 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-06 12:47 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-06 12:47 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-06 12:47 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-06 12:47 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-06 12:47 DEBUG WindowsBackend: Fetching host info...
07-06 12:47 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-06 12:47 DEBUG WindowsBackend: windows version=vista
07-06 12:47 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-06 12:47 DEBUG WindowsBackend: windows_sp=None
07-06 12:47 DEBUG WindowsBackend: windows_build=7600
07-06 12:47 DEBUG WindowsBackend: gmt=5
07-06 12:47 DEBUG WindowsBackend: country=US
07-06 12:47 DEBUG WindowsBackend: timezone=America/New_York
07-06 12:47 DEBUG WindowsBackend: windows_username=Manu
07-06 12:47 DEBUG WindowsBackend: user_full_name=Manu
07-06 12:47 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-06 12:47 DEBUG WindowsBackend: windows_language_code=1033
07-06 12:47 DEBUG WindowsBackend: windows_language=English
07-06 12:47 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-06 12:47 DEBUG WindowsBackend: bootloader=vista
07-06 12:47 DEBUG WindowsBackend: system_drive=Drive(C: hd 21238.4804688 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(C: hd 21238.4804688 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(D: hd 47153.359375 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3828125 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(G: hd 8695.29296875 mb free ntfs)
07-06 12:47 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-06 12:47 DEBUG WindowsBackend: uninstaller_path=None
07-06 12:47 DEBUG WindowsBackend: previous_target_dir=None
07-06 12:47 DEBUG WindowsBackend: previous_distro_name=None
07-06 12:47 DEBUG WindowsBackend: keyboard_id=67699721
07-06 12:47 DEBUG WindowsBackend: keyboard_layout=us
07-06 12:47 DEBUG WindowsBackend: keyboard_variant=
07-06 12:47 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-06 12:47 DEBUG CommonBackend: Searching ISOs on USB devices
07-06 12:47 DEBUG CommonBackend: Searching for local CDs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 INFO root: Running the installer...
07-06 12:47 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\translations, languages=['en_US', 'en']
07-06 12:47 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\translations, languages=['en_US', 'en']
07-06 12:47 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=manu
07-06 12:47 INFO root: Received settings
07-06 12:47 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\translations, languages=['en_US', 'en']
07-06 12:47 DEBUG TaskList: # Running tasklist...
07-06 12:47 DEBUG TaskList: ## Running select_target_dir...
07-06 12:47 INFO WindowsBackend: Installing into D:\ubuntu
07-06 12:47 DEBUG TaskList: ## Finished select_target_dir
07-06 12:47 DEBUG TaskList: ## Running create_dir_structure...
07-06 12:47 DEBUG CommonBackend: Creating dir D:\ubuntu
07-06 12:47 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
07-06 12:47 DEBUG CommonBackend: Creating dir D:\ubuntu\install
07-06 12:47 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
07-06 12:47 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
07-06 12:47 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-06 12:47 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-06 12:47 DEBUG TaskList: ## Finished create_dir_structure
07-06 12:47 DEBUG TaskList: ## Running uncompress_target_dir...
07-06 12:47 DEBUG TaskList: ## Finished uncompress_target_dir
07-06 12:47 DEBUG TaskList: ## Running create_uninstaller...
07-06 12:47 DEBUG WindowsBackend: Copying uninstaller C:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-06 12:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-06 12:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-06 12:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-06 12:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-06 12:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-06 12:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-06 12:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-06 12:47 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-06 12:47 DEBUG TaskList: ## Finished create_uninstaller
07-06 12:47 DEBUG TaskList: ## Running copy_installation_files...
07-06 12:47 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-06 12:47 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\winboot -> D:\ubuntu\winboot
07-06 12:47 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-06 12:47 DEBUG TaskList: ## Finished copy_installation_files
07-06 12:47 DEBUG TaskList: ## Running get_iso...
07-06 12:47 DEBUG CommonBackend: Searching for local CD
07-06 12:47 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl402E.tmp\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 12:47 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 12:47 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 12:47 DEBUG CommonBackend: Searching for local ISO
07-06 12:47 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-06 12:47 DEBUG TaskList: New task get_metalink
07-06 12:47 DEBUG TaskList: ### Running get_metalink...
07-06 12:47 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
07-06 12:47 DEBUG downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-06 12:47 DEBUG downloader: download finished (read 7472 bytes)
07-06 12:47 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
07-06 12:47 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-06 12:47 DEBUG downloader: download finished (read 639 bytes)
07-06 12:47 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-06 12:47 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-06 12:47 DEBUG downloader: download finished (read 189 bytes)
07-06 12:47 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
07-06 12:47 INFO saplog: Checking block bindings..
07-06 12:47 INFO saplog: Key verified successfully.
07-06 12:47 DEBUG CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5 ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83 ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882 ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6 ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5 ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0 ubuntu-10.04-server-i386.metalink
07-06 12:47 DEBUG TaskList: ### Finished get_metalink
07-06 12:47 DEBUG TaskList: New task download
07-06 12:47 DEBUG TaskList: ### Running download...
07-06 12:47 DEBUG btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-06 15:32 ERROR TaskList: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (7, 'getaddrinfo failed')>
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
DownloadError: Problem connecting to tracker - <urlopen error (7, 'getaddrinfo failed')>
 
07-06 15:32 ERROR TaskList: Non fatal error Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (7, 'getaddrinfo failed')>
in task download
07-06 15:32 DEBUG TaskList: ### Finished download
07-06 15:32 ERROR TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-06 15:32 DEBUG TaskList: # Cancelling tasklist
07-06 15:32 DEBUG TaskList: # Finished tasklist
07-06 15:32 ERROR root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 130, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-06 15:40 INFO root: === wubi 10.04 rev189 ===
07-06 15:40 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-06 15:40 DEBUG root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-06 15:40 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\data
07-06 15:40 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\bin\7z.exe
07-06 15:40 DEBUG CommonBackend: Fetching basic info...
07-06 15:40 DEBUG CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-06 15:40 DEBUG CommonBackend: platform=win32
07-06 15:40 DEBUG CommonBackend: osname=nt
07-06 15:40 DEBUG CommonBackend: language=en_US
07-06 15:40 DEBUG CommonBackend: encoding=cp1252
07-06 15:40 DEBUG WindowsBackend: arch=amd64
07-06 15:40 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\data\isolist.ini
07-06 15:40 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-06 15:40 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-06 15:40 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-06 15:40 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-06 15:40 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-06 15:40 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-06 15:40 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-06 15:40 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-06 15:40 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-06 15:40 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-06 15:40 DEBUG WindowsBackend: Fetching host info...
07-06 15:40 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-06 15:40 DEBUG WindowsBackend: windows version=vista
07-06 15:40 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-06 15:40 DEBUG WindowsBackend: windows_sp=None
07-06 15:40 DEBUG WindowsBackend: windows_build=7600
07-06 15:40 DEBUG WindowsBackend: gmt=5
07-06 15:40 DEBUG WindowsBackend: country=US
07-06 15:40 DEBUG WindowsBackend: timezone=America/New_York
07-06 15:40 DEBUG WindowsBackend: windows_username=Manu
07-06 15:40 DEBUG WindowsBackend: user_full_name=Manu
07-06 15:40 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-06 15:40 DEBUG WindowsBackend: windows_language_code=1033
07-06 15:40 DEBUG WindowsBackend: windows_language=English
07-06 15:40 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-06 15:40 DEBUG WindowsBackend: bootloader=vista
07-06 15:40 DEBUG WindowsBackend: system_drive=Drive(C: hd 21347.9804688 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: drive=Drive(C: hd 21347.9804688 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: drive=Drive(D: hd 46609.390625 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: drive=Drive(G: hd 8691.44140625 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-06 15:40 DEBUG WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-06 15:40 DEBUG WindowsBackend: previous_target_dir=D:\ubuntu
07-06 15:40 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-06 15:40 DEBUG WindowsBackend: keyboard_id=67699721
07-06 15:40 DEBUG WindowsBackend: keyboard_layout=us
07-06 15:40 DEBUG WindowsBackend: keyboard_variant=
07-06 15:40 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-06 15:40 DEBUG CommonBackend: locale=en_US.UTF-8
07-06 15:40 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-06 15:40 DEBUG CommonBackend: Searching ISOs on USB devices
07-06 15:40 DEBUG CommonBackend: Searching for local CDs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Ubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Kubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-06 15:40 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-06 15:40 INFO root: Running the uninstaller...
07-06 15:40 INFO CommonBackend: This is the uninstaller running
07-06 15:40 DEBUG WindowsFrontend: __init__...
07-06 15:40 DEBUG WindowsFrontend: on_init...
07-06 15:40 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\translations, languages=['en_US', 'en']
07-06 15:40 INFO root: Received settings
07-06 15:40 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\translations, languages=['en_US', 'en']
07-06 15:40 DEBUG TaskList: # Running tasklist...
07-06 15:40 DEBUG TaskList: ## Running Backup ISO...
07-06 15:40 DEBUG TaskList: ## Finished Backup ISO
07-06 15:40 DEBUG TaskList: ## Running Remove bootloader entry...
07-06 15:40 DEBUG WindowsBackend: Could not find bcd id
07-06 15:40 DEBUG WindowsBackend: undo_bootini C:
07-06 15:40 DEBUG WindowsBackend: undo_configsys Drive(C: hd 21347.9804688 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: undo_bootini D:
07-06 15:40 DEBUG WindowsBackend: undo_configsys Drive(D: hd 46609.390625 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: undo_bootini E:
07-06 15:40 DEBUG WindowsBackend: undo_configsys Drive(E: hd 17628.171875 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: undo_bootini F:
07-06 15:40 DEBUG WindowsBackend: undo_configsys Drive(F: hd 23888.3789063 mb free ntfs)
07-06 15:40 DEBUG WindowsBackend: undo_bootini G:
07-06 15:40 DEBUG WindowsBackend: undo_configsys Drive(G: hd 8691.44140625 mb free ntfs)
07-06 15:40 DEBUG TaskList: ## Finished Remove bootloader entry
07-06 15:40 DEBUG TaskList: ## Running Remove target dir...
07-06 15:40 DEBUG CommonBackend: Deleting D:\ubuntu
07-06 15:40 DEBUG TaskList: ## Finished Remove target dir
07-06 15:40 DEBUG TaskList: ## Running Remove registry key...
07-06 15:40 DEBUG TaskList: ## Finished Remove registry key
07-06 15:40 DEBUG TaskList: # Finished tasklist
07-06 15:40 INFO root: Almost finished uninstalling
07-06 15:40 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylAC74.tmp\translations, languages=['en_US', 'en']
07-06 15:40 INFO root: Finished uninstallation
07-06 15:40 DEBUG root: application.quit
07-06 15:40 DEBUG WindowsFrontend: frontend.quit
07-06 15:40 DEBUG WindowsFrontend: frontend.on_quit
07-06 15:40 DEBUG root: application.on_quit
07-06 15:40 INFO root: sys.exit
07-07 03:20 INFO root: === wubi 10.04 rev189 ===
07-07 03:20 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-07 03:20 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\wubi_2.exe"']
07-07 03:20 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\data
07-07 03:20 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\bin\7z.exe
07-07 03:20 DEBUG CommonBackend: Fetching basic info...
07-07 03:20 DEBUG CommonBackend: original_exe=C:\wubi_2.exe
07-07 03:20 DEBUG CommonBackend: platform=win32
07-07 03:20 DEBUG CommonBackend: osname=nt
07-07 03:20 DEBUG CommonBackend: language=en_US
07-07 03:20 DEBUG CommonBackend: encoding=cp1252
07-07 03:20 DEBUG WindowsBackend: arch=amd64
07-07 03:20 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\data\isolist.ini
07-07 03:20 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-07 03:20 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-07 03:20 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-07 03:20 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-07 03:20 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-07 03:20 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-07 03:20 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-07 03:20 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-07 03:20 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-07 03:20 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-07 03:20 DEBUG WindowsBackend: Fetching host info...
07-07 03:20 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-07 03:20 DEBUG WindowsBackend: windows version=vista
07-07 03:20 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-07 03:20 DEBUG WindowsBackend: windows_sp=None
07-07 03:20 DEBUG WindowsBackend: windows_build=7600
07-07 03:20 DEBUG WindowsBackend: gmt=5
07-07 03:20 DEBUG WindowsBackend: country=US
07-07 03:20 DEBUG WindowsBackend: timezone=America/New_York
07-07 03:20 DEBUG WindowsBackend: windows_username=Manu
07-07 03:20 DEBUG WindowsBackend: user_full_name=Manu
07-07 03:20 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-07 03:20 DEBUG WindowsBackend: windows_language_code=1033
07-07 03:20 DEBUG WindowsBackend: windows_language=English
07-07 03:20 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-07 03:20 DEBUG WindowsBackend: bootloader=vista
07-07 03:20 DEBUG WindowsBackend: system_drive=Drive(C: hd 21311.5859375 mb free ntfs)
07-07 03:20 DEBUG WindowsBackend: drive=Drive(C: hd 21311.5859375 mb free ntfs)
07-07 03:20 DEBUG WindowsBackend: drive=Drive(D: hd 47152.921875 mb free ntfs)
07-07 03:20 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-07 03:20 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-07 03:20 DEBUG WindowsBackend: drive=Drive(G: hd 8691.44140625 mb free ntfs)
07-07 03:20 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-07 03:20 DEBUG WindowsBackend: uninstaller_path=None
07-07 03:20 DEBUG WindowsBackend: previous_target_dir=None
07-07 03:20 DEBUG WindowsBackend: previous_distro_name=None
07-07 03:20 DEBUG WindowsBackend: keyboard_id=67699721
07-07 03:20 DEBUG WindowsBackend: keyboard_layout=us
07-07 03:20 DEBUG WindowsBackend: keyboard_variant=
07-07 03:20 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-07 03:20 DEBUG CommonBackend: locale=en_US.UTF-8
07-07 03:20 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-07 03:20 DEBUG CommonBackend: Searching ISOs on USB devices
07-07 03:20 DEBUG CommonBackend: Searching for local CDs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 03:20 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:20 INFO root: Running the installer...
07-07 03:20 DEBUG WindowsFrontend: __init__...
07-07 03:20 DEBUG WindowsFrontend: on_init...
07-07 03:20 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_US', 'en']
07-07 03:20 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_US', 'en']
07-07 03:23 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Mythbuntu, language=en_US, locale=en_US.UTF-8, username=manu
07-07 03:23 INFO root: Received settings
07-07 03:23 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_US', 'en']
07-07 03:23 DEBUG TaskList: # Running tasklist...
07-07 03:23 DEBUG TaskList: ## Running select_target_dir...
07-07 03:23 INFO WindowsBackend: Installing into D:\ubuntu
07-07 03:23 DEBUG TaskList: ## Finished select_target_dir
07-07 03:23 DEBUG TaskList: ## Running create_dir_structure...
07-07 03:23 DEBUG CommonBackend: Creating dir D:\ubuntu
07-07 03:23 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
07-07 03:23 DEBUG CommonBackend: Creating dir D:\ubuntu\install
07-07 03:23 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
07-07 03:23 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
07-07 03:23 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-07 03:23 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-07 03:23 DEBUG TaskList: ## Finished create_dir_structure
07-07 03:23 DEBUG TaskList: ## Running uncompress_target_dir...
07-07 03:23 DEBUG TaskList: ## Finished uncompress_target_dir
07-07 03:23 DEBUG TaskList: ## Running create_uninstaller...
07-07 03:23 DEBUG WindowsBackend: Copying uninstaller C:\wubi_2.exe -> D:\ubuntu\uninstall-wubi.exe
07-07 03:23 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-07 03:23 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-07 03:23 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Mythbuntu
07-07 03:23 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Mythbuntu.ico
07-07 03:23 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-07 03:23 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Mythbuntu
07-07 03:23 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.mythbuntu.org](http://www.mythbuntu.org)
07-07 03:23 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-07 03:23 DEBUG TaskList: ## Finished create_uninstaller
07-07 03:23 DEBUG TaskList: ## Running copy_installation_files...
07-07 03:23 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-07 03:23 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\winboot -> D:\ubuntu\winboot
07-07 03:23 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\data\images\Mythbuntu.ico -> D:\ubuntu\Mythbuntu.ico
07-07 03:23 DEBUG TaskList: ## Finished copy_installation_files
07-07 03:23 DEBUG TaskList: ## Running get_iso...
07-07 03:23 DEBUG CommonBackend: Searching for local CD
07-07 03:23 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
07-07 03:23 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
07-07 03:23 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 03:23 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:23 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 03:23 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:23 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 03:23 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:23 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 03:23 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:23 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 03:23 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:23 DEBUG CommonBackend: Searching for local ISO
07-07 03:23 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-07 03:23 DEBUG TaskList: New task get_metalink
07-07 03:23 DEBUG TaskList: ### Running get_metalink...
07-07 03:23 DEBUG downloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
07-07 03:23 DEBUG downloader: Download start filename=D:\ubuntu\install\mythbuntu-10.04-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.metalink, basename=mythbuntu-10.04-desktop-amd64.metalink, length=1050, text=None
07-07 03:23 DEBUG downloader: download finished (read 1050 bytes)
07-07 03:23 DEBUG downloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink) > D:\ubuntu\install
07-07 03:23 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=145, text=None
07-07 03:23 DEBUG downloader: download finished (read 145 bytes)
07-07 03:23 DEBUG downloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-07 03:23 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-07 03:23 DEBUG downloader: download finished (read 189 bytes)
07-07 03:23 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
07-07 03:23 INFO saplog: Checking block bindings..
07-07 03:23 INFO saplog: Key verified successfully.
07-07 03:23 DEBUG CommonBackend: metalink md5sums:
1e39ff0b997440bfb704cbb0e904804d mythbuntu-10.04-desktop-amd64.metalink
7a01310ce5c5ddacc18c03bde99a8125 mythbuntu-10.04-desktop-i386.metalink
07-07 03:23 DEBUG TaskList: ### Finished get_metalink
07-07 03:23 DEBUG TaskList: New task download
07-07 03:23 DEBUG TaskList: ### Running download...
07-07 03:23 DEBUG btdownloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\mythbuntu-10.04-desktop-amd64.iso
07-07 03:27 INFO WindowsFrontend: Operation cancelled
07-07 03:27 DEBUG WindowsFrontend: frontend.quit
07-07 03:27 DEBUG WindowsFrontend: frontend.on_quit
07-07 03:27 DEBUG WindowsFrontend: stopping remaining background tasks: 'tasklist'
07-07 03:27 DEBUG TaskList: # Cancelling tasklist
07-07 03:27 DEBUG TaskList: ### Finished download
07-07 03:27 DEBUG WindowsFrontend: Task cancellation timed out, the program will exit anyway
07-07 03:27 DEBUG root: application.on_quit
07-07 03:27 DEBUG root: Forceful exit
07-07 03:27 INFO root: sys.exit
07-07 03:30 INFO root: === wubi 10.04 rev189 ===
07-07 03:30 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-07 03:30 DEBUG root: sys.argv = ['main.pyo', '--exefile="G:\\Softwares\\Operating Systems\\wubi_2.exe"']
07-07 03:30 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\data
07-07 03:30 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\bin\7z.exe
07-07 03:30 DEBUG CommonBackend: Fetching basic info...
07-07 03:30 DEBUG CommonBackend: original_exe=G:\Softwares\Operating Systems\wubi_2.exe
07-07 03:30 DEBUG CommonBackend: platform=win32
07-07 03:30 DEBUG CommonBackend: osname=nt
07-07 03:30 DEBUG CommonBackend: language=en_US
07-07 03:30 DEBUG CommonBackend: encoding=cp1252
07-07 03:30 DEBUG WindowsBackend: arch=amd64
07-07 03:30 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\data\isolist.ini
07-07 03:30 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-07 03:30 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-07 03:30 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-07 03:30 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-07 03:30 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-07 03:30 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-07 03:30 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-07 03:30 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-07 03:30 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-07 03:30 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-07 03:30 DEBUG WindowsBackend: Fetching host info...
07-07 03:30 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-07 03:30 DEBUG WindowsBackend: windows version=vista
07-07 03:30 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-07 03:30 DEBUG WindowsBackend: windows_sp=None
07-07 03:30 DEBUG WindowsBackend: windows_build=7600
07-07 03:30 DEBUG WindowsBackend: gmt=5
07-07 03:30 DEBUG WindowsBackend: country=US
07-07 03:30 DEBUG WindowsBackend: timezone=America/New_York
07-07 03:30 DEBUG WindowsBackend: windows_username=Manu
07-07 03:30 DEBUG WindowsBackend: user_full_name=Manu
07-07 03:30 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-07 03:30 DEBUG WindowsBackend: windows_language_code=1033
07-07 03:30 DEBUG WindowsBackend: windows_language=English
07-07 03:30 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-07 03:30 DEBUG WindowsBackend: bootloader=vista
07-07 03:30 DEBUG WindowsBackend: system_drive=Drive(C: hd 21308.8398438 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(C: hd 21308.8398438 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(D: hd 47138.3867188 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(G: hd 8690.0390625 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-07 03:30 DEBUG WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-07 03:30 DEBUG WindowsBackend: previous_target_dir=D:\ubuntu
07-07 03:30 DEBUG WindowsBackend: previous_distro_name=Mythbuntu
07-07 03:30 DEBUG WindowsBackend: keyboard_id=67699721
07-07 03:30 DEBUG WindowsBackend: keyboard_layout=us
07-07 03:30 DEBUG WindowsBackend: keyboard_variant=
07-07 03:30 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-07 03:30 DEBUG CommonBackend: locale=en_US.UTF-8
07-07 03:30 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-07 03:30 DEBUG CommonBackend: Searching ISOs on USB devices
07-07 03:30 DEBUG CommonBackend: Searching for local CDs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 INFO root: Already installed, running the uninstaller...
07-07 03:30 INFO root: Running the uninstaller...
07-07 03:30 INFO CommonBackend: This is the uninstaller running
07-07 03:30 DEBUG WindowsFrontend: __init__...
07-07 03:30 DEBUG WindowsFrontend: on_init...
07-07 03:30 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\translations, languages=['en_US', 'en']
07-07 03:30 INFO root: Received settings
07-07 03:30 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\translations, languages=['en_US', 'en']
07-07 03:30 DEBUG TaskList: # Running tasklist...
07-07 03:30 DEBUG TaskList: ## Running Backup ISO...
07-07 03:30 DEBUG TaskList: ## Finished Backup ISO
07-07 03:30 DEBUG TaskList: ## Running Remove bootloader entry...
07-07 03:30 DEBUG WindowsBackend: Could not find bcd id
07-07 03:30 DEBUG WindowsBackend: undo_bootini C:
07-07 03:30 DEBUG WindowsBackend: undo_configsys Drive(C: hd 21308.8398438 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: undo_bootini D:
07-07 03:30 DEBUG WindowsBackend: undo_configsys Drive(D: hd 47138.3867188 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: undo_bootini E:
07-07 03:30 DEBUG WindowsBackend: undo_configsys Drive(E: hd 17628.171875 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: undo_bootini F:
07-07 03:30 DEBUG WindowsBackend: undo_configsys Drive(F: hd 23888.3789063 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: undo_bootini G:
07-07 03:30 DEBUG WindowsBackend: undo_configsys Drive(G: hd 8690.0390625 mb free ntfs)
07-07 03:30 DEBUG TaskList: ## Finished Remove bootloader entry
07-07 03:30 DEBUG TaskList: ## Running Remove target dir...
07-07 03:30 DEBUG CommonBackend: Deleting D:\ubuntu
07-07 03:30 DEBUG TaskList: ## Finished Remove target dir
07-07 03:30 DEBUG TaskList: ## Running Remove registry key...
07-07 03:30 DEBUG TaskList: ## Finished Remove registry key
07-07 03:30 DEBUG TaskList: # Finished tasklist
07-07 03:30 INFO root: Almost finished uninstalling
07-07 03:30 INFO root: Finished uninstallation
07-07 03:30 DEBUG CommonBackend: Fetching basic info...
07-07 03:30 DEBUG CommonBackend: original_exe=G:\Softwares\Operating Systems\wubi_2.exe
07-07 03:30 DEBUG CommonBackend: platform=win32
07-07 03:30 DEBUG CommonBackend: osname=nt
07-07 03:30 DEBUG WindowsBackend: arch=amd64
07-07 03:30 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\data\isolist.ini
07-07 03:30 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-07 03:30 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-07 03:30 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-07 03:30 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-07 03:30 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-07 03:30 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-07 03:30 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-07 03:30 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-07 03:30 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-07 03:30 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-07 03:30 DEBUG WindowsBackend: Fetching host info...
07-07 03:30 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-07 03:30 DEBUG WindowsBackend: windows version=vista
07-07 03:30 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-07 03:30 DEBUG WindowsBackend: windows_sp=None
07-07 03:30 DEBUG WindowsBackend: windows_build=7600
07-07 03:30 DEBUG WindowsBackend: gmt=5
07-07 03:30 DEBUG WindowsBackend: country=US
07-07 03:30 DEBUG WindowsBackend: timezone=America/New_York
07-07 03:30 DEBUG WindowsBackend: windows_username=Manu
07-07 03:30 DEBUG WindowsBackend: user_full_name=Manu
07-07 03:30 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-07 03:30 DEBUG WindowsBackend: windows_language_code=1033
07-07 03:30 DEBUG WindowsBackend: windows_language=English
07-07 03:30 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-07 03:30 DEBUG WindowsBackend: bootloader=vista
07-07 03:30 DEBUG WindowsBackend: system_drive=Drive(C: hd 21308.7148438 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(C: hd 21308.7148438 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(D: hd 47152.921875 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(G: hd 8690.0390625 mb free ntfs)
07-07 03:30 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-07 03:30 DEBUG WindowsBackend: uninstaller_path=None
07-07 03:30 DEBUG WindowsBackend: previous_target_dir=None
07-07 03:30 DEBUG WindowsBackend: previous_distro_name=None
07-07 03:30 DEBUG WindowsBackend: keyboard_id=67699721
07-07 03:30 DEBUG WindowsBackend: keyboard_layout=us
07-07 03:30 DEBUG WindowsBackend: keyboard_variant=
07-07 03:30 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-07 03:30 DEBUG CommonBackend: Searching ISOs on USB devices
07-07 03:30 DEBUG CommonBackend: Searching for local CDs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 INFO root: Running the installer...
07-07 03:30 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\translations, languages=['en_US', 'en']
07-07 03:30 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\translations, languages=['en_US', 'en']
07-07 03:30 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=manu
07-07 03:30 INFO root: Received settings
07-07 03:30 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\translations, languages=['en_US', 'en']
07-07 03:30 DEBUG TaskList: # Running tasklist...
07-07 03:30 DEBUG TaskList: ## Running select_target_dir...
07-07 03:30 INFO WindowsBackend: Installing into D:\ubuntu
07-07 03:30 DEBUG TaskList: ## Finished select_target_dir
07-07 03:30 DEBUG TaskList: ## Running create_dir_structure...
07-07 03:30 DEBUG CommonBackend: Creating dir D:\ubuntu
07-07 03:30 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
07-07 03:30 DEBUG CommonBackend: Creating dir D:\ubuntu\install
07-07 03:30 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
07-07 03:30 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
07-07 03:30 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-07 03:30 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-07 03:30 DEBUG TaskList: ## Finished create_dir_structure
07-07 03:30 DEBUG TaskList: ## Running uncompress_target_dir...
07-07 03:30 DEBUG TaskList: ## Finished uncompress_target_dir
07-07 03:30 DEBUG TaskList: ## Running create_uninstaller...
07-07 03:30 DEBUG WindowsBackend: Copying uninstaller G:\Softwares\Operating Systems\wubi_2.exe -> D:\ubuntu\uninstall-wubi.exe
07-07 03:30 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-07 03:30 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-07 03:30 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-07 03:30 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-07 03:30 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-07 03:30 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-07 03:30 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-07 03:30 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-07 03:30 DEBUG TaskList: ## Finished create_uninstaller
07-07 03:30 DEBUG TaskList: ## Running copy_installation_files...
07-07 03:30 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-07 03:30 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\winboot -> D:\ubuntu\winboot
07-07 03:30 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-07 03:30 DEBUG TaskList: ## Finished copy_installation_files
07-07 03:30 DEBUG TaskList: ## Running get_iso...
07-07 03:30 DEBUG CommonBackend: Searching for local CD
07-07 03:30 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl80E2.tmp\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 03:30 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 03:30 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 03:30 DEBUG CommonBackend: Searching for local ISO
07-07 03:30 DEBUG Distro: checking Ubuntu ISO G:\Softwares\Operating Systems\ubuntu-9.10-desktop-i386.iso
07-07 03:30 DEBUG WindowsBackend: extracting .disk\info from G:\Softwares\Operating Systems\ubuntu-9.10-desktop-i386.iso
07-07 03:30 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-07 03:30 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-07 03:30 DEBUG Distro: wrong version: 9.10 != 10.04
07-07 03:30 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-07 03:30 DEBUG TaskList: New task get_metalink
07-07 03:30 DEBUG TaskList: ### Running get_metalink...
07-07 03:30 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
07-07 03:30 DEBUG downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-07 03:30 DEBUG downloader: download finished (read 7472 bytes)
07-07 03:30 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
07-07 03:30 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-07 03:30 DEBUG downloader: download finished (read 639 bytes)
07-07 03:30 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-07 03:30 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-07 03:30 DEBUG downloader: download finished (read 189 bytes)
07-07 03:30 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
07-07 03:30 INFO saplog: Checking block bindings..
07-07 03:30 INFO saplog: Key verified successfully.
07-07 03:30 DEBUG CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5 ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83 ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882 ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6 ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5 ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0 ubuntu-10.04-server-i386.metalink
07-07 03:30 DEBUG TaskList: ### Finished get_metalink
07-07 03:30 DEBUG TaskList: New task download
07-07 03:30 DEBUG TaskList: ### Running download...
07-07 03:30 DEBUG btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-07 05:01 ERROR TaskList: Traceback (most recent call last):
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
 
07-07 05:01 ERROR TaskList: Non fatal error Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request
in task download
07-07 05:01 DEBUG TaskList: ### Finished download
07-07 05:01 ERROR TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-07 05:01 DEBUG TaskList: # Cancelling tasklist
07-07 05:01 DEBUG TaskList: # Finished tasklist
07-07 05:01 ERROR root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 130, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-07 09:32 INFO root: === wubi 10.04 rev189 ===
07-07 09:32 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-07 09:32 DEBUG root: sys.argv = ['main.pyo', '--exefile="G:\\Softwares\\Operating Systems\\wubi_2.exe"']
07-07 09:32 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\data
07-07 09:32 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\bin\7z.exe
07-07 09:32 DEBUG CommonBackend: Fetching basic info...
07-07 09:32 DEBUG CommonBackend: original_exe=G:\Softwares\Operating Systems\wubi_2.exe
07-07 09:32 DEBUG CommonBackend: platform=win32
07-07 09:32 DEBUG CommonBackend: osname=nt
07-07 09:32 DEBUG CommonBackend: language=en_US
07-07 09:32 DEBUG CommonBackend: encoding=cp1252
07-07 09:32 DEBUG WindowsBackend: arch=amd64
07-07 09:32 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\data\isolist.ini
07-07 09:32 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-07 09:32 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-07 09:32 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-07 09:32 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-07 09:32 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-07 09:32 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-07 09:32 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-07 09:32 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-07 09:32 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-07 09:32 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-07 09:32 DEBUG WindowsBackend: Fetching host info...
07-07 09:32 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-07 09:32 DEBUG WindowsBackend: windows version=vista
07-07 09:32 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-07 09:32 DEBUG WindowsBackend: windows_sp=None
07-07 09:32 DEBUG WindowsBackend: windows_build=7600
07-07 09:32 DEBUG WindowsBackend: gmt=5
07-07 09:32 DEBUG WindowsBackend: country=US
07-07 09:32 DEBUG WindowsBackend: timezone=America/New_York
07-07 09:32 DEBUG WindowsBackend: windows_username=Manu
07-07 09:32 DEBUG WindowsBackend: user_full_name=Manu
07-07 09:32 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-07 09:32 DEBUG WindowsBackend: windows_language_code=1033
07-07 09:32 DEBUG WindowsBackend: windows_language=English
07-07 09:32 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-07 09:32 DEBUG WindowsBackend: bootloader=vista
07-07 09:32 DEBUG WindowsBackend: system_drive=Drive(C: hd 22517.046875 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: drive=Drive(C: hd 22517.046875 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: drive=Drive(D: hd 46531.328125 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: drive=Drive(G: hd 8690.0390625 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-07 09:32 DEBUG WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-07 09:32 DEBUG WindowsBackend: previous_target_dir=D:\ubuntu
07-07 09:32 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-07 09:32 DEBUG WindowsBackend: keyboard_id=67699721
07-07 09:32 DEBUG WindowsBackend: keyboard_layout=us
07-07 09:32 DEBUG WindowsBackend: keyboard_variant=
07-07 09:32 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-07 09:32 DEBUG CommonBackend: locale=en_US.UTF-8
07-07 09:32 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-07 09:32 DEBUG CommonBackend: Searching ISOs on USB devices
07-07 09:32 DEBUG CommonBackend: Searching for local CDs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Ubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Kubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 09:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:32 INFO root: Already installed, running the uninstaller...
07-07 09:32 INFO root: Running the uninstaller...
07-07 09:32 INFO CommonBackend: This is the uninstaller running
07-07 09:32 DEBUG WindowsFrontend: __init__...
07-07 09:32 DEBUG WindowsFrontend: on_init...
07-07 09:32 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\translations, languages=['en_US', 'en']
07-07 09:32 INFO root: Received settings
07-07 09:32 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\translations, languages=['en_US', 'en']
07-07 09:32 DEBUG TaskList: # Running tasklist...
07-07 09:32 DEBUG TaskList: ## Running Backup ISO...
07-07 09:32 DEBUG TaskList: ## Finished Backup ISO
07-07 09:32 DEBUG TaskList: ## Running Remove bootloader entry...
07-07 09:32 DEBUG WindowsBackend: Could not find bcd id
07-07 09:32 DEBUG WindowsBackend: undo_bootini C:
07-07 09:32 DEBUG WindowsBackend: undo_configsys Drive(C: hd 22517.046875 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: undo_bootini D:
07-07 09:32 DEBUG WindowsBackend: undo_configsys Drive(D: hd 46531.328125 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: undo_bootini E:
07-07 09:32 DEBUG WindowsBackend: undo_configsys Drive(E: hd 17628.171875 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: undo_bootini F:
07-07 09:32 DEBUG WindowsBackend: undo_configsys Drive(F: hd 23888.3789063 mb free ntfs)
07-07 09:32 DEBUG WindowsBackend: undo_bootini G:
07-07 09:32 DEBUG WindowsBackend: undo_configsys Drive(G: hd 8690.0390625 mb free ntfs)
07-07 09:32 DEBUG TaskList: ## Finished Remove bootloader entry
07-07 09:32 DEBUG TaskList: ## Running Remove target dir...
07-07 09:32 DEBUG CommonBackend: Deleting D:\ubuntu
07-07 09:33 DEBUG TaskList: ## Finished Remove target dir
07-07 09:33 DEBUG TaskList: ## Running Remove registry key...
07-07 09:33 DEBUG TaskList: ## Finished Remove registry key
07-07 09:33 DEBUG TaskList: # Finished tasklist
07-07 09:33 INFO root: Almost finished uninstalling
07-07 09:33 INFO root: Finished uninstallation
07-07 09:33 DEBUG CommonBackend: Fetching basic info...
07-07 09:33 DEBUG CommonBackend: original_exe=G:\Softwares\Operating Systems\wubi_2.exe
07-07 09:33 DEBUG CommonBackend: platform=win32
07-07 09:33 DEBUG CommonBackend: osname=nt
07-07 09:33 DEBUG WindowsBackend: arch=amd64
07-07 09:33 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\data\isolist.ini
07-07 09:33 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-07 09:33 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-07 09:33 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-07 09:33 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-07 09:33 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-07 09:33 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-07 09:33 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-07 09:33 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-07 09:33 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-07 09:33 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-07 09:33 DEBUG WindowsBackend: Fetching host info...
07-07 09:33 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-07 09:33 DEBUG WindowsBackend: windows version=vista
07-07 09:33 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-07 09:33 DEBUG WindowsBackend: windows_sp=None
07-07 09:33 DEBUG WindowsBackend: windows_build=7600
07-07 09:33 DEBUG WindowsBackend: gmt=5
07-07 09:33 DEBUG WindowsBackend: country=US
07-07 09:33 DEBUG WindowsBackend: timezone=America/New_York
07-07 09:33 DEBUG WindowsBackend: windows_username=Manu
07-07 09:33 DEBUG WindowsBackend: user_full_name=Manu
07-07 09:33 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-07 09:33 DEBUG WindowsBackend: windows_language_code=1033
07-07 09:33 DEBUG WindowsBackend: windows_language=English
07-07 09:33 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-07 09:33 DEBUG WindowsBackend: bootloader=vista
07-07 09:33 DEBUG WindowsBackend: system_drive=Drive(C: hd 22516.9492188 mb free ntfs)
07-07 09:33 DEBUG WindowsBackend: drive=Drive(C: hd 22516.9492188 mb free ntfs)
07-07 09:33 DEBUG WindowsBackend: drive=Drive(D: hd 47153.359375 mb free ntfs)
07-07 09:33 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-07 09:33 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-07 09:33 DEBUG WindowsBackend: drive=Drive(G: hd 8690.0390625 mb free ntfs)
07-07 09:33 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-07 09:33 DEBUG WindowsBackend: uninstaller_path=None
07-07 09:33 DEBUG WindowsBackend: previous_target_dir=None
07-07 09:33 DEBUG WindowsBackend: previous_distro_name=None
07-07 09:33 DEBUG WindowsBackend: keyboard_id=67699721
07-07 09:33 DEBUG WindowsBackend: keyboard_layout=us
07-07 09:33 DEBUG WindowsBackend: keyboard_variant=
07-07 09:33 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-07 09:33 DEBUG CommonBackend: Searching ISOs on USB devices
07-07 09:33 DEBUG CommonBackend: Searching for local CDs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Kubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 INFO root: Running the installer...
07-07 09:33 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\translations, languages=['en_US', 'en']
07-07 09:33 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\translations, languages=['en_US', 'en']
07-07 09:33 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=manu
07-07 09:33 INFO root: Received settings
07-07 09:33 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\translations, languages=['en_US', 'en']
07-07 09:33 DEBUG TaskList: # Running tasklist...
07-07 09:33 DEBUG TaskList: ## Running select_target_dir...
07-07 09:33 INFO WindowsBackend: Installing into D:\ubuntu
07-07 09:33 DEBUG TaskList: ## Finished select_target_dir
07-07 09:33 DEBUG TaskList: ## Running create_dir_structure...
07-07 09:33 DEBUG CommonBackend: Creating dir D:\ubuntu
07-07 09:33 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
07-07 09:33 DEBUG CommonBackend: Creating dir D:\ubuntu\install
07-07 09:33 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
07-07 09:33 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
07-07 09:33 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-07 09:33 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-07 09:33 DEBUG TaskList: ## Finished create_dir_structure
07-07 09:33 DEBUG TaskList: ## Running uncompress_target_dir...
07-07 09:33 DEBUG TaskList: ## Finished uncompress_target_dir
07-07 09:33 DEBUG TaskList: ## Running create_uninstaller...
07-07 09:33 DEBUG WindowsBackend: Copying uninstaller G:\Softwares\Operating Systems\wubi_2.exe -> D:\ubuntu\uninstall-wubi.exe
07-07 09:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-07 09:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-07 09:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
07-07 09:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu Netbook.ico
07-07 09:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-07 09:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
07-07 09:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-07 09:33 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-07 09:33 DEBUG TaskList: ## Finished create_uninstaller
07-07 09:33 DEBUG TaskList: ## Running copy_installation_files...
07-07 09:33 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-07 09:33 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\winboot -> D:\ubuntu\winboot
07-07 09:33 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\data\images\Ubuntu Netbook.ico -> D:\ubuntu\Ubuntu Netbook.ico
07-07 09:33 DEBUG TaskList: ## Finished copy_installation_files
07-07 09:33 DEBUG TaskList: ## Running get_iso...
07-07 09:33 DEBUG CommonBackend: Searching for local CD
07-07 09:33 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pyl7140.tmp\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 09:33 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 09:33 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 09:33 DEBUG CommonBackend: Searching for local ISO
07-07 09:33 DEBUG Distro: checking Ubuntu Netbook ISO G:\Softwares\Operating Systems\ubuntu-9.10-desktop-i386.iso
07-07 09:33 DEBUG WindowsBackend: extracting .disk\info from G:\Softwares\Operating Systems\ubuntu-9.10-desktop-i386.iso
07-07 09:33 DEBUG Distro: parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
07-07 09:33 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
07-07 09:33 DEBUG Distro: wrong name: Ubuntu != Ubuntu Netbook
07-07 09:33 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-07 09:33 DEBUG TaskList: New task get_metalink
07-07 09:33 DEBUG TaskList: ### Running get_metalink...
07-07 09:33 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink) > D:\ubuntu\install
07-07 09:33 DEBUG downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-netbook-i386.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.metalink, basename=ubuntu-10.04-netbook-i386.metalink, length=7420, text=None
07-07 09:33 DEBUG downloader: download finished (read 7420 bytes)
07-07 09:33 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
07-07 09:33 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-07 09:33 DEBUG downloader: download finished (read 639 bytes)
07-07 09:33 DEBUG downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-07 09:33 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-07 09:33 DEBUG downloader: download finished (read 189 bytes)
07-07 09:33 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
07-07 09:33 INFO saplog: Checking block bindings..
07-07 09:33 INFO saplog: Key verified successfully.
07-07 09:33 DEBUG CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5 ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83 ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882 ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6 ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5 ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0 ubuntu-10.04-server-i386.metalink
07-07 09:33 DEBUG TaskList: ### Finished get_metalink
07-07 09:33 DEBUG TaskList: New task download
07-07 09:33 DEBUG TaskList: ### Running download...
07-07 09:33 DEBUG btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-netbook-i386.iso
07-07 11:33 ERROR TaskList: Traceback (most recent call last):
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
 
07-07 11:33 ERROR TaskList: Non fatal error Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
File "\lib\bittorrent\Rerequester.py", line 96, in fail
File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request
in task download
07-07 11:33 DEBUG TaskList: ### Finished download
07-07 11:33 ERROR TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
Traceback (most recent call last):
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
07-07 11:33 DEBUG TaskList: # Cancelling tasklist
07-07 11:33 DEBUG TaskList: # Finished tasklist
07-07 11:33 ERROR root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
Traceback (most recent call last):
File "\lib\wubi\application.py", line 56, in run
File "\lib\wubi\application.py", line 130, in select_task
File "\lib\wubi\application.py", line 156, in run_installer
File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-netbook-i386.iso'
07-07 11:46 INFO root: === wubi 10.04 rev189 ===
07-07 11:46 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-07 11:46 DEBUG root: sys.argv = ['main.pyo', '--exefile="G:\\Softwares\\Operating Systems\\wubi_2.exe"']
07-07 11:46 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\data
07-07 11:46 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\bin\7z.exe
07-07 11:46 DEBUG CommonBackend: Fetching basic info...
07-07 11:46 DEBUG CommonBackend: original_exe=G:\Softwares\Operating Systems\wubi_2.exe
07-07 11:46 DEBUG CommonBackend: platform=win32
07-07 11:46 DEBUG CommonBackend: osname=nt
07-07 11:46 DEBUG CommonBackend: language=en_US
07-07 11:46 DEBUG CommonBackend: encoding=cp1252
07-07 11:46 DEBUG WindowsBackend: arch=amd64
07-07 11:46 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\data\isolist.ini
07-07 11:46 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-07 11:46 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-07 11:46 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-07 11:46 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-07 11:46 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-07 11:46 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-07 11:46 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-07 11:46 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-07 11:46 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-07 11:46 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-07 11:46 DEBUG WindowsBackend: Fetching host info...
07-07 11:46 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-07 11:46 DEBUG WindowsBackend: windows version=vista
07-07 11:46 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-07 11:46 DEBUG WindowsBackend: windows_sp=None
07-07 11:46 DEBUG WindowsBackend: windows_build=7600
07-07 11:46 DEBUG WindowsBackend: gmt=5
07-07 11:46 DEBUG WindowsBackend: country=US
07-07 11:46 DEBUG WindowsBackend: timezone=America/New_York
07-07 11:46 DEBUG WindowsBackend: windows_username=Manu
07-07 11:46 DEBUG WindowsBackend: user_full_name=Manu
07-07 11:46 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-07 11:46 DEBUG WindowsBackend: windows_language_code=1033
07-07 11:46 DEBUG WindowsBackend: windows_language=English
07-07 11:46 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-07 11:46 DEBUG WindowsBackend: bootloader=vista
07-07 11:46 DEBUG WindowsBackend: system_drive=Drive(C: hd 21687.2578125 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(C: hd 21687.2578125 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(D: hd 46712.2617188 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(G: hd 8690.0390625 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-07 11:46 DEBUG WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-07 11:46 DEBUG WindowsBackend: previous_target_dir=D:\ubuntu
07-07 11:46 DEBUG WindowsBackend: previous_distro_name=Ubuntu Netbook
07-07 11:46 DEBUG WindowsBackend: keyboard_id=67699721
07-07 11:46 DEBUG WindowsBackend: keyboard_layout=us
07-07 11:46 DEBUG WindowsBackend: keyboard_variant=
07-07 11:46 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-07 11:46 DEBUG CommonBackend: locale=en_US.UTF-8
07-07 11:46 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-07 11:46 DEBUG CommonBackend: Searching ISOs on USB devices
07-07 11:46 DEBUG CommonBackend: Searching for local CDs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 INFO root: Already installed, running the uninstaller...
07-07 11:46 INFO root: Running the uninstaller...
07-07 11:46 INFO CommonBackend: This is the uninstaller running
07-07 11:46 DEBUG WindowsFrontend: __init__...
07-07 11:46 DEBUG WindowsFrontend: on_init...
07-07 11:46 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\translations, languages=['en_US', 'en']
07-07 11:46 INFO root: Received settings
07-07 11:46 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\translations, languages=['en_US', 'en']
07-07 11:46 DEBUG TaskList: # Running tasklist...
07-07 11:46 DEBUG TaskList: ## Running Backup ISO...
07-07 11:46 DEBUG TaskList: ## Finished Backup ISO
07-07 11:46 DEBUG TaskList: ## Running Remove bootloader entry...
07-07 11:46 DEBUG WindowsBackend: Could not find bcd id
07-07 11:46 DEBUG WindowsBackend: undo_bootini C:
07-07 11:46 DEBUG WindowsBackend: undo_configsys Drive(C: hd 21687.2578125 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: undo_bootini D:
07-07 11:46 DEBUG WindowsBackend: undo_configsys Drive(D: hd 46712.2617188 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: undo_bootini E:
07-07 11:46 DEBUG WindowsBackend: undo_configsys Drive(E: hd 17628.171875 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: undo_bootini F:
07-07 11:46 DEBUG WindowsBackend: undo_configsys Drive(F: hd 23888.3789063 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: undo_bootini G:
07-07 11:46 DEBUG WindowsBackend: undo_configsys Drive(G: hd 8690.0390625 mb free ntfs)
07-07 11:46 DEBUG TaskList: ## Finished Remove bootloader entry
07-07 11:46 DEBUG TaskList: ## Running Remove target dir...
07-07 11:46 DEBUG CommonBackend: Deleting D:\ubuntu
07-07 11:46 DEBUG TaskList: ## Finished Remove target dir
07-07 11:46 DEBUG TaskList: ## Running Remove registry key...
07-07 11:46 DEBUG TaskList: ## Finished Remove registry key
07-07 11:46 DEBUG TaskList: # Finished tasklist
07-07 11:46 INFO root: Almost finished uninstalling
07-07 11:46 INFO root: Finished uninstallation
07-07 11:46 DEBUG CommonBackend: Fetching basic info...
07-07 11:46 DEBUG CommonBackend: original_exe=G:\Softwares\Operating Systems\wubi_2.exe
07-07 11:46 DEBUG CommonBackend: platform=win32
07-07 11:46 DEBUG CommonBackend: osname=nt
07-07 11:46 DEBUG WindowsBackend: arch=amd64
07-07 11:46 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\data\isolist.ini
07-07 11:46 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-07 11:46 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-07 11:46 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-07 11:46 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-07 11:46 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-07 11:46 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-07 11:46 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-07 11:46 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-07 11:46 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-07 11:46 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-07 11:46 DEBUG WindowsBackend: Fetching host info...
07-07 11:46 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-07 11:46 DEBUG WindowsBackend: windows version=vista
07-07 11:46 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-07 11:46 DEBUG WindowsBackend: windows_sp=None
07-07 11:46 DEBUG WindowsBackend: windows_build=7600
07-07 11:46 DEBUG WindowsBackend: gmt=5
07-07 11:46 DEBUG WindowsBackend: country=US
07-07 11:46 DEBUG WindowsBackend: timezone=America/New_York
07-07 11:46 DEBUG WindowsBackend: windows_username=Manu
07-07 11:46 DEBUG WindowsBackend: user_full_name=Manu
07-07 11:46 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-07 11:46 DEBUG WindowsBackend: windows_language_code=1033
07-07 11:46 DEBUG WindowsBackend: windows_language=English
07-07 11:46 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-07 11:46 DEBUG WindowsBackend: bootloader=vista
07-07 11:46 DEBUG WindowsBackend: system_drive=Drive(C: hd 21687.1601563 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(C: hd 21687.1601563 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(D: hd 47153.296875 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(G: hd 8690.0390625 mb free ntfs)
07-07 11:46 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-07 11:46 DEBUG WindowsBackend: uninstaller_path=None
07-07 11:46 DEBUG WindowsBackend: previous_target_dir=None
07-07 11:46 DEBUG WindowsBackend: previous_distro_name=None
07-07 11:46 DEBUG WindowsBackend: keyboard_id=67699721
07-07 11:46 DEBUG WindowsBackend: keyboard_layout=us
07-07 11:46 DEBUG WindowsBackend: keyboard_variant=
07-07 11:46 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-07 11:46 DEBUG CommonBackend: Searching ISOs on USB devices
07-07 11:46 DEBUG CommonBackend: Searching for local CDs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylE153.tmp is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 11:46 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 11:46 INFO root: Running the installer...
07-07 11:46 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\translations, languages=['en_US', 'en']
07-07 11:46 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylE153.tmp\translations, languages=['en_US', 'en']
07-07 11:47 DEBUG WindowsFrontend: frontend.on_quit
07-07 11:47 DEBUG root: application.on_quit
07-07 11:47 INFO root: sys.exit
07-07 13:31 INFO root: === wubi 10.04 rev189 ===
07-07 13:31 DEBUG root: Logfile is c:\users\manu\appdata\local\temp\wubi-10.04-rev189.log
07-07 13:31 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
07-07 13:31 DEBUG CommonBackend: data_dir=C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\data
07-07 13:31 DEBUG WindowsBackend: 7z=C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\bin\7z.exe
07-07 13:31 DEBUG CommonBackend: Fetching basic info...
07-07 13:31 DEBUG CommonBackend: original_exe=C:\wubi.exe
07-07 13:31 DEBUG CommonBackend: platform=win32
07-07 13:31 DEBUG CommonBackend: osname=nt
07-07 13:31 DEBUG CommonBackend: language=en_US
07-07 13:31 DEBUG CommonBackend: encoding=cp1252
07-07 13:31 DEBUG WindowsBackend: arch=amd64
07-07 13:31 DEBUG CommonBackend: Parsing isolist=C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\data\isolist.ini
07-07 13:31 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-07 13:31 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-07 13:31 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-07 13:31 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-07 13:31 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-07 13:31 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-07 13:31 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-07 13:31 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-07 13:31 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-07 13:31 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-07 13:31 DEBUG WindowsBackend: Fetching host info...
07-07 13:31 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-07 13:31 DEBUG WindowsBackend: windows version=vista
07-07 13:31 DEBUG WindowsBackend: windows_version2=Windows 7 Ultimate
07-07 13:31 DEBUG WindowsBackend: windows_sp=None
07-07 13:31 DEBUG WindowsBackend: windows_build=7600
07-07 13:31 DEBUG WindowsBackend: gmt=5
07-07 13:31 DEBUG WindowsBackend: country=US
07-07 13:31 DEBUG WindowsBackend: timezone=America/New_York
07-07 13:31 DEBUG WindowsBackend: windows_username=Manu
07-07 13:31 DEBUG WindowsBackend: user_full_name=Manu
07-07 13:31 DEBUG WindowsBackend: user_directory=C:\Users\Manu
07-07 13:31 DEBUG WindowsBackend: windows_language_code=1033
07-07 13:31 DEBUG WindowsBackend: windows_language=English
07-07 13:31 DEBUG WindowsBackend: processor_name=Intel(R) Pentium(R) Dual CPU T3200 @ 2.00GHz
07-07 13:31 DEBUG WindowsBackend: bootloader=vista
07-07 13:31 DEBUG WindowsBackend: system_drive=Drive(C: hd 21645.7109375 mb free ntfs)
07-07 13:31 DEBUG WindowsBackend: drive=Drive(C: hd 21645.7070313 mb free ntfs)
07-07 13:31 DEBUG WindowsBackend: drive=Drive(D: hd 47153.421875 mb free ntfs)
07-07 13:31 DEBUG WindowsBackend: drive=Drive(E: hd 17628.171875 mb free ntfs)
07-07 13:31 DEBUG WindowsBackend: drive=Drive(F: hd 23888.3789063 mb free ntfs)
07-07 13:31 DEBUG WindowsBackend: drive=Drive(G: hd 8690.0703125 mb free ntfs)
07-07 13:31 DEBUG WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-07 13:31 DEBUG WindowsBackend: uninstaller_path=None
07-07 13:31 DEBUG WindowsBackend: previous_target_dir=None
07-07 13:31 DEBUG WindowsBackend: previous_distro_name=None
07-07 13:31 DEBUG WindowsBackend: keyboard_id=67699721
07-07 13:31 DEBUG WindowsBackend: keyboard_layout=us
07-07 13:31 DEBUG WindowsBackend: keyboard_variant=
07-07 13:31 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-07 13:31 DEBUG CommonBackend: locale=en_US.UTF-8
07-07 13:31 DEBUG WindowsBackend: total_memory_mb=3999.19140625
07-07 13:31 DEBUG CommonBackend: Searching ISOs on USB devices
07-07 13:31 DEBUG CommonBackend: Searching for local CDs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Ubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Kubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Ubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Kubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Ubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Kubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Ubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Kubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Ubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Kubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Ubuntu CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Ubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Kubuntu CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Kubuntu Netbook CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Xubuntu CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 13:31 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:31 INFO root: Running the installer...
07-07 13:31 DEBUG WindowsFrontend: __init__...
07-07 13:31 DEBUG WindowsFrontend: on_init...
07-07 13:31 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\translations, languages=['en_US', 'en']
07-07 13:31 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\translations, languages=['en_US', 'en']
07-07 13:32 DEBUG WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Mythbuntu, language=en_US, locale=en_US.UTF-8, username=manu
07-07 13:32 INFO root: Received settings
07-07 13:32 INFO WinuiPage: appname=wubi, localedir=C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\translations, languages=['en_US', 'en']
07-07 13:32 DEBUG TaskList: # Running tasklist...
07-07 13:32 DEBUG TaskList: ## Running select_target_dir...
07-07 13:32 INFO WindowsBackend: Installing into D:\ubuntu
07-07 13:32 DEBUG TaskList: ## Finished select_target_dir
07-07 13:32 DEBUG TaskList: ## Running create_dir_structure...
07-07 13:32 DEBUG CommonBackend: Creating dir D:\ubuntu
07-07 13:32 DEBUG CommonBackend: Creating dir D:\ubuntu\disks
07-07 13:32 DEBUG CommonBackend: Creating dir D:\ubuntu\install
07-07 13:32 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot
07-07 13:32 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot
07-07 13:32 DEBUG CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-07 13:32 DEBUG CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-07 13:32 DEBUG TaskList: ## Finished create_dir_structure
07-07 13:32 DEBUG TaskList: ## Running uncompress_target_dir...
07-07 13:32 DEBUG TaskList: ## Finished uncompress_target_dir
07-07 13:32 DEBUG TaskList: ## Running create_uninstaller...
07-07 13:32 DEBUG WindowsBackend: Copying uninstaller C:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-07 13:32 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-07 13:32 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-07 13:32 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Mythbuntu
07-07 13:32 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Mythbuntu.ico
07-07 13:32 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-07 13:32 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Mythbuntu
07-07 13:32 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.mythbuntu.org](http://www.mythbuntu.org)
07-07 13:32 DEBUG registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-07 13:32 DEBUG TaskList: ## Finished create_uninstaller
07-07 13:32 DEBUG TaskList: ## Running copy_installation_files...
07-07 13:32 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-07 13:32 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\winboot -> D:\ubuntu\winboot
07-07 13:32 DEBUG WindowsBackend: Copying C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\data\images\Mythbuntu.ico -> D:\ubuntu\Mythbuntu.ico
07-07 13:32 DEBUG TaskList: ## Finished copy_installation_files
07-07 13:32 DEBUG TaskList: ## Running get_iso...
07-07 13:32 DEBUG CommonBackend: Searching for local CD
07-07 13:32 DEBUG Distro: checking whether C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp is a valid Mythbuntu CD
07-07 13:32 DEBUG Distro: does not contain C:\Users\Manu\AppData\Local\Temp\pylBF98.tmp\casper\filesystem.squashfs
07-07 13:32 DEBUG Distro: checking whether D:\ is a valid Mythbuntu CD
07-07 13:32 DEBUG Distro: does not contain D:\casper\filesystem.squashfs
07-07 13:32 DEBUG Distro: checking whether E:\ is a valid Mythbuntu CD
07-07 13:32 DEBUG Distro: does not contain E:\casper\filesystem.squashfs
07-07 13:32 DEBUG Distro: checking whether F:\ is a valid Mythbuntu CD
07-07 13:32 DEBUG Distro: does not contain F:\casper\filesystem.squashfs
07-07 13:32 DEBUG Distro: checking whether G:\ is a valid Mythbuntu CD
07-07 13:32 DEBUG Distro: does not contain G:\casper\filesystem.squashfs
07-07 13:32 DEBUG Distro: checking whether H:\ is a valid Mythbuntu CD
07-07 13:32 DEBUG Distro: does not contain H:\casper\filesystem.squashfs
07-07 13:32 DEBUG CommonBackend: Searching for local ISO
07-07 13:32 DEBUG CommonBackend: Could not find any ISO or CD, downloading one now
07-07 13:32 DEBUG TaskList: New task get_metalink
07-07 13:32 DEBUG TaskList: ### Running get_metalink...
07-07 13:32 DEBUG downloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
07-07 13:32 DEBUG downloader: Download start filename=D:\ubuntu\install\mythbuntu-10.04-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.metalink, basename=mythbuntu-10.04-desktop-amd64.metalink, length=1050, text=None
07-07 13:32 DEBUG downloader: download finished (read 1050 bytes)
07-07 13:32 DEBUG downloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink) > D:\ubuntu\install
07-07 13:32 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=145, text=None
07-07 13:32 DEBUG downloader: download finished (read 145 bytes)
07-07 13:32 DEBUG downloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-07 13:32 DEBUG downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-07 13:32 DEBUG downloader: download finished (read 189 bytes)
07-07 13:32 INFO saplog: Verified a signature from ID:'46181433FBB75451'.
07-07 13:32 INFO saplog: Checking block bindings..
07-07 13:32 INFO saplog: Key verified successfully.
07-07 13:32 DEBUG CommonBackend: metalink md5sums:
1e39ff0b997440bfb704cbb0e904804d mythbuntu-10.04-desktop-amd64.metalink
7a01310ce5c5ddacc18c03bde99a8125 mythbuntu-10.04-desktop-i386.metalink
07-07 13:32 DEBUG TaskList: ### Finished get_metalink
07-07 13:32 DEBUG TaskList: New task download
07-07 13:32 DEBUG TaskList: ### Running download...
07-07 13:32 DEBUG btdownloader: downloading [http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/mythbuntu/releases/10.04/release/mythbuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\mythbuntu-10.04-desktop-amd64.iso
07-07 13:32 INFO WindowsFrontend: Operation cancelled
07-07 13:32 DEBUG WindowsFrontend: frontend.quit
07-07 13:32 DEBUG WindowsFrontend: frontend.on_quit
07-07 13:32 DEBUG WindowsFrontend: stopping remaining background tasks: 'tasklist'
07-07 13:32 DEBUG TaskList: # Cancelling tasklist
07-07 13:32 DEBUG TaskList: ### Finished download
07-07 13:32 DEBUG WindowsFrontend: Task cancellation timed out, the program will exit anyway
07-07 13:32 DEBUG root: application.on_quit
07-07 13:32 DEBUG root: Forceful exit
07-07 13:32 INFO root: sys.exit

---

### Post by dino99 on 2010-07-07
make a real install if you want something serious:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by withmanu on 2010-07-07
Im trying to install the Wubi, on Windows 7. I dont need to have a seperate installation for Ubuntu

---

### Post by dino99 on 2010-07-07
so look here:

[http://www.clububuntu.com/2009/01/how-to-solve-windows-7-and-ubuntu-810.html](http://www.clububuntu.com/2009/01/how-to-solve-windows-7-and-ubuntu-810.html)

---

### Post by withmanu on 2010-07-07
I have tried the same, but got a permission denied error again just before the installion got finished .. Im really frustrated.. :-(

---

### Post by Rubi1200 on 2010-07-07
Hi withmanu,
I do not know that much about Wubi installation errors, but I did find this post on the forum:

[http://ubuntuforums.org/showpost.php?p=9323362&postcount=16](http://ubuntuforums.org/showpost.php?p=9323362&postcount=16)

Have a look and see if this resolves your problem.

---

### Post by withmanu on 2010-07-07
Great Rubi.. I think this must be the actual issue.. let me try installing it after unhiding the Application data folder..  Thnx alot

---

### Post by Rubi1200 on 2010-07-07
No problem, let us know if it works and you manage to install 10.04 with Wubi.

---

### Post by withmanu on 2010-07-08
I could install wubi successfully... Thnx for all your support

---

