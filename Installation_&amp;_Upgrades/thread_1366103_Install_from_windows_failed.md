---
title: "Install from windows failed"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by rmjohnson144 on 2009-12-28
I tried to install Ubuntu from within windows 7 Ult x64 as a fresh install failed as well and I got an error(invalid argument).  not sure what to make of it.

Here's the logfile:
```
12-27 22:31 INFO   root: === wubi 9.10ubuntu1 rev160 ===
12-27 22:31 DEBUG  root: Logfile is c:\users\mark\appdata\local\temp\wubi-9.10ubuntu1-rev160.log
12-27 22:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
12-27 22:31 DEBUG  CommonBackend: data_dir=C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\data
12-27 22:31 DEBUG  WindowsBackend: 7z=C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\bin\7z.exe
12-27 22:31 DEBUG  CommonBackend: Fetching basic info...
12-27 22:31 DEBUG  CommonBackend: original_exe=E:\wubi.exe
12-27 22:31 DEBUG  CommonBackend: platform=win32
12-27 22:31 DEBUG  CommonBackend: osname=nt
12-27 22:31 DEBUG  CommonBackend: language=en_US
12-27 22:31 DEBUG  CommonBackend: encoding=cp1252
12-27 22:31 DEBUG  WindowsBackend: arch=amd64
12-27 22:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\data\isolist.ini
12-27 22:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 22:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 22:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 22:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 22:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 22:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 22:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 22:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 22:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 22:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
12-27 22:31 DEBUG  WindowsBackend: Fetching host info...
12-27 22:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 22:31 DEBUG  WindowsBackend: windows version=vista
12-27 22:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
12-27 22:31 DEBUG  WindowsBackend: windows_sp=None
12-27 22:31 DEBUG  WindowsBackend: windows_build=7600
12-27 22:31 DEBUG  WindowsBackend: gmt=-8
12-27 22:31 DEBUG  WindowsBackend: country=US
12-27 22:31 DEBUG  WindowsBackend: timezone=America/Los_Angeles
12-27 22:31 DEBUG  WindowsBackend: windows_username=Mark
12-27 22:31 DEBUG  WindowsBackend: user_full_name=Mark
12-27 22:31 DEBUG  WindowsBackend: user_directory=C:\Users\Mark
12-27 22:31 DEBUG  WindowsBackend: windows_language_code=1033
12-27 22:31 DEBUG  WindowsBackend: windows_language=English
12-27 22:31 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core  CPU      E5200  @ 2.50GHz
12-27 22:31 DEBUG  WindowsBackend: bootloader=vista
12-27 22:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 421560.414063 mb free ntfs)
12-27 22:31 DEBUG  WindowsBackend: drive=Drive(C: hd 421560.414063 mb free ntfs)
12-27 22:31 DEBUG  WindowsBackend: drive=Drive(D: hd 71.640625 mb free ntfs)
12-27 22:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-27 22:31 DEBUG  WindowsBackend: drive=Drive(F: hd 1539357.19531 mb free ntfs)
12-27 22:31 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-27 22:31 DEBUG  WindowsBackend: drive=Drive(H: hd 149597.0 mb free fat32)
12-27 22:31 DEBUG  WindowsBackend: drive=Drive(I: hd 433882.566406 mb free ntfs)
12-27 22:31 DEBUG  WindowsBackend: uninstaller_path=None
12-27 22:31 DEBUG  WindowsBackend: previous_target_dir=None
12-27 22:31 DEBUG  WindowsBackend: previous_distro_name=None
12-27 22:31 DEBUG  WindowsBackend: keyboard_id=67699721
12-27 22:31 DEBUG  WindowsBackend: keyboard_layout=us
12-27 22:31 DEBUG  WindowsBackend: keyboard_variant=
12-27 22:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-27 22:31 DEBUG  CommonBackend: locale=en_US.UTF-8
12-27 22:31 DEBUG  WindowsBackend: total_memory_mb=4095.1171875
12-27 22:31 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 22:31 DEBUG  CommonBackend: Searching for local CDs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Ubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Ubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Ubuntu Netbook Remix CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Kubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Kubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Kubuntu Netbook CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Xubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Xubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Mythbuntu CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp is a valid Mythbuntu CD
12-27 22:31 DEBUG  Distro:     does not contain C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 22:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 22:31 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release amd64 (20091027)
12-27 22:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091027', 'codename': 'Karmic Koala', 'arch': 'amd64'}
12-27 22:31 INFO   Distro: Found a valid CD for Ubuntu: E:\
12-27 22:31 INFO   root: Running the CD menu...
12-27 22:31 DEBUG  WindowsFrontend: __init__...
12-27 22:31 DEBUG  WindowsFrontend: on_init...
12-27 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\translations, languages=['en_US', 'en']
12-27 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\translations, languages=['en_US', 'en']
12-27 22:31 INFO   root: CD menu finished
12-27 22:31 INFO   root: Running the installer...
12-27 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\translations, languages=['en_US', 'en']
12-27 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\translations, languages=['en_US', 'en']
12-27 22:31 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mark
12-27 22:31 INFO   root: Received settings
12-27 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\translations, languages=['en_US', 'en']
12-27 22:31 DEBUG  TaskList: # Running tasklist...
12-27 22:31 DEBUG  TaskList: ## Running select_target_dir...
12-27 22:31 INFO   WindowsBackend: Installing into C:\ubuntu
12-27 22:31 DEBUG  TaskList: ## Finished select_target_dir
12-27 22:31 DEBUG  TaskList: ## Running create_dir_structure...
12-27 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-27 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-27 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-27 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-27 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-27 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-27 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-27 22:31 DEBUG  TaskList: ## Finished create_dir_structure
12-27 22:31 DEBUG  TaskList: ## Running uncompress_target_dir...
12-27 22:31 DEBUG  TaskList: ## Finished uncompress_target_dir
12-27 22:31 DEBUG  TaskList: ## Running create_uninstaller...
12-27 22:31 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-27 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-27 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-27 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-27 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-27 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160
12-27 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-27 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-27 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-27 22:31 DEBUG  TaskList: ## Finished create_uninstaller
12-27 22:31 DEBUG  TaskList: ## Running copy_installation_files...
12-27 22:31 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-27 22:31 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\winboot -> C:\ubuntu\winboot
12-27 22:31 DEBUG  WindowsBackend: Copying C:\Users\Mark\AppData\Local\Temp\pyl1E87.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-27 22:31 DEBUG  TaskList: ## Finished copy_installation_files
12-27 22:31 DEBUG  TaskList: ## Running get_iso...
12-27 22:31 DEBUG  TaskList: New task copy_file
12-27 22:31 DEBUG  TaskList: ### Running copy_file...
12-27 22:41 DEBUG  TaskList: ### Finished copy_file
12-27 22:41 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
12-27 22:41 DEBUG  TaskList: # Cancelling tasklist
12-27 22:41 DEBUG  TaskList: New task check_iso
12-27 22:41 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 126, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 22] Invalid argument
12-27 22:41 DEBUG  CommonBackend: Searching for local ISO
12-27 22:41 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-27 22:41 DEBUG  TaskList: New task get_metalink
12-27 22:41 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
12-27 22:41 DEBUG  TaskList: # Cancelling tasklist
12-27 22:41 DEBUG  TaskList: # Finished tasklist

```

Any suggestions?
-=Mark=-

---

### Post by alswilling on 2010-01-01
I'm new to Ubuntu, too; but I had basically the same problem that you had, both when trying to install from the CD and when trying to install from Wubi Installer. The basic difference between our experiences is the Windows OS. You are running Windows 7, and I am running Windows XP SP2; but the errors encountered while trying to install Ubuntu are the same. Hopefully sharing my experience will help you solve your problem. 

The first error I received was that the installer could not find the ISO, just as your error message indicates happened to you. The reason I received that error message was because I saved the downloaded ISO to a different physical drive from the root drive (C:\). I moved the ISO to the C:\ drive (C:\WubiInstaller\) and started the installation again, and that cleared up that error. However, my second attempt to install was more troublesome.

On my second attempt to install, Wubi indicated that Ubuntu had installed and that I needed to reboot in order to finish the installation. What it didn't say was that I needed to reboot into Ubuntu in order to finish the installation. So, after rebooting into Windows and waiting to no avail, I rebooted and selected Ubuntu as the OS to which to boot. When Ubuntu began the process of finishing the installation, I encountered another error, only instead of an outright error message, the screen went black. When I pressed the Enter or Space Bar--or any key--the code reappeared, and it acted as though the installation was continuing, then stopped altogether. I finally shut down the computer and restarted it, booting back into Windows. I uninstalled what Wubi had installed and searched the Web for solutions. 

I finally stumbled upon an Ubuntu forum that talked about problems using Nvidia GeForce graphics cards with Ubuntu. I had an Nvidia GeForce 4 MX 4000 video card installed, but I also have integrated Intel Graphics, which I had disabled when I installed the Nvidia card. After enabling the Intel Graphics and disabling and REMOVING the Nvidia card, Ubuntu installed with no problem whatsoever then rebooted the machine. After rebooting into Ubuntu, the OS worked perfectly--except for the Netgear wireless adapter, which I am now researching to see if I need new drivers and if the adapter is compatible with Ubuntu. If you are running a video card other than the one provided with your machine, then you will probably have to remove it and revert back to the old card in order to get Ubuntu to install. Then you can download and install drivers for the video card that are compatible with the version of Ubuntu that you are trying to install.

So, if the ISO is on a drive other than C:\, then you should move the ISO file onto C:\. If you are trying to install Ubuntu using the Wubi Installer (recommended), then you will have to move the ISO file into the same directory as the Wubi Installer. Otherwise Wubi will try to download a torrent of the ISO, which can take anywhere from a minute to forever, depending on your Internet connection and other torrent related factors.

If you are running any graphics card other than the one that came installed on your machine, then you may have to remove it before Ubuntu can finish installing.

I hope this helps, even though it may sound like the blind leading the blind.

Al

---

### Post by northrup on 2010-01-01
I had the same issue when I tried to install Wubi on an eMachines box.  It worked fine after a couple more tries with different versions.  I'd try it with an older (or newer) version of Wubi, then if it works, upgrade from there.

---

### Post by rmjohnson144 on 2010-01-01
Thanks for the replies, but I found out that the wubi install wasn't for me.  I read it was slower.  so, I just rebooted and installed from the booted ubuntu CD and told it to use the auto-partitioning of my C:\ drive to have ubuntu and win7 on the same drive and it worked like a charm.  

Thanks again for the help.
-=Mark=-

---

