---
title: "Wubi Install 10.10 x64"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by CoryVenditti on 2011-01-07
Hello,

I understand this is a common problem but i can't seem to find a solution for it other than use gparted to partition your hard drive and install directly to the hard drive.

I am trying to load 10.10 through the wubi installer. I want to install the 64 bit version of ubuntu. My windows OS is 64 bit as well. 

I download the wubi online and when i run it i get through the first step of picking how large i want the hard drive and my sudo password. I click next and it goes to download the 10.10 x64 ISO. After about 10 sec a firewall alert comes up and i say allow then right after that the wubi crashes and i get an error log that i will post below saying i dont have permissions. Ive also tried using the right click "run as administrator" option on the wubi from windows 7. 

Ive also tried downloading the ubuntu 10.10 x64 desktop iso. i extracted it using winrar then ran the wubi that comes with that and i get the same issue. I find it funny that when your run the wubi from the install disk it still downloads another copy of the iso instead of asking for its location on your hard drive.

I like the concept of the wubi and i had previously installed 10.04 through the wubi and loved it. I had an issue with 10.04 after doing a lot of tweaking and I simply wanted to just remove it and install 10.10 fresh. I'm strictly using ubuntu for experimental and learning purposes so i dont want to install it directly to my hard drive.

-----------------------------------------------------------------
WUBI ERROR LOG
|
01-07 10:58 INFO   root: === wubi 10.10 rev197 ===
01-07 10:58 DEBUG  root: Logfile is c:\users\cory\appdata\local\temp\wubi-10.10-rev197.log
01-07 10:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Shared\\wubi.exe"']
01-07 10:58 DEBUG  CommonBackend: data_dir=C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\data
01-07 10:58 DEBUG  WindowsBackend: 7z=C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\bin\7z.exe
01-07 10:58 DEBUG  CommonBackend: Fetching basic info...
01-07 10:58 DEBUG  CommonBackend: original_exe=C:\Shared\wubi.exe
01-07 10:58 DEBUG  CommonBackend: platform=win32
01-07 10:58 DEBUG  CommonBackend: osname=nt
01-07 10:58 DEBUG  CommonBackend: language=en_US
01-07 10:58 DEBUG  CommonBackend: encoding=cp1252
01-07 10:58 DEBUG  WindowsBackend: arch=amd64
01-07 10:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\data\isolist.ini
01-07 10:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-07 10:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-07 10:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-07 10:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-07 10:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-07 10:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-07 10:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-07 10:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-07 10:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-07 10:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-07 10:58 DEBUG  WindowsBackend: Fetching host info...
01-07 10:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-07 10:58 DEBUG  WindowsBackend: windows version=vista
01-07 10:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-07 10:58 DEBUG  WindowsBackend: windows_sp=None
01-07 10:58 DEBUG  WindowsBackend: windows_build=7600
01-07 10:58 DEBUG  WindowsBackend: gmt=-5
01-07 10:58 DEBUG  WindowsBackend: country=US
01-07 10:58 DEBUG  WindowsBackend: timezone=America/New_York
01-07 10:58 DEBUG  WindowsBackend: windows_username=Cory
01-07 10:58 DEBUG  WindowsBackend: user_full_name=Cory
01-07 10:58 DEBUG  WindowsBackend: user_directory=C:\Users\Cory
01-07 10:58 DEBUG  WindowsBackend: windows_language_code=1033
01-07 10:58 DEBUG  WindowsBackend: windows_language=English
01-07 10:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
01-07 10:58 DEBUG  WindowsBackend: bootloader=vista
01-07 10:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 297956.179688 mb free ntfs)
01-07 10:58 DEBUG  WindowsBackend: drive=Drive(C: hd 297956.179688 mb free ntfs)
01-07 10:58 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-07 10:58 DEBUG  WindowsBackend: uninstaller_path=None
01-07 10:58 DEBUG  WindowsBackend: previous_target_dir=None
01-07 10:58 DEBUG  WindowsBackend: previous_distro_name=None
01-07 10:58 DEBUG  WindowsBackend: keyboard_id=67699721
01-07 10:58 DEBUG  WindowsBackend: keyboard_layout=us
01-07 10:58 DEBUG  WindowsBackend: keyboard_variant=
01-07 10:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-07 10:58 DEBUG  CommonBackend: locale=en_US.UTF-8
01-07 10:58 DEBUG  WindowsBackend: total_memory_mb=4056.55859375
01-07 10:58 DEBUG  CommonBackend: Searching ISOs on USB devices
01-07 10:58 DEBUG  CommonBackend: Searching for local CDs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Ubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Ubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Ubuntu Netbook CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Kubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Kubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Kubuntu Netbook CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Xubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Xubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Mythbuntu CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Mythbuntu CD
01-07 10:58 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 10:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:58 INFO   root: Running the installer...
01-07 10:58 DEBUG  WindowsFrontend: __init__...
01-07 10:58 DEBUG  WindowsFrontend: on_init...
01-07 10:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\translations, languages=['en_US', 'en']
01-07 10:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\translations, languages=['en_US', 'en']
01-07 10:59 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=cory
01-07 10:59 INFO   root: Received settings
01-07 10:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\translations, languages=['en_US', 'en']
01-07 10:59 DEBUG  TaskList: # Running tasklist...
01-07 10:59 DEBUG  TaskList: ## Running select_target_dir...
01-07 10:59 INFO   WindowsBackend: Installing into C:\ubuntu
01-07 10:59 DEBUG  TaskList: ## Finished select_target_dir
01-07 10:59 DEBUG  TaskList: ## Running create_dir_structure...
01-07 10:59 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-07 10:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-07 10:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-07 10:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-07 10:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-07 10:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-07 10:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-07 10:59 DEBUG  TaskList: ## Finished create_dir_structure
01-07 10:59 DEBUG  TaskList: ## Running uncompress_target_dir...
01-07 10:59 DEBUG  TaskList: ## Finished uncompress_target_dir
01-07 10:59 DEBUG  TaskList: ## Running create_uninstaller...
01-07 10:59 DEBUG  WindowsBackend: Copying uninstaller C:\Shared\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-07 10:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-07 10:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-07 10:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-07 10:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-07 10:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-07 10:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-07 10:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-07 10:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-07 10:59 DEBUG  TaskList: ## Finished create_uninstaller
01-07 10:59 DEBUG  TaskList: ## Running copy_installation_files...
01-07 10:59 DEBUG  WindowsBackend: Copying C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-07 10:59 DEBUG  WindowsBackend: Copying C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\winboot -> C:\ubuntu\winboot
01-07 10:59 DEBUG  WindowsBackend: Copying C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-07 10:59 DEBUG  TaskList: ## Finished copy_installation_files
01-07 10:59 DEBUG  TaskList: ## Running get_iso...
01-07 10:59 DEBUG  CommonBackend: Searching for local CD
01-07 10:59 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp is a valid Ubuntu CD
01-07 10:59 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pylF6FB.tmp\casper\filesystem.squashfs
01-07 10:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 10:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 10:59 DEBUG  CommonBackend: Searching for local ISO
01-07 10:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-07 10:59 DEBUG  TaskList: New task get_metalink
01-07 10:59 DEBUG  TaskList: ### Running get_metalink...
01-07 10:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink) > C:\ubuntu\install
01-07 10:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
01-07 10:59 DEBUG  downloader: download finished (read 9135 bytes)
01-07 10:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
01-07 10:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
01-07 10:59 DEBUG  downloader: download finished (read 488 bytes)
01-07 10:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
01-07 10:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
01-07 10:59 DEBUG  downloader: download finished (read 198 bytes)
01-07 10:59 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
01-07 10:59 INFO   saplog: Checking block bindings..
01-07 10:59 INFO   saplog: Key verified successfully.
01-07 10:59 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

01-07 10:59 DEBUG  TaskList: ### Finished get_metalink
01-07 10:59 DEBUG  TaskList: New task download
01-07 10:59 DEBUG  TaskList: ### Running download...
01-07 10:59 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
01-07 10:59 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

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
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>


01-07 10:59 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

 in task download
01-07 10:59 DEBUG  TaskList: ### Finished download
01-07 10:59 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
01-07 10:59 DEBUG  TaskList: # Cancelling tasklist
01-07 10:59 DEBUG  TaskList: # Finished tasklist
01-07 10:59 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
01-07 11:00 INFO   root: === wubi 10.10 rev197 ===
01-07 11:00 DEBUG  root: Logfile is c:\users\cory\appdata\local\temp\wubi-10.10-rev197.log
01-07 11:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
01-07 11:00 DEBUG  CommonBackend: data_dir=C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\data
01-07 11:00 DEBUG  WindowsBackend: 7z=C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\bin\7z.exe
01-07 11:00 DEBUG  CommonBackend: Fetching basic info...
01-07 11:00 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
01-07 11:00 DEBUG  CommonBackend: platform=win32
01-07 11:00 DEBUG  CommonBackend: osname=nt
01-07 11:00 DEBUG  CommonBackend: language=en_US
01-07 11:00 DEBUG  CommonBackend: encoding=cp1252
01-07 11:00 DEBUG  WindowsBackend: arch=amd64
01-07 11:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\data\isolist.ini
01-07 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-07 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-07 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-07 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-07 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-07 11:00 DEBUG  WindowsBackend: Fetching host info...
01-07 11:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-07 11:00 DEBUG  WindowsBackend: windows version=vista
01-07 11:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-07 11:00 DEBUG  WindowsBackend: windows_sp=None
01-07 11:00 DEBUG  WindowsBackend: windows_build=7600
01-07 11:00 DEBUG  WindowsBackend: gmt=-5
01-07 11:00 DEBUG  WindowsBackend: country=US
01-07 11:00 DEBUG  WindowsBackend: timezone=America/New_York
01-07 11:00 DEBUG  WindowsBackend: windows_username=Cory
01-07 11:00 DEBUG  WindowsBackend: user_full_name=Cory
01-07 11:00 DEBUG  WindowsBackend: user_directory=C:\Users\Cory
01-07 11:00 DEBUG  WindowsBackend: windows_language_code=1033
01-07 11:00 DEBUG  WindowsBackend: windows_language=English
01-07 11:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
01-07 11:00 DEBUG  WindowsBackend: bootloader=vista
01-07 11:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 297955.105469 mb free ntfs)
01-07 11:00 DEBUG  WindowsBackend: drive=Drive(C: hd 297955.105469 mb free ntfs)
01-07 11:00 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-07 11:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-07 11:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-07 11:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-07 11:00 DEBUG  WindowsBackend: keyboard_id=67699721
01-07 11:00 DEBUG  WindowsBackend: keyboard_layout=us
01-07 11:00 DEBUG  WindowsBackend: keyboard_variant=
01-07 11:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-07 11:00 DEBUG  CommonBackend: locale=en_US.UTF-8
01-07 11:00 DEBUG  WindowsBackend: total_memory_mb=4056.55859375
01-07 11:00 DEBUG  CommonBackend: Searching ISOs on USB devices
01-07 11:00 DEBUG  CommonBackend: Searching for local CDs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Ubuntu Netbook CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Kubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Kubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Kubuntu Netbook CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Xubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Xubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Mythbuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp is a valid Mythbuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 INFO   root: Running the uninstaller...
01-07 11:00 INFO   CommonBackend: This is the uninstaller running
01-07 11:00 DEBUG  WindowsFrontend: __init__...
01-07 11:00 DEBUG  WindowsFrontend: on_init...
01-07 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\translations, languages=['en_US', 'en']
01-07 11:00 INFO   root: Received settings
01-07 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\translations, languages=['en_US', 'en']
01-07 11:00 DEBUG  TaskList: # Running tasklist...
01-07 11:00 DEBUG  TaskList: ## Running Backup ISO...
01-07 11:00 DEBUG  TaskList: ## Finished Backup ISO
01-07 11:00 DEBUG  TaskList: ## Running Remove bootloader entry...
01-07 11:00 DEBUG  WindowsBackend: Could not find bcd id
01-07 11:00 DEBUG  WindowsBackend: undo_bootini C:
01-07 11:00 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 297955.105469 mb free ntfs)
01-07 11:00 DEBUG  TaskList: ## Finished Remove bootloader entry
01-07 11:00 DEBUG  TaskList: ## Running Remove target dir...
01-07 11:00 DEBUG  CommonBackend: Deleting C:\ubuntu
01-07 11:00 DEBUG  TaskList: ## Finished Remove target dir
01-07 11:00 DEBUG  TaskList: ## Running Remove registry key...
01-07 11:00 DEBUG  TaskList: ## Finished Remove registry key
01-07 11:00 DEBUG  TaskList: # Finished tasklist
01-07 11:00 INFO   root: Almost finished uninstalling
01-07 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pyl1CF2.tmp\translations, languages=['en_US', 'en']
01-07 11:00 INFO   root: Finished uninstallation
01-07 11:00 DEBUG  root: application.quit
01-07 11:00 DEBUG  WindowsFrontend: frontend.quit
01-07 11:00 DEBUG  WindowsFrontend: frontend.on_quit
01-07 11:00 DEBUG  root: application.on_quit
01-07 11:00 INFO   root: sys.exit
01-07 11:00 INFO   root: === wubi 10.10 rev197 ===
01-07 11:00 DEBUG  root: Logfile is c:\users\cory\appdata\local\temp\wubi-10.10-rev197.log
01-07 11:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Shared\\wubi.exe"']
01-07 11:00 DEBUG  CommonBackend: data_dir=C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\data
01-07 11:00 DEBUG  WindowsBackend: 7z=C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\bin\7z.exe
01-07 11:00 DEBUG  CommonBackend: Fetching basic info...
01-07 11:00 DEBUG  CommonBackend: original_exe=C:\Shared\wubi.exe
01-07 11:00 DEBUG  CommonBackend: platform=win32
01-07 11:00 DEBUG  CommonBackend: osname=nt
01-07 11:00 DEBUG  CommonBackend: language=en_US
01-07 11:00 DEBUG  CommonBackend: encoding=cp1252
01-07 11:00 DEBUG  WindowsBackend: arch=amd64
01-07 11:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\data\isolist.ini
01-07 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-07 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-07 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-07 11:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-07 11:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-07 11:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-07 11:00 DEBUG  WindowsBackend: Fetching host info...
01-07 11:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-07 11:00 DEBUG  WindowsBackend: windows version=vista
01-07 11:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
01-07 11:00 DEBUG  WindowsBackend: windows_sp=None
01-07 11:00 DEBUG  WindowsBackend: windows_build=7600
01-07 11:00 DEBUG  WindowsBackend: gmt=-5
01-07 11:00 DEBUG  WindowsBackend: country=US
01-07 11:00 DEBUG  WindowsBackend: timezone=America/New_York
01-07 11:00 DEBUG  WindowsBackend: windows_username=Cory
01-07 11:00 DEBUG  WindowsBackend: user_full_name=Cory
01-07 11:00 DEBUG  WindowsBackend: user_directory=C:\Users\Cory
01-07 11:00 DEBUG  WindowsBackend: windows_language_code=1033
01-07 11:00 DEBUG  WindowsBackend: windows_language=English
01-07 11:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5800  @ 2.00GHz
01-07 11:00 DEBUG  WindowsBackend: bootloader=vista
01-07 11:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 297957.675781 mb free ntfs)
01-07 11:00 DEBUG  WindowsBackend: drive=Drive(C: hd 297957.675781 mb free ntfs)
01-07 11:00 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
01-07 11:00 DEBUG  WindowsBackend: uninstaller_path=None
01-07 11:00 DEBUG  WindowsBackend: previous_target_dir=None
01-07 11:00 DEBUG  WindowsBackend: previous_distro_name=None
01-07 11:00 DEBUG  WindowsBackend: keyboard_id=67699721
01-07 11:00 DEBUG  WindowsBackend: keyboard_layout=us
01-07 11:00 DEBUG  WindowsBackend: keyboard_variant=
01-07 11:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
01-07 11:00 DEBUG  CommonBackend: locale=en_US.UTF-8
01-07 11:00 DEBUG  WindowsBackend: total_memory_mb=4056.55859375
01-07 11:00 DEBUG  CommonBackend: Searching ISOs on USB devices
01-07 11:00 DEBUG  CommonBackend: Searching for local CDs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Ubuntu Netbook CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Kubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Kubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Kubuntu Netbook CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Xubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Xubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Mythbuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Mythbuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 INFO   root: Running the installer...
01-07 11:00 DEBUG  WindowsFrontend: __init__...
01-07 11:00 DEBUG  WindowsFrontend: on_init...
01-07 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\translations, languages=['en_US', 'en']
01-07 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\translations, languages=['en_US', 'en']
01-07 11:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=cory
01-07 11:00 INFO   root: Received settings
01-07 11:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\translations, languages=['en_US', 'en']
01-07 11:00 DEBUG  TaskList: # Running tasklist...
01-07 11:00 DEBUG  TaskList: ## Running select_target_dir...
01-07 11:00 INFO   WindowsBackend: Installing into C:\ubuntu
01-07 11:00 DEBUG  TaskList: ## Finished select_target_dir
01-07 11:00 DEBUG  TaskList: ## Running create_dir_structure...
01-07 11:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-07 11:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-07 11:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-07 11:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-07 11:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-07 11:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-07 11:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-07 11:00 DEBUG  TaskList: ## Finished create_dir_structure
01-07 11:00 DEBUG  TaskList: ## Running uncompress_target_dir...
01-07 11:00 DEBUG  TaskList: ## Finished uncompress_target_dir
01-07 11:00 DEBUG  TaskList: ## Running create_uninstaller...
01-07 11:00 DEBUG  WindowsBackend: Copying uninstaller C:\Shared\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-07 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-07 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-07 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-07 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-07 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-07 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-07 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-07 11:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-07 11:00 DEBUG  TaskList: ## Finished create_uninstaller
01-07 11:00 DEBUG  TaskList: ## Running copy_installation_files...
01-07 11:00 DEBUG  WindowsBackend: Copying C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
01-07 11:00 DEBUG  WindowsBackend: Copying C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\winboot -> C:\ubuntu\winboot
01-07 11:00 DEBUG  WindowsBackend: Copying C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
01-07 11:00 DEBUG  TaskList: ## Finished copy_installation_files
01-07 11:00 DEBUG  TaskList: ## Running get_iso...
01-07 11:00 DEBUG  CommonBackend: Searching for local CD
01-07 11:00 DEBUG  Distro:   checking whether C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain C:\Users\Cory\AppData\Local\Temp\pyl4D16.tmp\casper\filesystem.squashfs
01-07 11:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-07 11:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-07 11:00 DEBUG  CommonBackend: Searching for local ISO
01-07 11:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-07 11:00 DEBUG  TaskList: New task get_metalink
01-07 11:00 DEBUG  TaskList: ### Running get_metalink...
01-07 11:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink) > C:\ubuntu\install
01-07 11:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
01-07 11:00 DEBUG  downloader: download finished (read 9135 bytes)
01-07 11:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > C:\ubuntu\install
01-07 11:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
01-07 11:00 DEBUG  downloader: download finished (read 488 bytes)
01-07 11:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
01-07 11:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
01-07 11:00 DEBUG  downloader: download finished (read 198 bytes)
01-07 11:00 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
01-07 11:00 INFO   saplog: Checking block bindings..
01-07 11:00 INFO   saplog: Key verified successfully.
01-07 11:00 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

01-07 11:00 DEBUG  TaskList: ### Finished get_metalink
01-07 11:00 DEBUG  TaskList: New task download
01-07 11:00 DEBUG  TaskList: ### Running download...
01-07 11:00 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
01-07 11:00 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

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
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>


01-07 11:00 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

 in task download
01-07 11:00 DEBUG  TaskList: ### Finished download
01-07 11:00 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
01-07 11:00 DEBUG  TaskList: # Cancelling tasklist
01-07 11:00 DEBUG  TaskList: # Finished tasklist
01-07 11:00 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'

---

### Post by bcbc on 2011-01-07
Put the downloaded .iso in the same folder as wubi.exe and run it from there and it will use the one you've downloaded. There's no need to expand it other than to extract the wubi.exe. 

It will still look on the net to run an md5 check.

---

