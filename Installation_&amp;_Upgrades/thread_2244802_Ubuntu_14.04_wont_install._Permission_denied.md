---
title: "Ubuntu 14.04 wont install. Permission denied"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by edwin13 on 2014-09-18
Im trying to install Ubuntu 14.04 om my toshiba satellite l300 0h9 using Windows 7 Ultimate OS SP1 but Every time i try to install i get Permission Denied error.

Heres the log:
```
09-18 18:50 INFO   root: === wubi 14.04 rev286 ===09-18 18:50 DEBUG  root: Logfile is c:\users\phong\appdata\local\temp\wubi-14.04-rev286.log
09-18 18:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Phong\\AppData\\Local\\Temp\\$PowerISO$\\wubi.exe"']
09-18 18:50 DEBUG  CommonBackend: data_dir=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\data
09-18 18:50 DEBUG  WindowsBackend: 7z=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\bin\7z.exe
09-18 18:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-18 18:50 DEBUG  CommonBackend: Fetching basic info...
09-18 18:50 DEBUG  CommonBackend: original_exe=C:\Users\Phong\AppData\Local\Temp\$PowerISO$\wubi.exe
09-18 18:50 DEBUG  CommonBackend: platform=win32
09-18 18:50 DEBUG  CommonBackend: osname=nt
09-18 18:50 DEBUG  CommonBackend: language=en_CA
09-18 18:50 DEBUG  CommonBackend: encoding=cp1252
09-18 18:50 DEBUG  WindowsBackend: arch=amd64
09-18 18:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\data\isolist.ini
09-18 18:50 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 18:50 DEBUG  WindowsBackend: Fetching host info...
09-18 18:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-18 18:50 DEBUG  WindowsBackend: windows version=vista
09-18 18:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 18:50 DEBUG  WindowsBackend: windows_sp=None
09-18 18:50 DEBUG  WindowsBackend: windows_build=7601
09-18 18:50 DEBUG  WindowsBackend: gmt=-5
09-18 18:50 DEBUG  WindowsBackend: country=US
09-18 18:50 DEBUG  WindowsBackend: timezone=America/New_York
09-18 18:50 DEBUG  WindowsBackend: windows_username=Phong
09-18 18:50 DEBUG  WindowsBackend: user_full_name=Phong
09-18 18:50 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 18:50 DEBUG  WindowsBackend: windows_language_code=1033
09-18 18:50 DEBUG  WindowsBackend: windows_language=English
09-18 18:50 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 18:50 DEBUG  WindowsBackend: bootloader=vista
09-18 18:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 186776.167969 mb free ntfs)
09-18 18:50 DEBUG  WindowsBackend: drive=Drive(C: hd 186776.167969 mb free ntfs)
09-18 18:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 18:50 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 18:50 DEBUG  WindowsBackend: uninstaller_path=None
09-18 18:50 DEBUG  WindowsBackend: previous_target_dir=None
09-18 18:50 DEBUG  WindowsBackend: previous_distro_name=None
09-18 18:50 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 18:50 DEBUG  WindowsBackend: keyboard_layout=us
09-18 18:50 DEBUG  WindowsBackend: keyboard_variant=
09-18 18:50 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
09-18 18:50 DEBUG  CommonBackend: locale=en_CA.UTF-8
09-18 18:50 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 18:50 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 18:50 DEBUG  CommonBackend: Searching for local CDs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 INFO   root: Running the installer...
09-18 18:50 DEBUG  WindowsFrontend: __init__...
09-18 18:50 DEBUG  WindowsFrontend: on_init...
09-18 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\translations, languages=['en_CA', 'en']
09-18 18:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\translations, languages=['en_CA', 'en']
09-18 18:54 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=phong
09-18 18:54 INFO   root: Received settings
09-18 18:54 DEBUG  CommonBackend: Searching for local CD
09-18 18:54 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu CD
09-18 18:54 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casper\filesystem.squashfs
09-18 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:54 DEBUG  CommonBackend: Searching for local ISO
09-18 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\translations, languages=['en_US', 'en']
09-18 18:54 DEBUG  TaskList: # Running tasklist...
09-18 18:54 DEBUG  TaskList: ## Running select_target_dir...
09-18 18:54 INFO   WindowsBackend: Installing into C:\ubuntu
09-18 18:54 DEBUG  TaskList: ## Finished select_target_dir
09-18 18:54 DEBUG  TaskList: ## Running create_dir_structure...
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-18 18:54 DEBUG  TaskList: ## Finished create_dir_structure
09-18 18:54 DEBUG  TaskList: ## Running uncompress_target_dir...
09-18 18:54 DEBUG  TaskList: ## Finished uncompress_target_dir
09-18 18:54 DEBUG  TaskList: ## Running create_uninstaller...
09-18 18:54 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Phong\AppData\Local\Temp\$PowerISO$\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-18 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-18 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-18 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-18 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-18 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
09-18 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-18 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-18 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-18 18:54 DEBUG  TaskList: ## Finished create_uninstaller
09-18 18:54 DEBUG  TaskList: ## Running copy_installation_files...
09-18 18:54 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-18 18:54 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\winboot -> C:\ubuntu\winboot
09-18 18:54 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-18 18:54 DEBUG  TaskList: ## Finished copy_installation_files
09-18 18:54 DEBUG  TaskList: ## Running get_iso...
09-18 18:54 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-18 18:54 DEBUG  TaskList: New task get_metalink
09-18 18:54 DEBUG  TaskList: ### Running get_metalink...
09-18 18:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
09-18 18:54 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-18 18:54 DEBUG  downloader: download finished (read 45848 bytes)
09-18 18:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-18 18:54 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
09-18 18:54 DEBUG  downloader: download finished (read 560 bytes)
09-18 18:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-18 18:54 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-18 18:54 DEBUG  downloader: download finished (read 198 bytes)
09-18 18:54 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-18 18:54 INFO   saplog: Checking block bindings..
09-18 18:54 INFO   saplog: Key verified successfully.
09-18 18:54 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink


09-18 18:54 ERROR  CommonBackend: The md5 of the metalink does match
09-18 18:54 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-18 18:54 DEBUG  TaskList: ### Finished get_metalink
09-18 18:54 DEBUG  TaskList: New task download
09-18 18:54 DEBUG  TaskList: ### Running download...
09-18 18:54 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 18:54 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.




09-18 18:54 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


 in task download
09-18 18:54 DEBUG  TaskList: ### Finished download
09-18 18:54 ERROR  root: Could not remove: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 18:54 DEBUG  TaskList: New task download
09-18 18:54 DEBUG  TaskList: ### Running download...
09-18 18:54 DEBUG  downloader: downloading [http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso](http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 18:54 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso, url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso, basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None
09-18 19:07 DEBUG  TaskList: ### Finished download
09-18 19:07 DEBUG  downloader: download finished (read 1010827264 bytes)
09-18 19:07 DEBUG  TaskList: New task check_iso
09-18 19:07 DEBUG  TaskList: ### Running check_iso...
09-18 19:07 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:07 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:07 ERROR  WindowsBackend: Error executing command
>>command=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
09-18 19:07 DEBUG  WindowsBackend: command >>C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:07 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-18 19:07 DEBUG  TaskList: ### Finished check_iso
09-18 19:07 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:07 DEBUG  TaskList: # Cancelling tasklist
09-18 19:07 DEBUG  TaskList: # Finished tasklist
09-18 19:07 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:14 INFO   root: === wubi 14.04 rev286 ===
09-18 19:14 DEBUG  root: Logfile is c:\users\phong\appdata\local\temp\wubi-14.04-rev286.log
09-18 19:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Phong\\AppData\\Local\\Temp\\$PowerISO$\\wubi.exe"']
09-18 19:14 DEBUG  CommonBackend: data_dir=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\data
09-18 19:14 DEBUG  WindowsBackend: 7z=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\bin\7z.exe
09-18 19:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-18 19:14 DEBUG  CommonBackend: Fetching basic info...
09-18 19:14 DEBUG  CommonBackend: original_exe=C:\Users\Phong\AppData\Local\Temp\$PowerISO$\wubi.exe
09-18 19:14 DEBUG  CommonBackend: platform=win32
09-18 19:14 DEBUG  CommonBackend: osname=nt
09-18 19:14 DEBUG  CommonBackend: language=en_CA
09-18 19:14 DEBUG  CommonBackend: encoding=cp1252
09-18 19:14 DEBUG  WindowsBackend: arch=amd64
09-18 19:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\data\isolist.ini
09-18 19:14 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 19:14 DEBUG  WindowsBackend: Fetching host info...
09-18 19:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-18 19:14 DEBUG  WindowsBackend: windows version=vista
09-18 19:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 19:14 DEBUG  WindowsBackend: windows_sp=None
09-18 19:14 DEBUG  WindowsBackend: windows_build=7601
09-18 19:14 DEBUG  WindowsBackend: gmt=-5
09-18 19:14 DEBUG  WindowsBackend: country=US
09-18 19:14 DEBUG  WindowsBackend: timezone=America/New_York
09-18 19:14 DEBUG  WindowsBackend: windows_username=Phong
09-18 19:14 DEBUG  WindowsBackend: user_full_name=Phong
09-18 19:14 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 19:14 DEBUG  WindowsBackend: windows_language_code=1033
09-18 19:14 DEBUG  WindowsBackend: windows_language=English
09-18 19:14 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 19:14 DEBUG  WindowsBackend: bootloader=vista
09-18 19:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 185833.976563 mb free ntfs)
09-18 19:14 DEBUG  WindowsBackend: drive=Drive(C: hd 185833.976563 mb free ntfs)
09-18 19:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 19:14 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 19:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-18 19:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-18 19:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-18 19:14 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 19:14 DEBUG  WindowsBackend: keyboard_layout=us
09-18 19:14 DEBUG  WindowsBackend: keyboard_variant=
09-18 19:14 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
09-18 19:14 DEBUG  CommonBackend: locale=en_CA.UTF-8
09-18 19:14 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 19:14 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 19:14 DEBUG  CommonBackend: Searching for local CDs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Kubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Kubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Mythbuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Mythbuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Edubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Edubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Lubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Lubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu Studio CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu Studio CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 INFO   root: Already installed, running the uninstaller...
09-18 19:15 INFO   root: Running the uninstaller...
09-18 19:15 INFO   CommonBackend: This is the uninstaller running
09-18 19:15 DEBUG  WindowsFrontend: __init__...
09-18 19:15 DEBUG  WindowsFrontend: on_init...
09-18 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\translations, languages=['en_CA', 'en']
09-18 19:15 INFO   root: Received settings
09-18 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\translations, languages=['en_CA', 'en']
09-18 19:15 DEBUG  TaskList: # Running tasklist...
09-18 19:15 DEBUG  TaskList: ## Running Remove bootloader entry...
09-18 19:15 DEBUG  WindowsBackend: Could not find bcd id
09-18 19:15 DEBUG  WindowsBackend: undo_bootini C:
09-18 19:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 185833.976563 mb free ntfs)
09-18 19:15 DEBUG  WindowsBackend: undo_bootini E:
09-18 19:15 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
09-18 19:15 DEBUG  TaskList: ## Finished Remove bootloader entry
09-18 19:15 DEBUG  TaskList: ## Running Remove target dir...
09-18 19:15 DEBUG  CommonBackend: Deleting C:\ubuntu
09-18 19:15 DEBUG  TaskList: ## Finished Remove target dir
09-18 19:15 DEBUG  TaskList: ## Running Remove registry key...
09-18 19:15 DEBUG  TaskList: ## Finished Remove registry key
09-18 19:15 DEBUG  TaskList: # Finished tasklist
09-18 19:15 INFO   root: Almost finished uninstalling
09-18 19:15 INFO   root: Finished uninstallation
09-18 19:15 DEBUG  CommonBackend: Fetching basic info...
09-18 19:15 DEBUG  CommonBackend: original_exe=C:\Users\Phong\AppData\Local\Temp\$PowerISO$\wubi.exe
09-18 19:15 DEBUG  CommonBackend: platform=win32
09-18 19:15 DEBUG  CommonBackend: osname=nt
09-18 19:15 DEBUG  WindowsBackend: arch=amd64
09-18 19:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\data\isolist.ini
09-18 19:15 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 19:15 DEBUG  WindowsBackend: Fetching host info...
09-18 19:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-18 19:15 DEBUG  WindowsBackend: windows version=vista
09-18 19:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 19:15 DEBUG  WindowsBackend: windows_sp=None
09-18 19:15 DEBUG  WindowsBackend: windows_build=7601
09-18 19:15 DEBUG  WindowsBackend: gmt=-5
09-18 19:15 DEBUG  WindowsBackend: country=US
09-18 19:15 DEBUG  WindowsBackend: timezone=America/New_York
09-18 19:15 DEBUG  WindowsBackend: windows_username=Phong
09-18 19:15 DEBUG  WindowsBackend: user_full_name=Phong
09-18 19:15 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 19:15 DEBUG  WindowsBackend: windows_language_code=1033
09-18 19:15 DEBUG  WindowsBackend: windows_language=English
09-18 19:15 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 19:15 DEBUG  WindowsBackend: bootloader=vista
09-18 19:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 186801.175781 mb free ntfs)
09-18 19:15 DEBUG  WindowsBackend: drive=Drive(C: hd 186801.175781 mb free ntfs)
09-18 19:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 19:15 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 19:15 DEBUG  WindowsBackend: uninstaller_path=None
09-18 19:15 DEBUG  WindowsBackend: previous_target_dir=None
09-18 19:15 DEBUG  WindowsBackend: previous_distro_name=None
09-18 19:15 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 19:15 DEBUG  WindowsBackend: keyboard_layout=us
09-18 19:15 DEBUG  WindowsBackend: keyboard_variant=
09-18 19:15 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 19:15 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 19:15 DEBUG  CommonBackend: Searching for local CDs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 INFO   root: Running the installer...
09-18 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\translations, languages=['en_CA', 'en']
09-18 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\translations, languages=['en_CA', 'en']
09-18 19:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=phong
09-18 19:15 INFO   root: Received settings
09-18 19:15 DEBUG  CommonBackend: Searching for local CD
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  CommonBackend: Searching for local ISO
09-18 19:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\translations, languages=['en_US', 'en']
09-18 19:15 DEBUG  TaskList: # Running tasklist...
09-18 19:15 DEBUG  TaskList: ## Running select_target_dir...
09-18 19:15 INFO   WindowsBackend: Installing into C:\ubuntu
09-18 19:15 DEBUG  TaskList: ## Finished select_target_dir
09-18 19:15 DEBUG  TaskList: ## Running create_dir_structure...
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-18 19:15 DEBUG  TaskList: ## Finished create_dir_structure
09-18 19:15 DEBUG  TaskList: ## Running uncompress_target_dir...
09-18 19:15 DEBUG  TaskList: ## Finished uncompress_target_dir
09-18 19:15 DEBUG  TaskList: ## Running create_uninstaller...
09-18 19:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Phong\AppData\Local\Temp\$PowerISO$\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-18 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-18 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-18 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-18 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-18 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
09-18 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-18 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-18 19:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-18 19:15 DEBUG  TaskList: ## Finished create_uninstaller
09-18 19:15 DEBUG  TaskList: ## Running copy_installation_files...
09-18 19:15 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-18 19:15 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\winboot -> C:\ubuntu\winboot
09-18 19:15 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-18 19:15 DEBUG  TaskList: ## Finished copy_installation_files
09-18 19:15 DEBUG  TaskList: ## Running get_iso...
09-18 19:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-18 19:15 DEBUG  TaskList: New task get_metalink
09-18 19:15 DEBUG  TaskList: ### Running get_metalink...
09-18 19:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
09-18 19:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-18 19:15 DEBUG  downloader: download finished (read 45848 bytes)
09-18 19:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-18 19:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
09-18 19:15 DEBUG  downloader: download finished (read 560 bytes)
09-18 19:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-18 19:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-18 19:15 DEBUG  downloader: download finished (read 198 bytes)
09-18 19:15 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-18 19:15 INFO   saplog: Checking block bindings..
09-18 19:15 INFO   saplog: Key verified successfully.
09-18 19:15 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink


09-18 19:15 ERROR  CommonBackend: The md5 of the metalink does match
09-18 19:15 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-18 19:15 DEBUG  TaskList: ### Finished get_metalink
09-18 19:15 DEBUG  TaskList: New task download
09-18 19:15 DEBUG  TaskList: ### Running download...
09-18 19:15 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:15 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.




09-18 19:15 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


 in task download
09-18 19:15 DEBUG  TaskList: ### Finished download
09-18 19:15 ERROR  root: Could not remove: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:15 DEBUG  TaskList: New task download
09-18 19:15 DEBUG  TaskList: ### Running download...
09-18 19:15 DEBUG  downloader: downloading [http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso](http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso, url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso, basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None
09-18 19:24 DEBUG  TaskList: ### Finished download
09-18 19:24 DEBUG  downloader: download finished (read 1010827264 bytes)
09-18 19:24 DEBUG  TaskList: New task check_iso
09-18 19:24 DEBUG  TaskList: ### Running check_iso...
09-18 19:24 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:24 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:24 ERROR  WindowsBackend: Error executing command
>>command=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
09-18 19:24 DEBUG  WindowsBackend: command >>C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:24 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-18 19:24 DEBUG  TaskList: ### Finished check_iso
09-18 19:24 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:24 DEBUG  TaskList: # Cancelling tasklist
09-18 19:24 DEBUG  TaskList: # Finished tasklist
09-18 19:24 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:39 INFO   root: === wubi 14.04 rev286 ===
09-18 19:39 DEBUG  root: Logfile is c:\users\phong\appdata\local\temp\wubi-14.04-rev286.log
09-18 19:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Phong\\Desktop\\Ubuntu\\wubi.exe"']
09-18 19:39 DEBUG  CommonBackend: data_dir=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\data
09-18 19:39 DEBUG  WindowsBackend: 7z=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\bin\7z.exe
09-18 19:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-18 19:39 DEBUG  CommonBackend: Fetching basic info...
09-18 19:39 DEBUG  CommonBackend: original_exe=C:\Users\Phong\Desktop\Ubuntu\wubi.exe
09-18 19:39 DEBUG  CommonBackend: platform=win32
09-18 19:39 DEBUG  CommonBackend: osname=nt
09-18 19:39 DEBUG  CommonBackend: language=en_CA
09-18 19:39 DEBUG  CommonBackend: encoding=cp1252
09-18 19:39 DEBUG  WindowsBackend: arch=amd64
09-18 19:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\data\isolist.ini
09-18 19:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 19:39 DEBUG  WindowsBackend: Fetching host info...
09-18 19:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-18 19:39 DEBUG  WindowsBackend: windows version=vista
09-18 19:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 19:39 DEBUG  WindowsBackend: windows_sp=None
09-18 19:39 DEBUG  WindowsBackend: windows_build=7601
09-18 19:39 DEBUG  WindowsBackend: gmt=-5
09-18 19:39 DEBUG  WindowsBackend: country=US
09-18 19:39 DEBUG  WindowsBackend: timezone=America/New_York
09-18 19:39 DEBUG  WindowsBackend: windows_username=Phong
09-18 19:39 DEBUG  WindowsBackend: user_full_name=Phong
09-18 19:39 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 19:39 DEBUG  WindowsBackend: windows_language_code=1033
09-18 19:39 DEBUG  WindowsBackend: windows_language=English
09-18 19:39 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 19:39 DEBUG  WindowsBackend: bootloader=vista
09-18 19:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 185809.535156 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(C: hd 185809.535156 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 19:39 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-18 19:39 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-18 19:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-18 19:39 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 19:39 DEBUG  WindowsBackend: keyboard_layout=us
09-18 19:39 DEBUG  WindowsBackend: keyboard_variant=
09-18 19:39 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
09-18 19:39 DEBUG  CommonBackend: locale=en_CA.UTF-8
09-18 19:39 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 19:39 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 19:39 DEBUG  CommonBackend: Searching for local CDs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 INFO   root: Already installed, running the uninstaller...
09-18 19:39 INFO   root: Running the uninstaller...
09-18 19:39 INFO   CommonBackend: This is the uninstaller running
09-18 19:39 DEBUG  WindowsFrontend: __init__...
09-18 19:39 DEBUG  WindowsFrontend: on_init...
09-18 19:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\translations, languages=['en_CA', 'en']
09-18 19:39 INFO   root: Received settings
09-18 19:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\translations, languages=['en_CA', 'en']
09-18 19:39 DEBUG  TaskList: # Running tasklist...
09-18 19:39 DEBUG  TaskList: ## Running Remove bootloader entry...
09-18 19:39 DEBUG  WindowsBackend: Could not find bcd id
09-18 19:39 DEBUG  WindowsBackend: undo_bootini C:
09-18 19:39 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 185809.535156 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: undo_bootini E:
09-18 19:39 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
09-18 19:39 DEBUG  TaskList: ## Finished Remove bootloader entry
09-18 19:39 DEBUG  TaskList: ## Running Remove target dir...
09-18 19:39 DEBUG  CommonBackend: Deleting C:\ubuntu
09-18 19:39 DEBUG  TaskList: ## Finished Remove target dir
09-18 19:39 DEBUG  TaskList: ## Running Remove registry key...
09-18 19:39 DEBUG  TaskList: ## Finished Remove registry key
09-18 19:39 DEBUG  TaskList: # Finished tasklist
09-18 19:39 INFO   root: Almost finished uninstalling
09-18 19:39 INFO   root: Finished uninstallation
09-18 19:39 DEBUG  CommonBackend: Fetching basic info...
09-18 19:39 DEBUG  CommonBackend: original_exe=C:\Users\Phong\Desktop\Ubuntu\wubi.exe
09-18 19:39 DEBUG  CommonBackend: platform=win32
09-18 19:39 DEBUG  CommonBackend: osname=nt
09-18 19:39 DEBUG  WindowsBackend: arch=amd64
09-18 19:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\data\isolist.ini
09-18 19:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 19:39 DEBUG  WindowsBackend: Fetching host info...
09-18 19:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-18 19:39 DEBUG  WindowsBackend: windows version=vista
09-18 19:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 19:39 DEBUG  WindowsBackend: windows_sp=None
09-18 19:39 DEBUG  WindowsBackend: windows_build=7601
09-18 19:39 DEBUG  WindowsBackend: gmt=-5
09-18 19:39 DEBUG  WindowsBackend: country=US
09-18 19:39 DEBUG  WindowsBackend: timezone=America/New_York
09-18 19:39 DEBUG  WindowsBackend: windows_username=Phong
09-18 19:39 DEBUG  WindowsBackend: user_full_name=Phong
09-18 19:39 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 19:39 DEBUG  WindowsBackend: windows_language_code=1033
09-18 19:39 DEBUG  WindowsBackend: windows_language=English
09-18 19:39 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 19:39 DEBUG  WindowsBackend: bootloader=vista
09-18 19:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 186776.726563 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(C: hd 186776.726563 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 19:39 DEBUG  WindowsBackend: uninstaller_path=None
09-18 19:39 DEBUG  WindowsBackend: previous_target_dir=None
09-18 19:39 DEBUG  WindowsBackend: previous_distro_name=None
09-18 19:39 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 19:39 DEBUG  WindowsBackend: keyboard_layout=us
09-18 19:39 DEBUG  WindowsBackend: keyboard_variant=
09-18 19:39 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 19:39 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 19:39 DEBUG  CommonBackend: Searching for local CDs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 INFO   root: Running the installer...
09-18 19:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\translations, languages=['en_CA', 'en']
09-18 19:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\translations, languages=['en_CA', 'en']
09-18 19:40 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=quantom
09-18 19:40 INFO   root: Received settings
09-18 19:40 DEBUG  CommonBackend: Searching for local CD
09-18 19:40 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:40 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casper\filesystem.squashfs
09-18 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:40 DEBUG  CommonBackend: Searching for local ISO
09-18 19:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\translations, languages=['en_US', 'en']
09-18 19:40 DEBUG  TaskList: # Running tasklist...
09-18 19:40 DEBUG  TaskList: ## Running select_target_dir...
09-18 19:40 INFO   WindowsBackend: Installing into C:\ubuntu
09-18 19:40 DEBUG  TaskList: ## Finished select_target_dir
09-18 19:40 DEBUG  TaskList: ## Running create_dir_structure...
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-18 19:40 DEBUG  TaskList: ## Finished create_dir_structure
09-18 19:40 DEBUG  TaskList: ## Running uncompress_target_dir...
09-18 19:40 DEBUG  TaskList: ## Finished uncompress_target_dir
09-18 19:40 DEBUG  TaskList: ## Running create_uninstaller...
09-18 19:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Phong\Desktop\Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-18 19:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-18 19:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-18 19:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-18 19:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-18 19:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
09-18 19:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-18 19:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-18 19:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-18 19:40 DEBUG  TaskList: ## Finished create_uninstaller
09-18 19:40 DEBUG  TaskList: ## Running copy_installation_files...
09-18 19:40 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-18 19:40 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\winboot -> C:\ubuntu\winboot
09-18 19:40 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-18 19:40 DEBUG  TaskList: ## Finished copy_installation_files
09-18 19:40 DEBUG  TaskList: ## Running get_iso...
09-18 19:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-18 19:40 DEBUG  TaskList: New task get_metalink
09-18 19:40 DEBUG  TaskList: ### Running get_metalink...
09-18 19:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > C:\ubuntu\install
09-18 19:40 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-18 19:40 DEBUG  downloader: download finished (read 45848 bytes)
09-18 19:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-18 19:40 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=560, text=None
09-18 19:40 DEBUG  downloader: download finished (read 560 bytes)
09-18 19:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-18 19:40 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-18 19:40 DEBUG  downloader: download finished (read 198 bytes)
09-18 19:40 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-18 19:40 INFO   saplog: Checking block bindings..
09-18 19:40 INFO   saplog: Key verified successfully.
09-18 19:40 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink


09-18 19:40 ERROR  CommonBackend: The md5 of the metalink does match
09-18 19:40 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-18 19:40 DEBUG  TaskList: ### Finished get_metalink
09-18 19:40 DEBUG  TaskList: New task download
09-18 19:40 DEBUG  TaskList: ### Running download...
09-18 19:40 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:40 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.




09-18 19:40 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


 in task download
09-18 19:40 DEBUG  TaskList: ### Finished download
09-18 19:40 ERROR  root: Could not remove: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:40 DEBUG  TaskList: New task download
09-18 19:40 DEBUG  TaskList: ### Running download...
09-18 19:40 DEBUG  downloader: downloading [http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso](http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso) > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:40 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso, url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso, basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None
```


Pls help
           Thx, Edwin

---

### Post by edwin13 on 2014-09-18
I was looking through the log and it said "cannot access the file as it is being used in a different process" though i just tried to install it.

---

### Post by yancek on 2014-09-18
The WUBI installer is no longer being developed and I don't believe it is supported.  I have read posts here of people getting it to work with windows 7 and earlier.  Never used it but someone else familiar might post with some ideas.

---

### Post by edwin13 on 2014-09-19
So could you send me to a post how to install it without WUBI?

---

### Post by ibjsb4 on 2014-09-19
I will gladly help. but first please edit your post using code tags.

```
Heres the log:09-18 18:50 INFO   root: === wubi 14.04 rev286 ===09-18  18:50 DEBUG  root: Logfile is  c:\users\phong\appdata\local\temp\wubi-14.04-rev286.log
09-18 18:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Phong\\AppData\\Local\\Temp\\$  PowerISO$\\wubi.exe"']
09-18 18:50 DEBUG  CommonBackend: data_dir=C:\Users\Phong\AppData\Local\Temp\pylB8FD  .tmp\data
09-18 18:50 DEBUG  WindowsBackend: 7z=C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\b  in\7z.exe
09-18 18:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\St  art Menu\Programs\Startup
09-18 18:50 DEBUG  CommonBackend: Fetching basic info...
09-18 18:50 DEBUG  CommonBackend: original_exe=C:\Users\Phong\AppData\Local\Temp\$Po  werISO$\wubi.exe
09-18 18:50 DEBUG  CommonBackend: platform=win32
09-18 18:50 DEBUG  CommonBackend: osname=nt
09-18 18:50 DEBUG  CommonBackend: language=en_CA
09-18 18:50 DEBUG  CommonBackend: encoding=cp1252
09-18 18:50 DEBUG  WindowsBackend: arch=amd64
09-18 18:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pylB8FD.  tmp\data\isolist.ini
09-18 18:50 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 18:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 18:50 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 18:50 DEBUG  WindowsBackend: Fetching host info...
09-18 18:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer  sion\Uninstall\Wubi
09-18 18:50 DEBUG  WindowsBackend: windows version=vista
09-18 18:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 18:50 DEBUG  WindowsBackend: windows_sp=None
09-18 18:50 DEBUG  WindowsBackend: windows_build=7601
09-18 18:50 DEBUG  WindowsBackend: gmt=-5
09-18 18:50 DEBUG  WindowsBackend: country=US
09-18 18:50 DEBUG  WindowsBackend: timezone=America/New_York
09-18 18:50 DEBUG  WindowsBackend: windows_username=Phong
09-18 18:50 DEBUG  WindowsBackend: user_full_name=Phong
09-18 18:50 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 18:50 DEBUG  WindowsBackend: windows_language_code=1033
09-18 18:50 DEBUG  WindowsBackend: windows_language=English
09-18 18:50 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 18:50 DEBUG  WindowsBackend: bootloader=vista
09-18 18:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 186776.167969 mb free ntfs)
09-18 18:50 DEBUG  WindowsBackend: drive=Drive(C: hd 186776.167969 mb free ntfs)
09-18 18:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 18:50 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 18:50 DEBUG  WindowsBackend: uninstaller_path=None
09-18 18:50 DEBUG  WindowsBackend: previous_target_dir=None
09-18 18:50 DEBUG  WindowsBackend: previous_distro_name=None
09-18 18:50 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 18:50 DEBUG  WindowsBackend: keyboard_layout=us
09-18 18:50 DEBUG  WindowsBackend: keyboard_variant=
09-18 18:50 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
09-18 18:50 DEBUG  CommonBackend: locale=en_CA.UTF-8
09-18 18:50 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 18:50 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 18:50 DEBUG  CommonBackend: Searching for local CDs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 18:50 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:50 INFO   root: Running the installer...
09-18 18:50 DEBUG  WindowsFrontend: __init__...
09-18 18:50 DEBUG  WindowsFrontend: on_init...
09-18 18:50 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pylB8F  D.tmp\translations,  languages=['en_CA', 'en']
09-18 18:50 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pylB8F  D.tmp\translations,  languages=['en_CA', 'en']
09-18 18:54 DEBUG  WinuiInstallationPage: target_drive=C:,  installation_size=30000MB, distro_name=Ubuntu, language=en_US,  locale=en_US.UTF-8, username=phong
09-18 18:54 INFO   root: Received settings
09-18 18:54 DEBUG  CommonBackend: Searching for local CD
09-18 18:54 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp is a valid Ubuntu CD
09-18 18:54 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\casp  er\filesystem.squashfs
09-18 18:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 18:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 18:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 18:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 18:54 DEBUG  CommonBackend: Searching for local ISO
09-18 18:54 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pylB8F  D.tmp\translations,  languages=['en_US', 'en']
09-18 18:54 DEBUG  TaskList: # Running tasklist...
09-18 18:54 DEBUG  TaskList: ## Running select_target_dir...
09-18 18:54 INFO   WindowsBackend: Installing into C:\ubuntu
09-18 18:54 DEBUG  TaskList: ## Finished select_target_dir
09-18 18:54 DEBUG  TaskList: ## Running create_dir_structure...
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-18 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-18 18:54 DEBUG  TaskList: ## Finished create_dir_structure
09-18 18:54 DEBUG  TaskList: ## Running uncompress_target_dir...
09-18 18:54 DEBUG  TaskList: ## Finished uncompress_target_dir
09-18 18:54 DEBUG  TaskList: ## Running create_uninstaller...
09-18 18:54 DEBUG  WindowsBackend: Copying uninstaller  C:\Users\Phong\AppData\Local\Temp\$PowerISO$\wubi.  exe ->  C:\ubuntu\uninstall-wubi.exe
09-18 18:54 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  UninstallString C:\ubuntu\uninstall-wubi.exe
09-18 18:54 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  InstallationDir C:\ubuntu
09-18 18:54 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi DisplayName  Ubuntu
09-18 18:54 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi DisplayIcon  C:\ubuntu\Ubuntu.ico
09-18 18:54 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  DisplayVersion 14.04-rev286
09-18 18:54 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi Publisher  Ubuntu
09-18 18:54 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-18 18:54 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-18 18:54 DEBUG  TaskList: ## Finished create_uninstaller
09-18 18:54 DEBUG  TaskList: ## Running copy_installation_files...
09-18 18:54 DEBUG  WindowsBackend: Copying  C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\data  \custom-installation  -> C:\ubuntu\install\custom-installation
09-18 18:54 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\winb  oot -> C:\ubuntu\winboot
09-18 18:54 DEBUG  WindowsBackend: Copying  C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\data  \images\Ubuntu.ico  -> C:\ubuntu\Ubuntu.ico
09-18 18:54 DEBUG  TaskList: ## Finished copy_installation_files
09-18 18:54 DEBUG  TaskList: ## Running get_iso...
09-18 18:54 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-18 18:54 DEBUG  TaskList: New task get_metalink
09-18 18:54 DEBUG  TaskList: ### Running get_metalink...
09-18 18:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubu...amd64.metalink]("http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink") > C:\ubuntu\install
09-18 18:54 DEBUG  downloader: Download start  filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink,  url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink,  basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-18 18:54 DEBUG  downloader: download finished (read 45848 bytes)
09-18 18:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-18 18:54 DEBUG  downloader: Download start  filename=C:\ubuntu\install\MD5SUMS-metalink,  url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink,  basename=MD5SUMS-metalink, length=560, text=None
09-18 18:54 DEBUG  downloader: download finished (read 560 bytes)
09-18 18:54 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-18 18:54 DEBUG  downloader: Download start  filename=C:\ubuntu\install\MD5SUMS-metalink.gpg,  url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg,  basename=MD5SUMS-metalink.gpg, length=198, text=None
09-18 18:54 DEBUG  downloader: download finished (read 198 bytes)
09-18 18:54 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-18 18:54 INFO   saplog: Checking block bindings..
09-18 18:54 INFO   saplog: Key verified successfully.
09-18 18:54 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink


09-18 18:54 ERROR  CommonBackend: The md5 of the metalink does match
09-18 18:54 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-18 18:54 DEBUG  TaskList: ### Finished get_metalink
09-18 18:54 DEBUG  TaskList: New task download
09-18 18:54 DEBUG  TaskList: ### Running download...
09-18 18:54 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/14.04.1/u...64.iso.torrent]("http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent") > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 18:54 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.




09-18 18:54 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


 in task download
09-18 18:54 DEBUG  TaskList: ### Finished download
09-18 18:54 ERROR  root: Could not remove: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 18:54 DEBUG  TaskList: New task download
09-18 18:54 DEBUG  TaskList: ### Running download...
09-18 18:54 DEBUG  downloader: downloading [http://mirror.vutbr.cz/ubuntu/releas...ktop-amd64.iso]("http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso") > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 18:54 DEBUG  downloader: Download start  filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso,  url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso,  basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None
09-18 19:07 DEBUG  TaskList: ### Finished download
09-18 19:07 DEBUG  downloader: download finished (read 1010827264 bytes)
09-18 19:07 DEBUG  TaskList: New task check_iso
09-18 19:07 DEBUG  TaskList: ### Running check_iso...
09-18 19:07 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:07 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:07 ERROR  WindowsBackend: Error executing command
>>command=C:\Users\Phong\AppData\Local\Temp\pylB8F  D.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process  cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Phong\AppData\Local\Temp\pylB8F  D.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process  cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
09-18 19:07 DEBUG  WindowsBackend: command  >>C:\Users\Phong\AppData\Local\Temp\pylB8FD.tmp\bi  n\7z.exe l  C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:07 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-18 19:07 DEBUG  TaskList: ### Finished check_iso
09-18 19:07 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:07 DEBUG  TaskList: # Cancelling tasklist
09-18 19:07 DEBUG  TaskList: # Finished tasklist
09-18 19:07 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:14 INFO   root: === wubi 14.04 rev286 ===
09-18 19:14 DEBUG  root: Logfile is c:\users\phong\appdata\local\temp\wubi-14.04-rev286.log
09-18 19:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Phong\\AppData\\Local\\Temp\\$  PowerISO$\\wubi.exe"']
09-18 19:14 DEBUG  CommonBackend: data_dir=C:\Users\Phong\AppData\Local\Temp\pyl2E0E  .tmp\data
09-18 19:14 DEBUG  WindowsBackend: 7z=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\b  in\7z.exe
09-18 19:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\St  art Menu\Programs\Startup
09-18 19:14 DEBUG  CommonBackend: Fetching basic info...
09-18 19:14 DEBUG  CommonBackend: original_exe=C:\Users\Phong\AppData\Local\Temp\$Po  werISO$\wubi.exe
09-18 19:14 DEBUG  CommonBackend: platform=win32
09-18 19:14 DEBUG  CommonBackend: osname=nt
09-18 19:14 DEBUG  CommonBackend: language=en_CA
09-18 19:14 DEBUG  CommonBackend: encoding=cp1252
09-18 19:14 DEBUG  WindowsBackend: arch=amd64
09-18 19:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.  tmp\data\isolist.ini
09-18 19:14 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 19:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 19:14 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 19:14 DEBUG  WindowsBackend: Fetching host info...
09-18 19:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer  sion\Uninstall\Wubi
09-18 19:14 DEBUG  WindowsBackend: windows version=vista
09-18 19:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 19:14 DEBUG  WindowsBackend: windows_sp=None
09-18 19:14 DEBUG  WindowsBackend: windows_build=7601
09-18 19:14 DEBUG  WindowsBackend: gmt=-5
09-18 19:14 DEBUG  WindowsBackend: country=US
09-18 19:14 DEBUG  WindowsBackend: timezone=America/New_York
09-18 19:14 DEBUG  WindowsBackend: windows_username=Phong
09-18 19:14 DEBUG  WindowsBackend: user_full_name=Phong
09-18 19:14 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 19:14 DEBUG  WindowsBackend: windows_language_code=1033
09-18 19:14 DEBUG  WindowsBackend: windows_language=English
09-18 19:14 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 19:14 DEBUG  WindowsBackend: bootloader=vista
09-18 19:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 185833.976563 mb free ntfs)
09-18 19:14 DEBUG  WindowsBackend: drive=Drive(C: hd 185833.976563 mb free ntfs)
09-18 19:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 19:14 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 19:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-18 19:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-18 19:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-18 19:14 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 19:14 DEBUG  WindowsBackend: keyboard_layout=us
09-18 19:14 DEBUG  WindowsBackend: keyboard_variant=
09-18 19:14 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
09-18 19:14 DEBUG  CommonBackend: locale=en_CA.UTF-8
09-18 19:14 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 19:14 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 19:14 DEBUG  CommonBackend: Searching for local CDs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Kubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Kubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Mythbuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Mythbuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Edubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Edubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Lubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Lubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu Studio CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu Studio CD
09-18 19:14 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 INFO   root: Already installed, running the uninstaller...
09-18 19:15 INFO   root: Running the uninstaller...
09-18 19:15 INFO   CommonBackend: This is the uninstaller running
09-18 19:15 DEBUG  WindowsFrontend: __init__...
09-18 19:15 DEBUG  WindowsFrontend: on_init...
09-18 19:15 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0  E.tmp\translations,  languages=['en_CA', 'en']
09-18 19:15 INFO   root: Received settings
09-18 19:15 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0  E.tmp\translations,  languages=['en_CA', 'en']
09-18 19:15 DEBUG  TaskList: # Running tasklist...
09-18 19:15 DEBUG  TaskList: ## Running Remove bootloader entry...
09-18 19:15 DEBUG  WindowsBackend: Could not find bcd id
09-18 19:15 DEBUG  WindowsBackend: undo_bootini C:
09-18 19:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 185833.976563 mb free ntfs)
09-18 19:15 DEBUG  WindowsBackend: undo_bootini E:
09-18 19:15 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
09-18 19:15 DEBUG  TaskList: ## Finished Remove bootloader entry
09-18 19:15 DEBUG  TaskList: ## Running Remove target dir...
09-18 19:15 DEBUG  CommonBackend: Deleting C:\ubuntu
09-18 19:15 DEBUG  TaskList: ## Finished Remove target dir
09-18 19:15 DEBUG  TaskList: ## Running Remove registry key...
09-18 19:15 DEBUG  TaskList: ## Finished Remove registry key
09-18 19:15 DEBUG  TaskList: # Finished tasklist
09-18 19:15 INFO   root: Almost finished uninstalling
09-18 19:15 INFO   root: Finished uninstallation
09-18 19:15 DEBUG  CommonBackend: Fetching basic info...
09-18 19:15 DEBUG  CommonBackend: original_exe=C:\Users\Phong\AppData\Local\Temp\$Po  werISO$\wubi.exe
09-18 19:15 DEBUG  CommonBackend: platform=win32
09-18 19:15 DEBUG  CommonBackend: osname=nt
09-18 19:15 DEBUG  WindowsBackend: arch=amd64
09-18 19:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pyl2E0E.  tmp\data\isolist.ini
09-18 19:15 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 19:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 19:15 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 19:15 DEBUG  WindowsBackend: Fetching host info...
09-18 19:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer  sion\Uninstall\Wubi
09-18 19:15 DEBUG  WindowsBackend: windows version=vista
09-18 19:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 19:15 DEBUG  WindowsBackend: windows_sp=None
09-18 19:15 DEBUG  WindowsBackend: windows_build=7601
09-18 19:15 DEBUG  WindowsBackend: gmt=-5
09-18 19:15 DEBUG  WindowsBackend: country=US
09-18 19:15 DEBUG  WindowsBackend: timezone=America/New_York
09-18 19:15 DEBUG  WindowsBackend: windows_username=Phong
09-18 19:15 DEBUG  WindowsBackend: user_full_name=Phong
09-18 19:15 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 19:15 DEBUG  WindowsBackend: windows_language_code=1033
09-18 19:15 DEBUG  WindowsBackend: windows_language=English
09-18 19:15 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 19:15 DEBUG  WindowsBackend: bootloader=vista
09-18 19:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 186801.175781 mb free ntfs)
09-18 19:15 DEBUG  WindowsBackend: drive=Drive(C: hd 186801.175781 mb free ntfs)
09-18 19:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 19:15 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 19:15 DEBUG  WindowsBackend: uninstaller_path=None
09-18 19:15 DEBUG  WindowsBackend: previous_target_dir=None
09-18 19:15 DEBUG  WindowsBackend: previous_distro_name=None
09-18 19:15 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 19:15 DEBUG  WindowsBackend: keyboard_layout=us
09-18 19:15 DEBUG  WindowsBackend: keyboard_variant=
09-18 19:15 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 19:15 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 19:15 DEBUG  CommonBackend: Searching for local CDs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 INFO   root: Running the installer...
09-18 19:15 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0  E.tmp\translations,  languages=['en_CA', 'en']
09-18 19:15 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0  E.tmp\translations,  languages=['en_CA', 'en']
09-18 19:15 DEBUG  WinuiInstallationPage: target_drive=C:,  installation_size=18000MB, distro_name=Ubuntu, language=en_US,  locale=en_US.UTF-8, username=phong
09-18 19:15 INFO   root: Received settings
09-18 19:15 DEBUG  CommonBackend: Searching for local CD
09-18 19:15 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\casp  er\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:15 DEBUG  CommonBackend: Searching for local ISO
09-18 19:15 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pyl2E0  E.tmp\translations,  languages=['en_US', 'en']
09-18 19:15 DEBUG  TaskList: # Running tasklist...
09-18 19:15 DEBUG  TaskList: ## Running select_target_dir...
09-18 19:15 INFO   WindowsBackend: Installing into C:\ubuntu
09-18 19:15 DEBUG  TaskList: ## Finished select_target_dir
09-18 19:15 DEBUG  TaskList: ## Running create_dir_structure...
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-18 19:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-18 19:15 DEBUG  TaskList: ## Finished create_dir_structure
09-18 19:15 DEBUG  TaskList: ## Running uncompress_target_dir...
09-18 19:15 DEBUG  TaskList: ## Finished uncompress_target_dir
09-18 19:15 DEBUG  TaskList: ## Running create_uninstaller...
09-18 19:15 DEBUG  WindowsBackend: Copying uninstaller  C:\Users\Phong\AppData\Local\Temp\$PowerISO$\wubi.  exe ->  C:\ubuntu\uninstall-wubi.exe
09-18 19:15 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  UninstallString C:\ubuntu\uninstall-wubi.exe
09-18 19:15 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  InstallationDir C:\ubuntu
09-18 19:15 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi DisplayName  Ubuntu
09-18 19:15 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi DisplayIcon  C:\ubuntu\Ubuntu.ico
09-18 19:15 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  DisplayVersion 14.04-rev286
09-18 19:15 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi Publisher  Ubuntu
09-18 19:15 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-18 19:15 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-18 19:15 DEBUG  TaskList: ## Finished create_uninstaller
09-18 19:15 DEBUG  TaskList: ## Running copy_installation_files...
09-18 19:15 DEBUG  WindowsBackend: Copying  C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\data  \custom-installation  -> C:\ubuntu\install\custom-installation
09-18 19:15 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\winb  oot -> C:\ubuntu\winboot
09-18 19:15 DEBUG  WindowsBackend: Copying  C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\data  \images\Ubuntu.ico  -> C:\ubuntu\Ubuntu.ico
09-18 19:15 DEBUG  TaskList: ## Finished copy_installation_files
09-18 19:15 DEBUG  TaskList: ## Running get_iso...
09-18 19:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-18 19:15 DEBUG  TaskList: New task get_metalink
09-18 19:15 DEBUG  TaskList: ### Running get_metalink...
09-18 19:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubu...amd64.metalink]("http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink") > C:\ubuntu\install
09-18 19:15 DEBUG  downloader: Download start  filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink,  url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink,  basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-18 19:15 DEBUG  downloader: download finished (read 45848 bytes)
09-18 19:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-18 19:15 DEBUG  downloader: Download start  filename=C:\ubuntu\install\MD5SUMS-metalink,  url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink,  basename=MD5SUMS-metalink, length=560, text=None
09-18 19:15 DEBUG  downloader: download finished (read 560 bytes)
09-18 19:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-18 19:15 DEBUG  downloader: Download start  filename=C:\ubuntu\install\MD5SUMS-metalink.gpg,  url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg,  basename=MD5SUMS-metalink.gpg, length=198, text=None
09-18 19:15 DEBUG  downloader: download finished (read 198 bytes)
09-18 19:15 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-18 19:15 INFO   saplog: Checking block bindings..
09-18 19:15 INFO   saplog: Key verified successfully.
09-18 19:15 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink


09-18 19:15 ERROR  CommonBackend: The md5 of the metalink does match
09-18 19:15 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-18 19:15 DEBUG  TaskList: ### Finished get_metalink
09-18 19:15 DEBUG  TaskList: New task download
09-18 19:15 DEBUG  TaskList: ### Running download...
09-18 19:15 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/14.04.1/u...64.iso.torrent]("http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent") > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:15 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.




09-18 19:15 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


 in task download
09-18 19:15 DEBUG  TaskList: ### Finished download
09-18 19:15 ERROR  root: Could not remove: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:15 DEBUG  TaskList: New task download
09-18 19:15 DEBUG  TaskList: ### Running download...
09-18 19:15 DEBUG  downloader: downloading [http://mirror.vutbr.cz/ubuntu/releas...ktop-amd64.iso]("http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso") > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:15 DEBUG  downloader: Download start  filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso,  url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso,  basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None
09-18 19:24 DEBUG  TaskList: ### Finished download
09-18 19:24 DEBUG  downloader: download finished (read 1010827264 bytes)
09-18 19:24 DEBUG  TaskList: New task check_iso
09-18 19:24 DEBUG  TaskList: ### Running check_iso...
09-18 19:24 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:24 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:24 ERROR  WindowsBackend: Error executing command
>>command=C:\Users\Phong\AppData\Local\Temp\pyl2E0  E.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process  cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\Phong\AppData\Local\Temp\pyl2E0  E.tmp\bin\7z.exe l C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
>>retval=2
>>stderr=


7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18






Error: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso: The process  cannot access the file because it is being used by another process.












Errors: 1
>>stdout=
09-18 19:24 DEBUG  WindowsBackend: command  >>C:\Users\Phong\AppData\Local\Temp\pyl2E0E.tmp\bi  n\7z.exe l  C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:24 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-18 19:24 DEBUG  TaskList: ### Finished check_iso
09-18 19:24 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:24 DEBUG  TaskList: # Cancelling tasklist
09-18 19:24 DEBUG  TaskList: # Finished tasklist
09-18 19:24 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 595, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 441, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:39 INFO   root: === wubi 14.04 rev286 ===
09-18 19:39 DEBUG  root: Logfile is c:\users\phong\appdata\local\temp\wubi-14.04-rev286.log
09-18 19:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Phong\\Desktop\\Ubuntu\\wubi.e  xe"']
09-18 19:39 DEBUG  CommonBackend: data_dir=C:\Users\Phong\AppData\Local\Temp\pylBBAD  .tmp\data
09-18 19:39 DEBUG  WindowsBackend: 7z=C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\b  in\7z.exe
09-18 19:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\St  art Menu\Programs\Startup
09-18 19:39 DEBUG  CommonBackend: Fetching basic info...
09-18 19:39 DEBUG  CommonBackend: original_exe=C:\Users\Phong\Desktop\Ubuntu\wubi.ex  e
09-18 19:39 DEBUG  CommonBackend: platform=win32
09-18 19:39 DEBUG  CommonBackend: osname=nt
09-18 19:39 DEBUG  CommonBackend: language=en_CA
09-18 19:39 DEBUG  CommonBackend: encoding=cp1252
09-18 19:39 DEBUG  WindowsBackend: arch=amd64
09-18 19:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pylBBAD.  tmp\data\isolist.ini
09-18 19:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 19:39 DEBUG  WindowsBackend: Fetching host info...
09-18 19:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer  sion\Uninstall\Wubi
09-18 19:39 DEBUG  WindowsBackend: windows version=vista
09-18 19:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 19:39 DEBUG  WindowsBackend: windows_sp=None
09-18 19:39 DEBUG  WindowsBackend: windows_build=7601
09-18 19:39 DEBUG  WindowsBackend: gmt=-5
09-18 19:39 DEBUG  WindowsBackend: country=US
09-18 19:39 DEBUG  WindowsBackend: timezone=America/New_York
09-18 19:39 DEBUG  WindowsBackend: windows_username=Phong
09-18 19:39 DEBUG  WindowsBackend: user_full_name=Phong
09-18 19:39 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 19:39 DEBUG  WindowsBackend: windows_language_code=1033
09-18 19:39 DEBUG  WindowsBackend: windows_language=English
09-18 19:39 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 19:39 DEBUG  WindowsBackend: bootloader=vista
09-18 19:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 185809.535156 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(C: hd 185809.535156 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 19:39 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-18 19:39 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-18 19:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-18 19:39 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 19:39 DEBUG  WindowsBackend: keyboard_layout=us
09-18 19:39 DEBUG  WindowsBackend: keyboard_variant=
09-18 19:39 DEBUG  CommonBackend: python locale=('en_CA', 'cp1252')
09-18 19:39 DEBUG  CommonBackend: locale=en_CA.UTF-8
09-18 19:39 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 19:39 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 19:39 DEBUG  CommonBackend: Searching for local CDs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 INFO   root: Already installed, running the uninstaller...
09-18 19:39 INFO   root: Running the uninstaller...
09-18 19:39 INFO   CommonBackend: This is the uninstaller running
09-18 19:39 DEBUG  WindowsFrontend: __init__...
09-18 19:39 DEBUG  WindowsFrontend: on_init...
09-18 19:39 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pylBBA  D.tmp\translations,  languages=['en_CA', 'en']
09-18 19:39 INFO   root: Received settings
09-18 19:39 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pylBBA  D.tmp\translations,  languages=['en_CA', 'en']
09-18 19:39 DEBUG  TaskList: # Running tasklist...
09-18 19:39 DEBUG  TaskList: ## Running Remove bootloader entry...
09-18 19:39 DEBUG  WindowsBackend: Could not find bcd id
09-18 19:39 DEBUG  WindowsBackend: undo_bootini C:
09-18 19:39 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 185809.535156 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: undo_bootini E:
09-18 19:39 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
09-18 19:39 DEBUG  TaskList: ## Finished Remove bootloader entry
09-18 19:39 DEBUG  TaskList: ## Running Remove target dir...
09-18 19:39 DEBUG  CommonBackend: Deleting C:\ubuntu
09-18 19:39 DEBUG  TaskList: ## Finished Remove target dir
09-18 19:39 DEBUG  TaskList: ## Running Remove registry key...
09-18 19:39 DEBUG  TaskList: ## Finished Remove registry key
09-18 19:39 DEBUG  TaskList: # Finished tasklist
09-18 19:39 INFO   root: Almost finished uninstalling
09-18 19:39 INFO   root: Finished uninstallation
09-18 19:39 DEBUG  CommonBackend: Fetching basic info...
09-18 19:39 DEBUG  CommonBackend: original_exe=C:\Users\Phong\Desktop\Ubuntu\wubi.ex  e
09-18 19:39 DEBUG  CommonBackend: platform=win32
09-18 19:39 DEBUG  CommonBackend: osname=nt
09-18 19:39 DEBUG  WindowsBackend: arch=amd64
09-18 19:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Phong\AppData\Local\Temp\pylBBAD.  tmp\data\isolist.ini
09-18 19:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-18 19:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
09-18 19:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-18 19:39 DEBUG  WindowsBackend: Fetching host info...
09-18 19:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer  sion\Uninstall\Wubi
09-18 19:39 DEBUG  WindowsBackend: windows version=vista
09-18 19:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-18 19:39 DEBUG  WindowsBackend: windows_sp=None
09-18 19:39 DEBUG  WindowsBackend: windows_build=7601
09-18 19:39 DEBUG  WindowsBackend: gmt=-5
09-18 19:39 DEBUG  WindowsBackend: country=US
09-18 19:39 DEBUG  WindowsBackend: timezone=America/New_York
09-18 19:39 DEBUG  WindowsBackend: windows_username=Phong
09-18 19:39 DEBUG  WindowsBackend: user_full_name=Phong
09-18 19:39 DEBUG  WindowsBackend: user_directory=C:\Users\Phong
09-18 19:39 DEBUG  WindowsBackend: windows_language_code=1033
09-18 19:39 DEBUG  WindowsBackend: windows_language=English
09-18 19:39 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
09-18 19:39 DEBUG  WindowsBackend: bootloader=vista
09-18 19:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 186776.726563 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(C: hd 186776.726563 mb free ntfs)
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
09-18 19:39 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
09-18 19:39 DEBUG  WindowsBackend: uninstaller_path=None
09-18 19:39 DEBUG  WindowsBackend: previous_target_dir=None
09-18 19:39 DEBUG  WindowsBackend: previous_distro_name=None
09-18 19:39 DEBUG  WindowsBackend: keyboard_id=67702793
09-18 19:39 DEBUG  WindowsBackend: keyboard_layout=us
09-18 19:39 DEBUG  WindowsBackend: keyboard_variant=
09-18 19:39 DEBUG  WindowsBackend: total_memory_mb=2939.99609375
09-18 19:39 DEBUG  CommonBackend: Searching ISOs on USB devices
09-18 19:39 DEBUG  CommonBackend: Searching for local CDs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
09-18 19:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:39 INFO   root: Running the installer...
09-18 19:39 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pylBBA  D.tmp\translations,  languages=['en_CA', 'en']
09-18 19:39 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pylBBA  D.tmp\translations,  languages=['en_CA', 'en']
09-18 19:40 DEBUG  WinuiInstallationPage: target_drive=C:,  installation_size=30000MB, distro_name=Ubuntu, language=en_US,  locale=en_US.UTF-8, username=quantom
09-18 19:40 INFO   root: Received settings
09-18 19:40 DEBUG  CommonBackend: Searching for local CD
09-18 19:40 DEBUG  Distro:   checking whether C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp is a valid Ubuntu CD
09-18 19:40 DEBUG  Distro:     does not contain C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\casp  er\filesystem.squashfs
09-18 19:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-18 19:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-18 19:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-18 19:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-18 19:40 DEBUG  CommonBackend: Searching for local ISO
09-18 19:40 INFO   WinuiPage: appname=wubi,  localedir=C:\Users\Phong\AppData\Local\Temp\pylBBA  D.tmp\translations,  languages=['en_US', 'en']
09-18 19:40 DEBUG  TaskList: # Running tasklist...
09-18 19:40 DEBUG  TaskList: ## Running select_target_dir...
09-18 19:40 INFO   WindowsBackend: Installing into C:\ubuntu
09-18 19:40 DEBUG  TaskList: ## Finished select_target_dir
09-18 19:40 DEBUG  TaskList: ## Running create_dir_structure...
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-18 19:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-18 19:40 DEBUG  TaskList: ## Finished create_dir_structure
09-18 19:40 DEBUG  TaskList: ## Running uncompress_target_dir...
09-18 19:40 DEBUG  TaskList: ## Finished uncompress_target_dir
09-18 19:40 DEBUG  TaskList: ## Running create_uninstaller...
09-18 19:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Phong\Desktop\Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-18 19:40 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  UninstallString C:\ubuntu\uninstall-wubi.exe
09-18 19:40 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  InstallationDir C:\ubuntu
09-18 19:40 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi DisplayName  Ubuntu
09-18 19:40 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi DisplayIcon  C:\ubuntu\Ubuntu.ico
09-18 19:40 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi  DisplayVersion 14.04-rev286
09-18 19:40 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi Publisher  Ubuntu
09-18 19:40 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-18 19:40 DEBUG  registry: Setting registry key -2147483646  Software\Microsoft\Windows\CurrentVersion\Uninstal  l\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-18 19:40 DEBUG  TaskList: ## Finished create_uninstaller
09-18 19:40 DEBUG  TaskList: ## Running copy_installation_files...
09-18 19:40 DEBUG  WindowsBackend: Copying  C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\data  \custom-installation  -> C:\ubuntu\install\custom-installation
09-18 19:40 DEBUG  WindowsBackend: Copying C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\winb  oot -> C:\ubuntu\winboot
09-18 19:40 DEBUG  WindowsBackend: Copying  C:\Users\Phong\AppData\Local\Temp\pylBBAD.tmp\data  \images\Ubuntu.ico  -> C:\ubuntu\Ubuntu.ico
09-18 19:40 DEBUG  TaskList: ## Finished copy_installation_files
09-18 19:40 DEBUG  TaskList: ## Running get_iso...
09-18 19:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-18 19:40 DEBUG  TaskList: New task get_metalink
09-18 19:40 DEBUG  TaskList: ### Running get_metalink...
09-18 19:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubu...amd64.metalink]("http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink") > C:\ubuntu\install
09-18 19:40 DEBUG  downloader: Download start  filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink,  url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink,  basename=ubuntu-14.04-desktop-amd64.metalink, length=45848, text=None
09-18 19:40 DEBUG  downloader: download finished (read 45848 bytes)
09-18 19:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > C:\ubuntu\install
09-18 19:40 DEBUG  downloader: Download start  filename=C:\ubuntu\install\MD5SUMS-metalink,  url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink,  basename=MD5SUMS-metalink, length=560, text=None
09-18 19:40 DEBUG  downloader: download finished (read 560 bytes)
09-18 19:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
09-18 19:40 DEBUG  downloader: Download start  filename=C:\ubuntu\install\MD5SUMS-metalink.gpg,  url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg,  basename=MD5SUMS-metalink.gpg, length=198, text=None
09-18 19:40 DEBUG  downloader: download finished (read 198 bytes)
09-18 19:40 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-18 19:40 INFO   saplog: Checking block bindings..
09-18 19:40 INFO   saplog: Key verified successfully.
09-18 19:40 DEBUG  CommonBackend: metalink md5sums:
a6e180b2c31d7b1eea24679b8205f01c *ubuntu-14.04-desktop-amd64.metalink
d2c9e1eb6bc9b1ba67c06fdd4fd0347e *ubuntu-14.04-desktop-i386.metalink
b87f557d59555df5f4577d2700292f1f *ubuntu-14.04-server-amd64.metalink
63bf3b3b0eab70e6f8291605aea3d924 *ubuntu-14.04-server-i386.metalink
d1cbb30d6eab71cca40f3df717dc210c *ubuntu-14.04.1-desktop-amd64.metalink
3ae778859e3e1f830bc31d9d36c74d21 *ubuntu-14.04.1-desktop-i386.metalink
3bb29eaa4d905b0e6edac12b5d7d3d91 *ubuntu-14.04.1-server-amd64.metalink
38cd72646a2299b401fe7de19c54fa5b *ubuntu-14.04.1-server-i386.metalink


09-18 19:40 ERROR  CommonBackend: The md5 of the metalink does match
09-18 19:40 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
09-18 19:40 DEBUG  TaskList: ### Finished get_metalink
09-18 19:40 DEBUG  TaskList: New task download
09-18 19:40 DEBUG  TaskList: ### Running download...
09-18 19:40 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/14.04.1/u...64.iso.torrent]("http://releases.ubuntu.com/14.04.1/ubuntu-14.04-desktop-amd64.iso.torrent") > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:40 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.




09-18 19:40 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 90, in add
  File "\lib\bittorrent\Rerequester.py", line 105, in postrequest
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: rejected by tracker - Requested download is not authorized for use with this tracker.


 in task download
09-18 19:40 DEBUG  TaskList: ### Finished download
09-18 19:40 ERROR  root: Could not remove: C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 426, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-14.04-desktop-amd64.iso'
09-18 19:40 DEBUG  TaskList: New task download
09-18 19:40 DEBUG  TaskList: ### Running download...
09-18 19:40 DEBUG  downloader: downloading [http://mirror.vutbr.cz/ubuntu/releas...ktop-amd64.iso]("http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso") > C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso
09-18 19:40 DEBUG  downloader: Download start  filename=C:\ubuntu\install\ubuntu-14.04-desktop-amd64.iso,  url=http://mirror.vutbr.cz/ubuntu/releases/14.04.1/ubuntu-14.04-desktop-amd64.iso,  basename=ubuntu-14.04-desktop-amd64.iso, length=1010827264, text=None
```

---

### Post by yancek on 2014-09-19
> So could you send me to a post how to install it without WUBI?

The first part of the tutorial has a lot of useful information, scroll down further to "Installation Guide, Step by Step"

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by edwin13 on 2014-09-20
Thanks yancek!

---

### Post by filiaap on 2014-09-23
I installed Ubuntu with WUBI and mounted ISO with WinCDEmu before setup. During setup you should connect to network or connect to Wifi imediately after system start for initial setup to get all updates and especially the language files. That's it. Then have fun with a system booting from an image instead of repartitioning.

Regards

Flip

---

### Post by Lambert_Notasheep on 2014-12-01
I found myself with a similar problem, Permission Denied error and all. When I went to the link yancek provided and followed its instructions, I still got the Permission Denied error. Is there any other manner of method, some other link?

---

### Post by the-tech-kid on 2014-12-02
Go to terminal and type
sudo do-release-upgrade

---

### Post by mastablasta on 2014-12-03
wubi is no longer supported. do not install with wubi. use dualboot or install in virtualbox instead.

---

