---
title: "Unable to install Ubuntu 10.04.2"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by karan999 on 2011-03-22
**Hi all,**
I successfully created a live usb to boot ubuntu but, i want it installed on my hard disk.
i have 500GB hard disk.
 
While booting from live USB,i do get an option to Install / view before install or boot from hard drive and other options.
 
But when i click on install ubuntu,my computer just restarts and the monitor screen goes black.thats it.
 
Currently there are 4 partitions on my hard disk - 
(assume original size)
C:\ of size 53GB.
D:\ of size 210GB
E:\ of size 210GB
G:\ of size 10GB to boot ubuntu(not installed).
 
 
i tried mounting the **ubuntu-10.04.2-desktop-amd64.iso.**
then i run wubi for the installation.there after choosing my G:\drive for installation and 6GB as installation size when i click on install, after a few seconds during installation i get a error message which i have uploaded for you to see - 
 
image right before the error message is displayed - 
 
[http://hotfile.com/dl/111334195/b851a75/image_before_error_appears.png.html](http://hotfile.com/dl/111334195/b851a75/image_before_error_appears.png.html)
 
 
error message - 
 
[hotfile.com/dl/111254682/5643863/error.png.[COLOR=#0000ff]html[/COLOR]]("http://hotfile.com/dl/111254682/5643863/error.png.html")
 
 
This is the **wubi-10.04.2-rev191** log file generated. - 
 
```
03-22 05:17 INFO   root: === wubi 10.04.2 rev191 ===
03-22 05:17 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 05:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-22 05:17 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\data
03-22 05:17 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\bin\7z.exe
03-22 05:17 DEBUG  CommonBackend: Fetching basic info...
03-22 05:17 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 05:17 DEBUG  CommonBackend: platform=win32
03-22 05:17 DEBUG  CommonBackend: osname=nt
03-22 05:17 DEBUG  CommonBackend: language=en_US
03-22 05:17 DEBUG  CommonBackend: encoding=cp1252
03-22 05:17 DEBUG  WindowsBackend: arch=amd64
03-22 05:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\data\isolist.ini
03-22 05:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 05:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 05:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 05:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 05:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 05:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 05:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 05:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 05:17 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 05:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 05:17 DEBUG  WindowsBackend: Fetching host info...
03-22 05:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 05:17 DEBUG  WindowsBackend: windows version=vista
03-22 05:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 05:17 DEBUG  WindowsBackend: windows_sp=None
03-22 05:17 DEBUG  WindowsBackend: windows_build=7601
03-22 05:17 DEBUG  WindowsBackend: gmt=5
03-22 05:17 DEBUG  WindowsBackend: country=US
03-22 05:17 DEBUG  WindowsBackend: timezone=America/New_York
03-22 05:17 DEBUG  WindowsBackend: windows_username=Administrator
03-22 05:17 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 05:17 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 05:17 DEBUG  WindowsBackend: windows_language_code=1033
03-22 05:17 DEBUG  WindowsBackend: windows_language=English
03-22 05:17 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 05:17 DEBUG  WindowsBackend: bootloader=vista
03-22 05:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20486.71875 mb free ntfs)
03-22 05:17 DEBUG  WindowsBackend: drive=Drive(C: hd 20486.71875 mb free ntfs)
03-22 05:17 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:17 DEBUG  WindowsBackend: drive=Drive(E: hd 13169.09375 mb free ntfs)
03-22 05:17 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 05:17 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.81640625 mb free ntfs)
03-22 05:17 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 05:17 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 05:17 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 05:17 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 05:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 05:17 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 05:17 DEBUG  WindowsBackend: keyboard_layout=us
03-22 05:17 DEBUG  WindowsBackend: keyboard_variant=
03-22 05:17 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 05:17 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 05:17 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 05:17 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 05:17 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:17 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:17 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:17 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:17 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:17 DEBUG  CommonBackend: Searching for local CDs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Ubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Kubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:17 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:17 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:17 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:17 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 05:17 INFO   root: Running the CD menu...
03-22 05:17 DEBUG  WindowsFrontend: __init__...
03-22 05:17 DEBUG  WindowsFrontend: on_init...
03-22 05:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\translations, languages=['en_US', 'en']
03-22 05:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\translations, languages=['en_US', 'en']
03-22 05:17 INFO   root: CD menu finished
03-22 05:17 INFO   root: Running the installer...
03-22 05:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\translations, languages=['en_US', 'en']
03-22 05:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\translations, languages=['en_US', 'en']
03-22 05:18 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-22 05:18 INFO   root: Received settings
03-22 05:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\translations, languages=['en_US', 'en']
03-22 05:18 DEBUG  TaskList: # Running tasklist...
03-22 05:18 DEBUG  TaskList: ## Running select_target_dir...
03-22 05:18 INFO   WindowsBackend: Installing into G:\ubuntu
03-22 05:18 DEBUG  TaskList: ## Finished select_target_dir
03-22 05:18 DEBUG  TaskList: ## Running create_dir_structure...
03-22 05:18 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-22 05:18 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-22 05:18 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-22 05:18 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-22 05:18 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-22 05:18 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-22 05:18 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-22 05:18 DEBUG  TaskList: ## Finished create_dir_structure
03-22 05:18 DEBUG  TaskList: ## Running uncompress_target_dir...
03-22 05:18 DEBUG  TaskList: ## Finished uncompress_target_dir
03-22 05:18 DEBUG  TaskList: ## Running create_uninstaller...
03-22 05:18 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-22 05:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-22 05:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-22 05:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-22 05:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-22 05:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
03-22 05:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-22 05:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-22 05:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-22 05:18 DEBUG  TaskList: ## Finished create_uninstaller
03-22 05:18 DEBUG  TaskList: ## Running copy_installation_files...
03-22 05:18 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-22 05:18 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\winboot -> G:\ubuntu\winboot
03-22 05:18 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylE714.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-22 05:18 DEBUG  TaskList: ## Finished copy_installation_files
03-22 05:18 DEBUG  TaskList: ## Running get_iso...
03-22 05:18 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:18 DEBUG  TaskList: New task is_valid_iso
03-22 05:18 DEBUG  TaskList: ### Running is_valid_iso...
03-22 05:18 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:18 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:18 DEBUG  TaskList: ### Finished is_valid_iso
03-22 05:18 DEBUG  TaskList: New task check_iso
03-22 05:18 DEBUG  TaskList: ### Running check_iso...
03-22 05:18 DEBUG  CommonBackend: Checking E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:18 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:18 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:18 DEBUG  TaskList: New task get_metalink
03-22 05:18 DEBUG  TaskList: #### Running get_metalink...
03-22 05:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > G:\ubuntu\install
03-22 05:18 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
03-22 05:18 DEBUG  downloader: download finished (read 39020 bytes)
03-22 05:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > G:\ubuntu\install
03-22 05:18 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
03-22 05:18 DEBUG  downloader: download finished (read 651 bytes)
03-22 05:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > G:\ubuntu\install
03-22 05:18 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-22 05:18 DEBUG  downloader: download finished (read 198 bytes)
03-22 05:18 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-22 05:18 INFO   saplog: Checking block bindings..
03-22 05:18 INFO   saplog: Key verified successfully.
03-22 05:18 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink
03-22 05:18 DEBUG  TaskList: #### Finished get_metalink
03-22 05:18 DEBUG  TaskList: New task get_file_md5
03-22 05:18 DEBUG  TaskList: #### Running get_file_md5...
03-22 05:18 DEBUG  TaskList: #### Finished get_file_md5
03-22 05:18 DEBUG  TaskList: ### Finished check_iso
03-22 05:18 DEBUG  TaskList: New task copy_file
03-22 05:18 DEBUG  CommonBackend: Copying E:\ubuntu-10.04.2-desktop-amd64.iso > G:\ubuntu\install\installation.iso
03-22 05:18 DEBUG  TaskList: ### Running copy_file...
03-22 05:18 DEBUG  TaskList: ### Finished copy_file
03-22 05:18 DEBUG  TaskList: ## Finished get_iso
03-22 05:18 DEBUG  TaskList: ## Running extract_kernel...
03-22 05:18 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
03-22 05:18 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
03-22 05:18 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
03-22 05:18 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
03-22 05:18 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-22 05:18 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-22 05:18 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 41d2d275b0aed279030980587f6de7e9 == 41d2d275b0aed279030980587f6de7e9
03-22 05:18 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-22 05:18 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 774fcb24611ab59898b1e51df6cfd8d6 == 774fcb24611ab59898b1e51df6cfd8d6
03-22 05:18 DEBUG  TaskList: ## Finished extract_kernel
03-22 05:18 DEBUG  TaskList: ## Running choose_disk_sizes...
03-22 05:18 DEBUG  WindowsBackend: total size=6000
  root=5744
  swap=256
  home=0
  usr=0
03-22 05:18 DEBUG  TaskList: ## Finished choose_disk_sizes
03-22 05:18 DEBUG  TaskList: ## Running create_preseed...
03-22 05:18 DEBUG  TaskList: ## Finished create_preseed
03-22 05:18 DEBUG  TaskList: ## Running modify_bootloader...
03-22 05:18 DEBUG  TaskList: New task modify_bcd
03-22 05:18 DEBUG  TaskList: ### Running modify_bcd...
03-22 05:18 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 20486.71875 mb free ntfs)
03-22 05:18 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437c-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437c-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 05:18 DEBUG  TaskList: # Cancelling tasklist
03-22 05:18 DEBUG  TaskList: New task modify_bcd
03-22 05:18 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437c-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437c-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 05:18 DEBUG  TaskList: New task modify_bcd
03-22 05:18 DEBUG  TaskList: New task modify_bcd
03-22 05:18 DEBUG  TaskList: ## Finished modify_bootloader
03-22 05:18 DEBUG  TaskList: # Finished tasklist
03-22 05:19 INFO   root: === wubi 10.04.2 rev191 ===
03-22 05:19 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 05:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-22 05:19 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\data
03-22 05:19 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\bin\7z.exe
03-22 05:19 DEBUG  CommonBackend: Fetching basic info...
03-22 05:19 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 05:19 DEBUG  CommonBackend: platform=win32
03-22 05:19 DEBUG  CommonBackend: osname=nt
03-22 05:19 DEBUG  CommonBackend: language=en_US
03-22 05:19 DEBUG  CommonBackend: encoding=cp1252
03-22 05:19 DEBUG  WindowsBackend: arch=amd64
03-22 05:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\data\isolist.ini
03-22 05:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 05:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 05:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 05:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 05:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 05:19 DEBUG  WindowsBackend: Fetching host info...
03-22 05:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 05:19 DEBUG  WindowsBackend: windows version=vista
03-22 05:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 05:19 DEBUG  WindowsBackend: windows_sp=None
03-22 05:19 DEBUG  WindowsBackend: windows_build=7601
03-22 05:19 DEBUG  WindowsBackend: gmt=5
03-22 05:19 DEBUG  WindowsBackend: country=US
03-22 05:19 DEBUG  WindowsBackend: timezone=America/New_York
03-22 05:19 DEBUG  WindowsBackend: windows_username=Administrator
03-22 05:19 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 05:19 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 05:19 DEBUG  WindowsBackend: windows_language_code=1033
03-22 05:19 DEBUG  WindowsBackend: windows_language=English
03-22 05:19 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 05:19 DEBUG  WindowsBackend: bootloader=vista
03-22 05:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20486.6679688 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(C: hd 20486.6679688 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(E: hd 13169.09375 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(G: hd 9243.2421875 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 05:19 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 05:19 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 05:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 05:19 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 05:19 DEBUG  WindowsBackend: keyboard_layout=us
03-22 05:19 DEBUG  WindowsBackend: keyboard_variant=
03-22 05:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 05:19 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 05:19 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 05:19 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 05:19 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:19 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:19 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:19 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:19 DEBUG  CommonBackend: Searching for local CDs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:19 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 05:19 INFO   root: Running the CD menu...
03-22 05:19 DEBUG  WindowsFrontend: __init__...
03-22 05:19 DEBUG  WindowsFrontend: on_init...
03-22 05:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\translations, languages=['en_US', 'en']
03-22 05:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\translations, languages=['en_US', 'en']
03-22 05:19 INFO   root: CD menu finished
03-22 05:19 INFO   root: Already installed, running the uninstaller...
03-22 05:19 INFO   root: Running the uninstaller...
03-22 05:19 INFO   CommonBackend: This is the uninstaller running
03-22 05:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\translations, languages=['en_US', 'en']
03-22 05:19 INFO   root: Received settings
03-22 05:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\translations, languages=['en_US', 'en']
03-22 05:19 DEBUG  TaskList: # Running tasklist...
03-22 05:19 DEBUG  TaskList: ## Running Backup ISO...
03-22 05:19 DEBUG  TaskList: ## Finished Backup ISO
03-22 05:19 DEBUG  TaskList: ## Running Remove bootloader entry...
03-22 05:19 DEBUG  WindowsBackend: Could not find bcd id
03-22 05:19 DEBUG  WindowsBackend: undo_bootini C:
03-22 05:19 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 20486.6679688 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: undo_bootini D:
03-22 05:19 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: undo_bootini E:
03-22 05:19 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 13169.09375 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: undo_bootini G:
03-22 05:19 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 9243.2421875 mb free ntfs)
03-22 05:19 DEBUG  TaskList: ## Finished Remove bootloader entry
03-22 05:19 DEBUG  TaskList: ## Running Remove target dir...
03-22 05:19 DEBUG  CommonBackend: Deleting G:\ubuntu
03-22 05:19 DEBUG  TaskList: ## Finished Remove target dir
03-22 05:19 DEBUG  TaskList: ## Running Remove registry key...
03-22 05:19 DEBUG  TaskList: ## Finished Remove registry key
03-22 05:19 DEBUG  TaskList: # Finished tasklist
03-22 05:19 INFO   root: Almost finished uninstalling
03-22 05:19 INFO   root: Finished uninstallation
03-22 05:19 DEBUG  CommonBackend: Fetching basic info...
03-22 05:19 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 05:19 DEBUG  CommonBackend: platform=win32
03-22 05:19 DEBUG  CommonBackend: osname=nt
03-22 05:19 DEBUG  WindowsBackend: arch=amd64
03-22 05:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\data\isolist.ini
03-22 05:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 05:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 05:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 05:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 05:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 05:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 05:19 DEBUG  WindowsBackend: Fetching host info...
03-22 05:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 05:19 DEBUG  WindowsBackend: windows version=vista
03-22 05:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 05:19 DEBUG  WindowsBackend: windows_sp=None
03-22 05:19 DEBUG  WindowsBackend: windows_build=7601
03-22 05:19 DEBUG  WindowsBackend: gmt=5
03-22 05:19 DEBUG  WindowsBackend: country=US
03-22 05:19 DEBUG  WindowsBackend: timezone=America/New_York
03-22 05:19 DEBUG  WindowsBackend: windows_username=Administrator
03-22 05:19 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 05:19 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 05:19 DEBUG  WindowsBackend: windows_language_code=1033
03-22 05:19 DEBUG  WindowsBackend: windows_language=English
03-22 05:19 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 05:19 DEBUG  WindowsBackend: bootloader=vista
03-22 05:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20486.7304688 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(C: hd 20486.7304688 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(E: hd 13169.09375 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.8125 mb free ntfs)
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 05:19 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 05:19 DEBUG  WindowsBackend: uninstaller_path=None
03-22 05:19 DEBUG  WindowsBackend: previous_target_dir=None
03-22 05:19 DEBUG  WindowsBackend: previous_distro_name=None
03-22 05:19 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 05:19 DEBUG  WindowsBackend: keyboard_layout=us
03-22 05:19 DEBUG  WindowsBackend: keyboard_variant=
03-22 05:19 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 05:19 DEBUG  CommonBackend: Checking pre-specified ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:19 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:19 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:19 DEBUG  CommonBackend: Searching for local CDs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:19 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 05:19 INFO   root: Running the installer...
03-22 05:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\translations, languages=['en_US', 'en']
03-22 05:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl1A63.tmp\translations, languages=['en_US', 'en']
03-22 05:19 INFO   WindowsFrontend: Operation cancelled
03-22 05:19 DEBUG  WindowsFrontend: frontend.quit
03-22 05:19 DEBUG  WindowsFrontend: frontend.on_quit
03-22 05:19 DEBUG  root: application.on_quit
03-22 05:19 INFO   root: sys.exit
03-22 05:20 INFO   root: === wubi 10.04.2 rev191 ===
03-22 05:20 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 05:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-22 05:20 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\data
03-22 05:20 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\bin\7z.exe
03-22 05:20 DEBUG  CommonBackend: Fetching basic info...
03-22 05:20 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 05:20 DEBUG  CommonBackend: platform=win32
03-22 05:20 DEBUG  CommonBackend: osname=nt
03-22 05:20 DEBUG  CommonBackend: language=en_US
03-22 05:20 DEBUG  CommonBackend: encoding=cp1252
03-22 05:20 DEBUG  WindowsBackend: arch=amd64
03-22 05:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\data\isolist.ini
03-22 05:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 05:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 05:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 05:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 05:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 05:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 05:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 05:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 05:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 05:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 05:20 DEBUG  WindowsBackend: Fetching host info...
03-22 05:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 05:20 DEBUG  WindowsBackend: windows version=vista
03-22 05:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 05:20 DEBUG  WindowsBackend: windows_sp=None
03-22 05:20 DEBUG  WindowsBackend: windows_build=7601
03-22 05:20 DEBUG  WindowsBackend: gmt=5
03-22 05:20 DEBUG  WindowsBackend: country=US
03-22 05:20 DEBUG  WindowsBackend: timezone=America/New_York
03-22 05:20 DEBUG  WindowsBackend: windows_username=Administrator
03-22 05:20 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 05:20 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 05:20 DEBUG  WindowsBackend: windows_language_code=1033
03-22 05:20 DEBUG  WindowsBackend: windows_language=English
03-22 05:20 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 05:20 DEBUG  WindowsBackend: bootloader=vista
03-22 05:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20486.2109375 mb free ntfs)
03-22 05:20 DEBUG  WindowsBackend: drive=Drive(C: hd 20486.2109375 mb free ntfs)
03-22 05:20 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:20 DEBUG  WindowsBackend: drive=Drive(E: hd 18191.9414063 mb free ntfs)
03-22 05:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 05:20 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.81640625 mb free ntfs)
03-22 05:20 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 05:20 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 05:20 DEBUG  WindowsBackend: uninstaller_path=None
03-22 05:20 DEBUG  WindowsBackend: previous_target_dir=None
03-22 05:20 DEBUG  WindowsBackend: previous_distro_name=None
03-22 05:20 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 05:20 DEBUG  WindowsBackend: keyboard_layout=us
03-22 05:20 DEBUG  WindowsBackend: keyboard_variant=
03-22 05:20 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 05:20 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 05:20 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 05:20 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 05:20 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:20 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 DEBUG  CommonBackend: Searching for local CDs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Ubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Kubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:20 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:20 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 05:20 INFO   root: Running the CD menu...
03-22 05:20 DEBUG  WindowsFrontend: __init__...
03-22 05:20 DEBUG  WindowsFrontend: on_init...
03-22 05:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\translations, languages=['en_US', 'en']
03-22 05:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\translations, languages=['en_US', 'en']
03-22 05:20 INFO   root: CD menu finished
03-22 05:20 INFO   root: Running the installer...
03-22 05:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\translations, languages=['en_US', 'en']
03-22 05:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\translations, languages=['en_US', 'en']
03-22 05:20 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-22 05:20 INFO   root: Received settings
03-22 05:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\translations, languages=['en_US', 'en']
03-22 05:20 DEBUG  TaskList: # Running tasklist...
03-22 05:20 DEBUG  TaskList: ## Running select_target_dir...
03-22 05:20 INFO   WindowsBackend: Installing into G:\ubuntu
03-22 05:20 DEBUG  TaskList: ## Finished select_target_dir
03-22 05:20 DEBUG  TaskList: ## Running create_dir_structure...
03-22 05:20 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-22 05:20 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-22 05:20 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-22 05:20 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-22 05:20 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-22 05:20 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-22 05:20 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-22 05:20 DEBUG  TaskList: ## Finished create_dir_structure
03-22 05:20 DEBUG  TaskList: ## Running uncompress_target_dir...
03-22 05:20 DEBUG  TaskList: ## Finished uncompress_target_dir
03-22 05:20 DEBUG  TaskList: ## Running create_uninstaller...
03-22 05:20 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-22 05:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-22 05:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-22 05:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-22 05:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-22 05:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
03-22 05:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-22 05:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-22 05:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-22 05:20 DEBUG  TaskList: ## Finished create_uninstaller
03-22 05:20 DEBUG  TaskList: ## Running copy_installation_files...
03-22 05:20 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-22 05:20 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\winboot -> G:\ubuntu\winboot
03-22 05:20 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl5ADC.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-22 05:20 DEBUG  TaskList: ## Finished copy_installation_files
03-22 05:20 DEBUG  TaskList: ## Running get_iso...
03-22 05:20 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 DEBUG  TaskList: New task is_valid_iso
03-22 05:20 DEBUG  TaskList: ### Running is_valid_iso...
03-22 05:20 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 DEBUG  TaskList: ### Finished is_valid_iso
03-22 05:20 DEBUG  TaskList: New task check_iso
03-22 05:20 DEBUG  TaskList: ### Running check_iso...
03-22 05:20 DEBUG  CommonBackend: Checking E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:20 DEBUG  TaskList: New task get_metalink
03-22 05:20 DEBUG  TaskList: #### Running get_metalink...
03-22 05:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > G:\ubuntu\install
03-22 05:20 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
03-22 05:20 DEBUG  downloader: download finished (read 39020 bytes)
03-22 05:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > G:\ubuntu\install
03-22 05:20 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
03-22 05:20 DEBUG  downloader: download finished (read 651 bytes)
03-22 05:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > G:\ubuntu\install
03-22 05:20 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-22 05:20 DEBUG  downloader: download finished (read 198 bytes)
03-22 05:20 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-22 05:20 INFO   saplog: Checking block bindings..
03-22 05:20 INFO   saplog: Key verified successfully.
03-22 05:20 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink
03-22 05:20 DEBUG  TaskList: #### Finished get_metalink
03-22 05:20 DEBUG  TaskList: New task get_file_md5
03-22 05:20 DEBUG  TaskList: #### Running get_file_md5...
03-22 05:20 DEBUG  TaskList: #### Finished get_file_md5
03-22 05:20 DEBUG  TaskList: ### Finished check_iso
03-22 05:20 DEBUG  TaskList: New task copy_file
03-22 05:20 DEBUG  CommonBackend: Copying E:\ubuntu-10.04.2-desktop-amd64.iso > G:\ubuntu\install\installation.iso
03-22 05:20 DEBUG  TaskList: ### Running copy_file...
03-22 05:21 DEBUG  TaskList: ### Finished copy_file
03-22 05:21 DEBUG  TaskList: ## Finished get_iso
03-22 05:21 DEBUG  TaskList: ## Running extract_kernel...
03-22 05:21 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
03-22 05:21 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
03-22 05:21 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
03-22 05:21 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
03-22 05:21 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-22 05:21 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-22 05:21 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 41d2d275b0aed279030980587f6de7e9 == 41d2d275b0aed279030980587f6de7e9
03-22 05:21 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-22 05:21 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 774fcb24611ab59898b1e51df6cfd8d6 == 774fcb24611ab59898b1e51df6cfd8d6
03-22 05:21 DEBUG  TaskList: ## Finished extract_kernel
03-22 05:21 DEBUG  TaskList: ## Running choose_disk_sizes...
03-22 05:21 DEBUG  WindowsBackend: total size=6000
  root=5744
  swap=256
  home=0
  usr=0
03-22 05:21 DEBUG  TaskList: ## Finished choose_disk_sizes
03-22 05:21 DEBUG  TaskList: ## Running create_preseed...
03-22 05:21 DEBUG  TaskList: ## Finished create_preseed
03-22 05:21 DEBUG  TaskList: ## Running modify_bootloader...
03-22 05:21 DEBUG  TaskList: New task modify_bcd
03-22 05:21 DEBUG  TaskList: ### Running modify_bcd...
03-22 05:21 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 20486.2109375 mb free ntfs)
03-22 05:21 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437d-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437d-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 05:21 DEBUG  TaskList: # Cancelling tasklist
03-22 05:21 DEBUG  TaskList: New task modify_bcd
03-22 05:21 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437d-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437d-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 05:21 DEBUG  TaskList: New task modify_bcd
03-22 05:21 DEBUG  TaskList: New task modify_bcd
03-22 05:21 DEBUG  TaskList: ## Finished modify_bootloader
03-22 05:21 DEBUG  TaskList: # Finished tasklist
03-22 05:33 INFO   root: === wubi 10.04.2 rev191 ===
03-22 05:33 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 05:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
03-22 05:33 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\data
03-22 05:33 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\bin\7z.exe
03-22 05:33 DEBUG  CommonBackend: Fetching basic info...
03-22 05:33 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
03-22 05:33 DEBUG  CommonBackend: platform=win32
03-22 05:33 DEBUG  CommonBackend: osname=nt
03-22 05:33 DEBUG  CommonBackend: language=en_US
03-22 05:33 DEBUG  CommonBackend: encoding=cp1252
03-22 05:33 DEBUG  WindowsBackend: arch=amd64
03-22 05:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\data\isolist.ini
03-22 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 05:33 DEBUG  WindowsBackend: Fetching host info...
03-22 05:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 05:33 DEBUG  WindowsBackend: windows version=vista
03-22 05:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 05:33 DEBUG  WindowsBackend: windows_sp=None
03-22 05:33 DEBUG  WindowsBackend: windows_build=7601
03-22 05:33 DEBUG  WindowsBackend: gmt=5
03-22 05:33 DEBUG  WindowsBackend: country=US
03-22 05:33 DEBUG  WindowsBackend: timezone=America/New_York
03-22 05:33 DEBUG  WindowsBackend: windows_username=Administrator
03-22 05:33 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 05:33 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 05:33 DEBUG  WindowsBackend: windows_language_code=1033
03-22 05:33 DEBUG  WindowsBackend: windows_language=English
03-22 05:33 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 05:33 DEBUG  WindowsBackend: bootloader=vista
03-22 05:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20463.7421875 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(C: hd 20463.7421875 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(E: hd 18190.5039063 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(G: hd 9243.2421875 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 05:33 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 05:33 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 05:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 05:33 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 05:33 DEBUG  WindowsBackend: keyboard_layout=us
03-22 05:33 DEBUG  WindowsBackend: keyboard_variant=
03-22 05:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 05:33 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 05:33 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 05:33 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 05:33 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:33 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  CommonBackend: Searching for local CDs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:33 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 05:33 INFO   root: Running the uninstaller...
03-22 05:33 INFO   CommonBackend: This is the uninstaller running
03-22 05:33 DEBUG  WindowsFrontend: __init__...
03-22 05:33 DEBUG  WindowsFrontend: on_init...
03-22 05:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\translations, languages=['en_US', 'en']
03-22 05:33 INFO   root: Received settings
03-22 05:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\translations, languages=['en_US', 'en']
03-22 05:33 DEBUG  TaskList: # Running tasklist...
03-22 05:33 DEBUG  TaskList: ## Running Backup ISO...
03-22 05:33 DEBUG  TaskList: ## Finished Backup ISO
03-22 05:33 DEBUG  TaskList: ## Running Remove bootloader entry...
03-22 05:33 DEBUG  WindowsBackend: Could not find bcd id
03-22 05:33 DEBUG  WindowsBackend: undo_bootini C:
03-22 05:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 20463.7421875 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: undo_bootini D:
03-22 05:33 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: undo_bootini E:
03-22 05:33 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 18190.5039063 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: undo_bootini G:
03-22 05:33 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 9243.2421875 mb free ntfs)
03-22 05:33 DEBUG  TaskList: ## Finished Remove bootloader entry
03-22 05:33 DEBUG  TaskList: ## Running Remove target dir...
03-22 05:33 DEBUG  CommonBackend: Deleting G:\ubuntu
03-22 05:33 DEBUG  TaskList: ## Finished Remove target dir
03-22 05:33 DEBUG  TaskList: ## Running Remove registry key...
03-22 05:33 DEBUG  TaskList: ## Finished Remove registry key
03-22 05:33 DEBUG  TaskList: # Finished tasklist
03-22 05:33 INFO   root: Almost finished uninstalling
03-22 05:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl275E.tmp\translations, languages=['en_US', 'en']
03-22 05:33 INFO   root: Finished uninstallation
03-22 05:33 DEBUG  root: application.quit
03-22 05:33 DEBUG  WindowsFrontend: frontend.quit
03-22 05:33 DEBUG  WindowsFrontend: frontend.on_quit
03-22 05:33 DEBUG  root: application.on_quit
03-22 05:33 INFO   root: sys.exit
03-22 12:25 INFO   root: === wubi 10.04.2 rev191 ===
03-22 12:25 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 12:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-22 12:25 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\data
03-22 12:25 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\bin\7z.exe
03-22 12:25 DEBUG  CommonBackend: Fetching basic info...
03-22 12:25 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 12:25 DEBUG  CommonBackend: platform=win32
03-22 12:25 DEBUG  CommonBackend: osname=nt
03-22 12:25 DEBUG  CommonBackend: language=en_US
03-22 12:25 DEBUG  CommonBackend: encoding=cp1252
03-22 12:25 DEBUG  WindowsBackend: arch=amd64
03-22 12:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\data\isolist.ini
03-22 12:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 12:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 12:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 12:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 12:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 12:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 12:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 12:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 12:25 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 12:25 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 12:25 DEBUG  WindowsBackend: Fetching host info...
03-22 12:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 12:25 DEBUG  WindowsBackend: windows version=vista
03-22 12:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 12:25 DEBUG  WindowsBackend: windows_sp=None
03-22 12:25 DEBUG  WindowsBackend: windows_build=7601
03-22 12:25 DEBUG  WindowsBackend: gmt=5
03-22 12:25 DEBUG  WindowsBackend: country=US
03-22 12:25 DEBUG  WindowsBackend: timezone=America/New_York
03-22 12:25 DEBUG  WindowsBackend: windows_username=Administrator
03-22 12:25 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 12:25 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 12:25 DEBUG  WindowsBackend: windows_language_code=1033
03-22 12:25 DEBUG  WindowsBackend: windows_language=English
03-22 12:25 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 12:25 DEBUG  WindowsBackend: bootloader=vista
03-22 12:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20670.0507813 mb free ntfs)
03-22 12:25 DEBUG  WindowsBackend: drive=Drive(C: hd 20670.0507813 mb free ntfs)
03-22 12:25 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 12:25 DEBUG  WindowsBackend: drive=Drive(E: hd 18191.9375 mb free ntfs)
03-22 12:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 12:25 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.81640625 mb free ntfs)
03-22 12:25 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 12:25 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 12:25 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 12:25 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 12:25 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 12:25 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 12:25 DEBUG  WindowsBackend: keyboard_layout=us
03-22 12:25 DEBUG  WindowsBackend: keyboard_variant=
03-22 12:25 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 12:25 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 12:25 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 12:25 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 12:25 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 12:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 12:25 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 DEBUG  CommonBackend: Searching for local CDs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Ubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Kubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 12:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:25 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 12:25 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 12:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 12:25 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 12:25 INFO   root: Running the CD menu...
03-22 12:25 DEBUG  WindowsFrontend: __init__...
03-22 12:25 DEBUG  WindowsFrontend: on_init...
03-22 12:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\translations, languages=['en_US', 'en']
03-22 12:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\translations, languages=['en_US', 'en']
03-22 12:25 INFO   root: CD menu finished
03-22 12:25 INFO   root: Running the installer...
03-22 12:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\translations, languages=['en_US', 'en']
03-22 12:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\translations, languages=['en_US', 'en']
03-22 12:25 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-22 12:25 INFO   root: Received settings
03-22 12:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\translations, languages=['en_US', 'en']
03-22 12:25 DEBUG  TaskList: # Running tasklist...
03-22 12:25 DEBUG  TaskList: ## Running select_target_dir...
03-22 12:25 INFO   WindowsBackend: Installing into G:\ubuntu
03-22 12:25 DEBUG  TaskList: ## Finished select_target_dir
03-22 12:25 DEBUG  TaskList: ## Running create_dir_structure...
03-22 12:25 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-22 12:25 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-22 12:25 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-22 12:25 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-22 12:25 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-22 12:25 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-22 12:25 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-22 12:25 DEBUG  TaskList: ## Finished create_dir_structure
03-22 12:25 DEBUG  TaskList: ## Running uncompress_target_dir...
03-22 12:25 DEBUG  TaskList: ## Finished uncompress_target_dir
03-22 12:25 DEBUG  TaskList: ## Running create_uninstaller...
03-22 12:25 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-22 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-22 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-22 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-22 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-22 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
03-22 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-22 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-22 12:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-22 12:25 DEBUG  TaskList: ## Finished create_uninstaller
03-22 12:25 DEBUG  TaskList: ## Running copy_installation_files...
03-22 12:25 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-22 12:25 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\winboot -> G:\ubuntu\winboot
03-22 12:25 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl9D09.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-22 12:25 DEBUG  TaskList: ## Finished copy_installation_files
03-22 12:25 DEBUG  TaskList: ## Running get_iso...
03-22 12:25 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 DEBUG  TaskList: New task is_valid_iso
03-22 12:25 DEBUG  TaskList: ### Running is_valid_iso...
03-22 12:25 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 DEBUG  TaskList: ### Finished is_valid_iso
03-22 12:25 DEBUG  TaskList: New task check_iso
03-22 12:25 DEBUG  TaskList: ### Running check_iso...
03-22 12:25 DEBUG  CommonBackend: Checking E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:25 DEBUG  TaskList: New task get_metalink
03-22 12:25 DEBUG  TaskList: #### Running get_metalink...
03-22 12:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > G:\ubuntu\install
03-22 12:25 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
03-22 12:25 DEBUG  downloader: download finished (read 39020 bytes)
03-22 12:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > G:\ubuntu\install
03-22 12:25 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
03-22 12:25 DEBUG  downloader: download finished (read 651 bytes)
03-22 12:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > G:\ubuntu\install
03-22 12:25 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-22 12:25 DEBUG  downloader: download finished (read 198 bytes)
03-22 12:25 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-22 12:25 INFO   saplog: Checking block bindings..
03-22 12:25 INFO   saplog: Key verified successfully.
03-22 12:25 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink
03-22 12:25 DEBUG  TaskList: #### Finished get_metalink
03-22 12:25 DEBUG  TaskList: New task get_file_md5
03-22 12:25 DEBUG  TaskList: #### Running get_file_md5...
03-22 12:25 DEBUG  TaskList: #### Finished get_file_md5
03-22 12:25 DEBUG  TaskList: ### Finished check_iso
03-22 12:25 DEBUG  TaskList: New task copy_file
03-22 12:25 DEBUG  CommonBackend: Copying E:\ubuntu-10.04.2-desktop-amd64.iso > G:\ubuntu\install\installation.iso
03-22 12:25 DEBUG  TaskList: ### Running copy_file...
03-22 12:26 DEBUG  TaskList: ### Finished copy_file
03-22 12:26 DEBUG  TaskList: ## Finished get_iso
03-22 12:26 DEBUG  TaskList: ## Running extract_kernel...
03-22 12:26 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
03-22 12:26 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
03-22 12:26 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
03-22 12:26 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
03-22 12:26 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-22 12:26 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-22 12:26 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 41d2d275b0aed279030980587f6de7e9 == 41d2d275b0aed279030980587f6de7e9
03-22 12:26 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-22 12:26 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 774fcb24611ab59898b1e51df6cfd8d6 == 774fcb24611ab59898b1e51df6cfd8d6
03-22 12:26 DEBUG  TaskList: ## Finished extract_kernel
03-22 12:26 DEBUG  TaskList: ## Running choose_disk_sizes...
03-22 12:26 DEBUG  WindowsBackend: total size=6000
  root=5744
  swap=256
  home=0
  usr=0
03-22 12:26 DEBUG  TaskList: ## Finished choose_disk_sizes
03-22 12:26 DEBUG  TaskList: ## Running create_preseed...
03-22 12:26 DEBUG  TaskList: ## Finished create_preseed
03-22 12:26 DEBUG  TaskList: ## Running modify_bootloader...
03-22 12:26 DEBUG  TaskList: New task modify_bcd
03-22 12:26 DEBUG  TaskList: ### Running modify_bcd...
03-22 12:26 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 20670.0507813 mb free ntfs)
03-22 12:26 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437e-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437e-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 12:26 DEBUG  TaskList: # Cancelling tasklist
03-22 12:26 DEBUG  TaskList: New task modify_bcd
03-22 12:26 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437e-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437e-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 12:26 DEBUG  TaskList: New task modify_bcd
03-22 12:26 DEBUG  TaskList: New task modify_bcd
03-22 12:26 DEBUG  TaskList: ## Finished modify_bootloader
03-22 12:26 DEBUG  TaskList: # Finished tasklist
03-22 12:26 INFO   root: === wubi 10.04.2 rev191 ===
03-22 12:26 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 12:26 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-22 12:26 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\data
03-22 12:26 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\bin\7z.exe
03-22 12:26 DEBUG  CommonBackend: Fetching basic info...
03-22 12:26 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 12:26 DEBUG  CommonBackend: platform=win32
03-22 12:26 DEBUG  CommonBackend: osname=nt
03-22 12:26 DEBUG  CommonBackend: language=en_US
03-22 12:26 DEBUG  CommonBackend: encoding=cp1252
03-22 12:26 DEBUG  WindowsBackend: arch=amd64
03-22 12:26 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\data\isolist.ini
03-22 12:26 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 12:26 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 12:26 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 12:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 12:26 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 12:26 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 12:26 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 12:26 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 12:26 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 12:26 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 12:26 DEBUG  WindowsBackend: Fetching host info...
03-22 12:26 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 12:26 DEBUG  WindowsBackend: windows version=vista
03-22 12:26 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 12:26 DEBUG  WindowsBackend: windows_sp=None
03-22 12:26 DEBUG  WindowsBackend: windows_build=7601
03-22 12:26 DEBUG  WindowsBackend: gmt=5
03-22 12:26 DEBUG  WindowsBackend: country=US
03-22 12:26 DEBUG  WindowsBackend: timezone=America/New_York
03-22 12:26 DEBUG  WindowsBackend: windows_username=Administrator
03-22 12:26 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 12:26 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 12:26 DEBUG  WindowsBackend: windows_language_code=1033
03-22 12:26 DEBUG  WindowsBackend: windows_language=English
03-22 12:26 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 12:26 DEBUG  WindowsBackend: bootloader=vista
03-22 12:26 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20669.5273438 mb free ntfs)
03-22 12:26 DEBUG  WindowsBackend: drive=Drive(C: hd 20669.5273438 mb free ntfs)
03-22 12:26 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 12:26 DEBUG  WindowsBackend: drive=Drive(E: hd 18191.9375 mb free ntfs)
03-22 12:26 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 12:26 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.81640625 mb free ntfs)
03-22 12:26 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 12:26 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 12:26 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 12:26 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 12:26 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 12:26 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 12:26 DEBUG  WindowsBackend: keyboard_layout=us
03-22 12:26 DEBUG  WindowsBackend: keyboard_variant=
03-22 12:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 12:26 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 12:26 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 12:26 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 12:26 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:26 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:26 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 12:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 12:26 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:26 DEBUG  CommonBackend: Searching for local CDs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Ubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Kubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 12:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 12:26 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 12:26 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 12:26 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 12:26 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 12:26 INFO   root: Running the CD menu...
03-22 12:26 DEBUG  WindowsFrontend: __init__...
03-22 12:26 DEBUG  WindowsFrontend: on_init...
03-22 12:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\translations, languages=['en_US', 'en']
03-22 12:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\translations, languages=['en_US', 'en']
03-22 12:26 INFO   root: CD menu finished
03-22 12:26 INFO   root: Running the installer...
03-22 12:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\translations, languages=['en_US', 'en']
03-22 12:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\translations, languages=['en_US', 'en']
03-22 12:27 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-22 12:27 INFO   root: Received settings
03-22 12:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\translations, languages=['en_US', 'en']
03-22 12:27 DEBUG  TaskList: # Running tasklist...
03-22 12:27 DEBUG  TaskList: ## Running select_target_dir...
03-22 12:27 INFO   WindowsBackend: Installing into G:\ubuntu
03-22 12:27 DEBUG  TaskList: ## Finished select_target_dir
03-22 12:27 DEBUG  TaskList: ## Running create_dir_structure...
03-22 12:27 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-22 12:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-22 12:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-22 12:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-22 12:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-22 12:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-22 12:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-22 12:27 DEBUG  TaskList: ## Finished create_dir_structure
03-22 12:27 DEBUG  TaskList: ## Running uncompress_target_dir...
03-22 12:27 DEBUG  TaskList: ## Finished uncompress_target_dir
03-22 12:27 DEBUG  TaskList: ## Running create_uninstaller...
03-22 12:27 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-22 12:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-22 12:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-22 12:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-22 12:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-22 12:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
03-22 12:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-22 12:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-22 12:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-22 12:27 DEBUG  TaskList: ## Finished create_uninstaller
03-22 12:27 DEBUG  TaskList: ## Running copy_installation_files...
03-22 12:27 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-22 12:27 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\winboot -> G:\ubuntu\winboot
03-22 12:27 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylBC7B.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-22 12:27 DEBUG  TaskList: ## Finished copy_installation_files
03-22 12:27 DEBUG  TaskList: ## Running get_iso...
03-22 12:27 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:27 DEBUG  TaskList: New task is_valid_iso
03-22 12:27 DEBUG  TaskList: ### Running is_valid_iso...
03-22 12:27 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:27 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:27 DEBUG  TaskList: ### Finished is_valid_iso
03-22 12:27 DEBUG  TaskList: New task check_iso
03-22 12:27 DEBUG  TaskList: ### Running check_iso...
03-22 12:27 DEBUG  CommonBackend: Checking E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:27 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:27 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 12:27 DEBUG  TaskList: New task get_metalink
03-22 12:27 DEBUG  TaskList: #### Running get_metalink...
03-22 12:27 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > G:\ubuntu\install
03-22 12:27 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
03-22 12:27 DEBUG  downloader: download finished (read 39020 bytes)
03-22 12:27 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > G:\ubuntu\install
03-22 12:27 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
03-22 12:27 DEBUG  downloader: download finished (read 651 bytes)
03-22 12:27 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > G:\ubuntu\install
03-22 12:27 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-22 12:27 DEBUG  downloader: download finished (read 198 bytes)
03-22 12:27 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-22 12:27 INFO   saplog: Checking block bindings..
03-22 12:27 INFO   saplog: Key verified successfully.
03-22 12:27 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink
03-22 12:27 DEBUG  TaskList: #### Finished get_metalink
03-22 12:27 DEBUG  TaskList: New task get_file_md5
03-22 12:27 DEBUG  TaskList: #### Running get_file_md5...
03-22 12:27 DEBUG  TaskList: #### Finished get_file_md5
03-22 12:27 DEBUG  TaskList: ### Finished check_iso
03-22 12:27 DEBUG  TaskList: New task copy_file
03-22 12:27 DEBUG  CommonBackend: Copying E:\ubuntu-10.04.2-desktop-amd64.iso > G:\ubuntu\install\installation.iso
03-22 12:27 DEBUG  TaskList: ### Running copy_file...
03-22 12:27 DEBUG  TaskList: ### Finished copy_file
03-22 12:27 DEBUG  TaskList: ## Finished get_iso
03-22 12:27 DEBUG  TaskList: ## Running extract_kernel...
03-22 12:27 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
03-22 12:27 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
03-22 12:27 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
03-22 12:27 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
03-22 12:27 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-22 12:27 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-22 12:27 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 41d2d275b0aed279030980587f6de7e9 == 41d2d275b0aed279030980587f6de7e9
03-22 12:27 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-22 12:27 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 774fcb24611ab59898b1e51df6cfd8d6 == 774fcb24611ab59898b1e51df6cfd8d6
03-22 12:27 DEBUG  TaskList: ## Finished extract_kernel
03-22 12:27 DEBUG  TaskList: ## Running choose_disk_sizes...
03-22 12:27 DEBUG  WindowsBackend: total size=6000
  root=5744
  swap=256
  home=0
  usr=0
03-22 12:27 DEBUG  TaskList: ## Finished choose_disk_sizes
03-22 12:27 DEBUG  TaskList: ## Running create_preseed...
03-22 12:27 DEBUG  TaskList: ## Finished create_preseed
03-22 12:27 DEBUG  TaskList: ## Running modify_bootloader...
03-22 12:27 DEBUG  TaskList: New task modify_bcd
03-22 12:27 DEBUG  TaskList: ### Running modify_bcd...
03-22 12:27 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 20669.5273438 mb free ntfs)
03-22 12:27 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437f-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437f-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 12:27 DEBUG  TaskList: # Cancelling tasklist
03-22 12:27 DEBUG  TaskList: New task modify_bcd
03-22 12:27 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437f-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e8437f-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 12:27 DEBUG  TaskList: New task modify_bcd
03-22 12:27 DEBUG  TaskList: New task modify_bcd
03-22 12:27 DEBUG  TaskList: ## Finished modify_bootloader
03-22 12:27 DEBUG  TaskList: # Finished tasklist
03-22 17:41 INFO   root: === wubi 10.04.2 rev191 ===
03-22 17:41 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 17:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-22 17:41 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\data
03-22 17:41 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\bin\7z.exe
03-22 17:41 DEBUG  CommonBackend: Fetching basic info...
03-22 17:41 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 17:41 DEBUG  CommonBackend: platform=win32
03-22 17:41 DEBUG  CommonBackend: osname=nt
03-22 17:41 DEBUG  CommonBackend: language=en_US
03-22 17:41 DEBUG  CommonBackend: encoding=cp1252
03-22 17:41 DEBUG  WindowsBackend: arch=amd64
03-22 17:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\data\isolist.ini
03-22 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 17:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 17:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 17:41 DEBUG  WindowsBackend: Fetching host info...
03-22 17:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 17:41 DEBUG  WindowsBackend: windows version=vista
03-22 17:41 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 17:41 DEBUG  WindowsBackend: windows_sp=None
03-22 17:41 DEBUG  WindowsBackend: windows_build=7601
03-22 17:41 DEBUG  WindowsBackend: gmt=5
03-22 17:41 DEBUG  WindowsBackend: country=US
03-22 17:41 DEBUG  WindowsBackend: timezone=America/New_York
03-22 17:41 DEBUG  WindowsBackend: windows_username=Administrator
03-22 17:41 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 17:41 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 17:41 DEBUG  WindowsBackend: windows_language_code=1033
03-22 17:41 DEBUG  WindowsBackend: windows_language=English
03-22 17:41 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 17:41 DEBUG  WindowsBackend: bootloader=vista
03-22 17:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20632.7539063 mb free ntfs)
03-22 17:41 DEBUG  WindowsBackend: drive=Drive(C: hd 20632.7539063 mb free ntfs)
03-22 17:41 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 17:41 DEBUG  WindowsBackend: drive=Drive(E: hd 18186.1015625 mb free ntfs)
03-22 17:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 17:41 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.8125 mb free ntfs)
03-22 17:41 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 17:41 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 17:41 DEBUG  WindowsBackend: drive=Drive(J: removable 3099.33984375 mb free fat32)
03-22 17:41 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 17:41 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 17:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 17:41 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 17:41 DEBUG  WindowsBackend: keyboard_layout=us
03-22 17:41 DEBUG  WindowsBackend: keyboard_variant=
03-22 17:41 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 17:41 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 17:41 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 17:41 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 17:41 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 17:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 17:41 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 DEBUG  CommonBackend: Searching for local CDs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Ubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Kubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 17:41 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:41 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 17:41 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 17:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 17:41 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 17:41 INFO   root: Running the CD menu...
03-22 17:41 DEBUG  WindowsFrontend: __init__...
03-22 17:41 DEBUG  WindowsFrontend: on_init...
03-22 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\translations, languages=['en_US', 'en']
03-22 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\translations, languages=['en_US', 'en']
03-22 17:41 INFO   root: CD menu finished
03-22 17:41 INFO   root: Running the installer...
03-22 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\translations, languages=['en_US', 'en']
03-22 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\translations, languages=['en_US', 'en']
03-22 17:41 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-22 17:41 INFO   root: Received settings
03-22 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\translations, languages=['en_US', 'en']
03-22 17:41 DEBUG  TaskList: # Running tasklist...
03-22 17:41 DEBUG  TaskList: ## Running select_target_dir...
03-22 17:41 INFO   WindowsBackend: Installing into G:\ubuntu
03-22 17:41 DEBUG  TaskList: ## Finished select_target_dir
03-22 17:41 DEBUG  TaskList: ## Running create_dir_structure...
03-22 17:41 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-22 17:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-22 17:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-22 17:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-22 17:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-22 17:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-22 17:41 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-22 17:41 DEBUG  TaskList: ## Finished create_dir_structure
03-22 17:41 DEBUG  TaskList: ## Running uncompress_target_dir...
03-22 17:41 DEBUG  TaskList: ## Finished uncompress_target_dir
03-22 17:41 DEBUG  TaskList: ## Running create_uninstaller...
03-22 17:41 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-22 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-22 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-22 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-22 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-22 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
03-22 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-22 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-22 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-22 17:41 DEBUG  TaskList: ## Finished create_uninstaller
03-22 17:41 DEBUG  TaskList: ## Running copy_installation_files...
03-22 17:41 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-22 17:41 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\winboot -> G:\ubuntu\winboot
03-22 17:41 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl83CF.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-22 17:41 DEBUG  TaskList: ## Finished copy_installation_files
03-22 17:41 DEBUG  TaskList: ## Running get_iso...
03-22 17:41 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 DEBUG  TaskList: New task is_valid_iso
03-22 17:41 DEBUG  TaskList: ### Running is_valid_iso...
03-22 17:41 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 DEBUG  TaskList: ### Finished is_valid_iso
03-22 17:41 DEBUG  TaskList: New task check_iso
03-22 17:41 DEBUG  TaskList: ### Running check_iso...
03-22 17:41 DEBUG  CommonBackend: Checking E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:41 DEBUG  TaskList: New task get_metalink
03-22 17:41 DEBUG  TaskList: #### Running get_metalink...
03-22 17:41 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > G:\ubuntu\install
03-22 17:41 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
03-22 17:41 DEBUG  downloader: download finished (read 39020 bytes)
03-22 17:41 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > G:\ubuntu\install
03-22 17:41 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
03-22 17:41 DEBUG  downloader: download finished (read 651 bytes)
03-22 17:41 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > G:\ubuntu\install
03-22 17:41 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-22 17:41 DEBUG  downloader: download finished (read 198 bytes)
03-22 17:41 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-22 17:41 INFO   saplog: Checking block bindings..
03-22 17:41 INFO   saplog: Key verified successfully.
03-22 17:41 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink
03-22 17:41 DEBUG  TaskList: #### Finished get_metalink
03-22 17:41 DEBUG  TaskList: New task get_file_md5
03-22 17:41 DEBUG  TaskList: #### Running get_file_md5...
03-22 17:41 DEBUG  TaskList: #### Finished get_file_md5
03-22 17:41 DEBUG  TaskList: ### Finished check_iso
03-22 17:41 DEBUG  TaskList: New task copy_file
03-22 17:41 DEBUG  CommonBackend: Copying E:\ubuntu-10.04.2-desktop-amd64.iso > G:\ubuntu\install\installation.iso
03-22 17:41 DEBUG  TaskList: ### Running copy_file...
03-22 17:42 DEBUG  TaskList: ### Finished copy_file
03-22 17:42 DEBUG  TaskList: ## Finished get_iso
03-22 17:42 DEBUG  TaskList: ## Running extract_kernel...
03-22 17:42 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
03-22 17:42 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
03-22 17:42 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
03-22 17:42 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
03-22 17:42 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-22 17:42 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-22 17:42 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 41d2d275b0aed279030980587f6de7e9 == 41d2d275b0aed279030980587f6de7e9
03-22 17:42 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-22 17:42 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 774fcb24611ab59898b1e51df6cfd8d6 == 774fcb24611ab59898b1e51df6cfd8d6
03-22 17:42 DEBUG  TaskList: ## Finished extract_kernel
03-22 17:42 DEBUG  TaskList: ## Running choose_disk_sizes...
03-22 17:42 DEBUG  WindowsBackend: total size=6000
  root=5744
  swap=256
  home=0
  usr=0
03-22 17:42 DEBUG  TaskList: ## Finished choose_disk_sizes
03-22 17:42 DEBUG  TaskList: ## Running create_preseed...
03-22 17:42 DEBUG  TaskList: ## Finished create_preseed
03-22 17:42 DEBUG  TaskList: ## Running modify_bootloader...
03-22 17:42 DEBUG  TaskList: New task modify_bcd
03-22 17:42 DEBUG  TaskList: ### Running modify_bcd...
03-22 17:42 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 20632.7539063 mb free ntfs)
03-22 17:42 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84380-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84380-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 17:42 DEBUG  TaskList: # Cancelling tasklist
03-22 17:42 DEBUG  TaskList: New task modify_bcd
03-22 17:42 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84380-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84380-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 17:42 DEBUG  TaskList: New task modify_bcd
03-22 17:42 DEBUG  TaskList: New task modify_bcd
03-22 17:42 DEBUG  TaskList: New task modify_bcd
03-22 17:42 DEBUG  TaskList: ## Finished modify_bootloader
03-22 17:42 DEBUG  TaskList: # Finished tasklist
03-22 17:42 INFO   root: === wubi 10.04.2 rev191 ===
03-22 17:42 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 17:42 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-22 17:42 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\data
03-22 17:42 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\bin\7z.exe
03-22 17:42 DEBUG  CommonBackend: Fetching basic info...
03-22 17:42 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 17:42 DEBUG  CommonBackend: platform=win32
03-22 17:42 DEBUG  CommonBackend: osname=nt
03-22 17:42 DEBUG  CommonBackend: language=en_US
03-22 17:42 DEBUG  CommonBackend: encoding=cp1252
03-22 17:42 DEBUG  WindowsBackend: arch=amd64
03-22 17:42 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\data\isolist.ini
03-22 17:42 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 17:42 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 17:42 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 17:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 17:42 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 17:42 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 17:42 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 17:42 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 17:42 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 17:42 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 17:42 DEBUG  WindowsBackend: Fetching host info...
03-22 17:42 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 17:42 DEBUG  WindowsBackend: windows version=vista
03-22 17:42 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 17:42 DEBUG  WindowsBackend: windows_sp=None
03-22 17:42 DEBUG  WindowsBackend: windows_build=7601
03-22 17:42 DEBUG  WindowsBackend: gmt=5
03-22 17:42 DEBUG  WindowsBackend: country=US
03-22 17:42 DEBUG  WindowsBackend: timezone=America/New_York
03-22 17:42 DEBUG  WindowsBackend: windows_username=Administrator
03-22 17:42 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 17:42 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 17:42 DEBUG  WindowsBackend: windows_language_code=1033
03-22 17:42 DEBUG  WindowsBackend: windows_language=English
03-22 17:42 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 17:42 DEBUG  WindowsBackend: bootloader=vista
03-22 17:42 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20633.703125 mb free ntfs)
03-22 17:42 DEBUG  WindowsBackend: drive=Drive(C: hd 20633.703125 mb free ntfs)
03-22 17:42 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 17:42 DEBUG  WindowsBackend: drive=Drive(E: hd 18186.1015625 mb free ntfs)
03-22 17:42 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 17:42 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.81640625 mb free ntfs)
03-22 17:42 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 17:42 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 17:42 DEBUG  WindowsBackend: drive=Drive(J: removable 3099.33984375 mb free fat32)
03-22 17:42 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 17:42 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 17:42 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 17:42 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 17:42 DEBUG  WindowsBackend: keyboard_layout=us
03-22 17:42 DEBUG  WindowsBackend: keyboard_variant=
03-22 17:42 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 17:42 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 17:42 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 17:42 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 17:42 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 17:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 17:42 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 DEBUG  CommonBackend: Searching for local CDs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Ubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Kubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 17:42 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:42 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 17:42 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 17:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 17:42 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 17:42 INFO   root: Running the CD menu...
03-22 17:42 DEBUG  WindowsFrontend: __init__...
03-22 17:42 DEBUG  WindowsFrontend: on_init...
03-22 17:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\translations, languages=['en_US', 'en']
03-22 17:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\translations, languages=['en_US', 'en']
03-22 17:42 INFO   root: CD menu finished
03-22 17:42 INFO   root: Running the installer...
03-22 17:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\translations, languages=['en_US', 'en']
03-22 17:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\translations, languages=['en_US', 'en']
03-22 17:42 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-22 17:42 INFO   root: Received settings
03-22 17:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\translations, languages=['en_US', 'en']
03-22 17:42 DEBUG  TaskList: # Running tasklist...
03-22 17:42 DEBUG  TaskList: ## Running select_target_dir...
03-22 17:42 INFO   WindowsBackend: Installing into G:\ubuntu
03-22 17:42 DEBUG  TaskList: ## Finished select_target_dir
03-22 17:42 DEBUG  TaskList: ## Running create_dir_structure...
03-22 17:42 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-22 17:42 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-22 17:42 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-22 17:42 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-22 17:42 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-22 17:42 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-22 17:42 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-22 17:42 DEBUG  TaskList: ## Finished create_dir_structure
03-22 17:42 DEBUG  TaskList: ## Running uncompress_target_dir...
03-22 17:42 DEBUG  TaskList: ## Finished uncompress_target_dir
03-22 17:42 DEBUG  TaskList: ## Running create_uninstaller...
03-22 17:42 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-22 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-22 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-22 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-22 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-22 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
03-22 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-22 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-22 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-22 17:42 DEBUG  TaskList: ## Finished create_uninstaller
03-22 17:42 DEBUG  TaskList: ## Running copy_installation_files...
03-22 17:42 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-22 17:42 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\winboot -> G:\ubuntu\winboot
03-22 17:42 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl9FE7.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-22 17:42 DEBUG  TaskList: ## Finished copy_installation_files
03-22 17:42 DEBUG  TaskList: ## Running get_iso...
03-22 17:42 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 DEBUG  TaskList: New task is_valid_iso
03-22 17:42 DEBUG  TaskList: ### Running is_valid_iso...
03-22 17:42 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 DEBUG  TaskList: ### Finished is_valid_iso
03-22 17:42 DEBUG  TaskList: New task check_iso
03-22 17:42 DEBUG  TaskList: ### Running check_iso...
03-22 17:42 DEBUG  CommonBackend: Checking E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:42 DEBUG  TaskList: New task get_metalink
03-22 17:42 DEBUG  TaskList: #### Running get_metalink...
03-22 17:42 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > G:\ubuntu\install
03-22 17:42 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
03-22 17:42 DEBUG  downloader: download finished (read 39020 bytes)
03-22 17:42 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > G:\ubuntu\install
03-22 17:42 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
03-22 17:42 DEBUG  downloader: download finished (read 651 bytes)
03-22 17:42 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > G:\ubuntu\install
03-22 17:42 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-22 17:42 DEBUG  downloader: download finished (read 198 bytes)
03-22 17:42 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-22 17:42 INFO   saplog: Checking block bindings..
03-22 17:42 INFO   saplog: Key verified successfully.
03-22 17:42 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink
03-22 17:42 DEBUG  TaskList: #### Finished get_metalink
03-22 17:42 DEBUG  TaskList: New task get_file_md5
03-22 17:42 DEBUG  TaskList: #### Running get_file_md5...
03-22 17:43 DEBUG  TaskList: #### Finished get_file_md5
03-22 17:43 DEBUG  TaskList: ### Finished check_iso
03-22 17:43 DEBUG  TaskList: New task copy_file
03-22 17:43 DEBUG  CommonBackend: Copying E:\ubuntu-10.04.2-desktop-amd64.iso > G:\ubuntu\install\installation.iso
03-22 17:43 DEBUG  TaskList: ### Running copy_file...
03-22 17:43 DEBUG  TaskList: ### Finished copy_file
03-22 17:43 DEBUG  TaskList: ## Finished get_iso
03-22 17:43 DEBUG  TaskList: ## Running extract_kernel...
03-22 17:43 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
03-22 17:43 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
03-22 17:43 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
03-22 17:43 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
03-22 17:43 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-22 17:43 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-22 17:43 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 41d2d275b0aed279030980587f6de7e9 == 41d2d275b0aed279030980587f6de7e9
03-22 17:43 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-22 17:43 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 774fcb24611ab59898b1e51df6cfd8d6 == 774fcb24611ab59898b1e51df6cfd8d6
03-22 17:43 DEBUG  TaskList: ## Finished extract_kernel
03-22 17:43 DEBUG  TaskList: ## Running choose_disk_sizes...
03-22 17:43 DEBUG  WindowsBackend: total size=6000
  root=5744
  swap=256
  home=0
  usr=0
03-22 17:43 DEBUG  TaskList: ## Finished choose_disk_sizes
03-22 17:43 DEBUG  TaskList: ## Running create_preseed...
03-22 17:43 DEBUG  TaskList: ## Finished create_preseed
03-22 17:43 DEBUG  TaskList: ## Running modify_bootloader...
03-22 17:43 DEBUG  TaskList: New task modify_bcd
03-22 17:43 DEBUG  TaskList: ### Running modify_bcd...
03-22 17:43 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 20633.703125 mb free ntfs)
03-22 17:43 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84381-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84381-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 17:43 DEBUG  TaskList: # Cancelling tasklist
03-22 17:43 DEBUG  TaskList: New task modify_bcd
03-22 17:43 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84381-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84381-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 17:43 DEBUG  TaskList: New task modify_bcd
03-22 17:43 DEBUG  TaskList: New task modify_bcd
03-22 17:43 DEBUG  TaskList: New task modify_bcd
03-22 17:43 DEBUG  TaskList: ## Finished modify_bootloader
03-22 17:43 DEBUG  TaskList: # Finished tasklist
03-22 17:43 INFO   root: === wubi 10.04.2 rev191 ===
03-22 17:43 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.04.2-rev191.log
03-22 17:43 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"']
03-22 17:43 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\data
03-22 17:43 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\bin\7z.exe
03-22 17:43 DEBUG  CommonBackend: Fetching basic info...
03-22 17:43 DEBUG  CommonBackend: original_exe=I:\wubi.exe
03-22 17:43 DEBUG  CommonBackend: platform=win32
03-22 17:43 DEBUG  CommonBackend: osname=nt
03-22 17:43 DEBUG  CommonBackend: language=en_US
03-22 17:43 DEBUG  CommonBackend: encoding=cp1252
03-22 17:43 DEBUG  WindowsBackend: arch=amd64
03-22 17:43 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\data\isolist.ini
03-22 17:43 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 17:43 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 17:43 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 17:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 17:43 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 17:43 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 17:43 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 17:43 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 17:43 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 17:43 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 17:43 DEBUG  WindowsBackend: Fetching host info...
03-22 17:43 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 17:43 DEBUG  WindowsBackend: windows version=vista
03-22 17:43 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 17:43 DEBUG  WindowsBackend: windows_sp=None
03-22 17:43 DEBUG  WindowsBackend: windows_build=7601
03-22 17:43 DEBUG  WindowsBackend: gmt=5
03-22 17:43 DEBUG  WindowsBackend: country=US
03-22 17:43 DEBUG  WindowsBackend: timezone=America/New_York
03-22 17:43 DEBUG  WindowsBackend: windows_username=Administrator
03-22 17:43 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 17:43 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 17:43 DEBUG  WindowsBackend: windows_language_code=1033
03-22 17:43 DEBUG  WindowsBackend: windows_language=English
03-22 17:43 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 17:43 DEBUG  WindowsBackend: bootloader=vista
03-22 17:43 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20633.15625 mb free ntfs)
03-22 17:43 DEBUG  WindowsBackend: drive=Drive(C: hd 20633.15625 mb free ntfs)
03-22 17:43 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 17:43 DEBUG  WindowsBackend: drive=Drive(E: hd 18186.1015625 mb free ntfs)
03-22 17:43 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 17:43 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.81640625 mb free ntfs)
03-22 17:43 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 17:43 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 17:43 DEBUG  WindowsBackend: drive=Drive(J: removable 3099.33984375 mb free fat32)
03-22 17:43 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 17:43 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 17:43 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 17:43 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 17:43 DEBUG  WindowsBackend: keyboard_layout=us
03-22 17:43 DEBUG  WindowsBackend: keyboard_variant=
03-22 17:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 17:43 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 17:43 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 17:43 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 17:43 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:43 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:43 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 17:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 17:43 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:43 DEBUG  CommonBackend: Searching for local CDs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Ubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Kubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 17:43 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 17:43 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 17:43 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 17:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 17:43 INFO   Distro: Found a valid CD for Ubuntu: I:\
03-22 17:43 INFO   root: Running the CD menu...
03-22 17:43 DEBUG  WindowsFrontend: __init__...
03-22 17:43 DEBUG  WindowsFrontend: on_init...
03-22 17:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\translations, languages=['en_US', 'en']
03-22 17:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\translations, languages=['en_US', 'en']
03-22 17:43 INFO   root: CD menu finished
03-22 17:43 INFO   root: Running the installer...
03-22 17:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\translations, languages=['en_US', 'en']
03-22 17:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\translations, languages=['en_US', 'en']
03-22 17:44 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-22 17:44 INFO   root: Received settings
03-22 17:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\translations, languages=['en_US', 'en']
03-22 17:44 DEBUG  TaskList: # Running tasklist...
03-22 17:44 DEBUG  TaskList: ## Running select_target_dir...
03-22 17:44 INFO   WindowsBackend: Installing into G:\ubuntu
03-22 17:44 DEBUG  TaskList: ## Finished select_target_dir
03-22 17:44 DEBUG  TaskList: ## Running create_dir_structure...
03-22 17:44 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-22 17:44 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-22 17:44 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-22 17:44 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-22 17:44 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-22 17:44 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-22 17:44 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-22 17:44 DEBUG  TaskList: ## Finished create_dir_structure
03-22 17:44 DEBUG  TaskList: ## Running uncompress_target_dir...
03-22 17:44 DEBUG  TaskList: ## Finished uncompress_target_dir
03-22 17:44 DEBUG  TaskList: ## Running create_uninstaller...
03-22 17:44 DEBUG  WindowsBackend: Copying uninstaller I:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-22 17:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-22 17:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-22 17:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-22 17:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-22 17:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.2-rev191
03-22 17:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-22 17:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-22 17:44 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-22 17:44 DEBUG  TaskList: ## Finished create_uninstaller
03-22 17:44 DEBUG  TaskList: ## Running copy_installation_files...
03-22 17:44 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-22 17:44 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\winboot -> G:\ubuntu\winboot
03-22 17:44 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pylCC73.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-22 17:44 DEBUG  TaskList: ## Finished copy_installation_files
03-22 17:44 DEBUG  TaskList: ## Running get_iso...
03-22 17:44 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:44 DEBUG  TaskList: New task is_valid_iso
03-22 17:44 DEBUG  TaskList: ### Running is_valid_iso...
03-22 17:44 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:44 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:44 DEBUG  TaskList: ### Finished is_valid_iso
03-22 17:44 DEBUG  TaskList: New task check_iso
03-22 17:44 DEBUG  TaskList: ### Running check_iso...
03-22 17:44 DEBUG  CommonBackend: Checking E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:44 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:44 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 17:44 DEBUG  TaskList: New task get_metalink
03-22 17:44 DEBUG  TaskList: #### Running get_metalink...
03-22 17:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink) > G:\ubuntu\install
03-22 17:44 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.04.2-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04.2/ubuntu-10.04.2-desktop-amd64.metalink, basename=ubuntu-10.04.2-desktop-amd64.metalink, length=39020, text=None
03-22 17:44 DEBUG  downloader: download finished (read 39020 bytes)
03-22 17:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink) > G:\ubuntu\install
03-22 17:44 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=651, text=None
03-22 17:44 DEBUG  downloader: download finished (read 651 bytes)
03-22 17:44 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg) > G:\ubuntu\install
03-22 17:44 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.2/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-22 17:44 DEBUG  downloader: download finished (read 198 bytes)
03-22 17:44 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-22 17:44 INFO   saplog: Checking block bindings..
03-22 17:44 INFO   saplog: Key verified successfully.
03-22 17:44 DEBUG  CommonBackend: metalink md5sums:
20cc9c37f09c8aa1f49c3d41e9956537  ubuntu-10.04-netbook-armel+dove.metalink
88ddc306074203f6cd97dadd1f645752  ubuntu-10.04-netbook-armel+imx51.metalink
8d837320137f3f76dda3d9a8296c0ace  ubuntu-10.04-netbook-i386.metalink
90dd1611d9178a064f529115e0c31556  ubuntu-10.04.2-alternate-amd64.metalink
1da39cf8ef1574af434be85f966fd6ca  ubuntu-10.04.2-alternate-i386.metalink
2c1e61efc8c1daecbf1105e5083ceefe  ubuntu-10.04.2-desktop-amd64.metalink
7412fe194b9e65ec6348aa7be5fb1f3d  ubuntu-10.04.2-desktop-i386.metalink
95ea8d107d3b6a5b37bf9bc256e6e4f9  ubuntu-10.04.2-server-amd64.metalink
79a18577ded9811ba7ad10facb4acfdf  ubuntu-10.04.2-server-i386.metalink
03-22 17:44 DEBUG  TaskList: #### Finished get_metalink
03-22 17:44 DEBUG  TaskList: New task get_file_md5
03-22 17:44 DEBUG  TaskList: #### Running get_file_md5...
03-22 17:44 DEBUG  TaskList: #### Finished get_file_md5
03-22 17:44 DEBUG  TaskList: ### Finished check_iso
03-22 17:44 DEBUG  TaskList: New task copy_file
03-22 17:44 DEBUG  CommonBackend: Copying E:\ubuntu-10.04.2-desktop-amd64.iso > G:\ubuntu\install\installation.iso
03-22 17:44 DEBUG  TaskList: ### Running copy_file...
03-22 17:44 DEBUG  TaskList: ### Finished copy_file
03-22 17:44 DEBUG  TaskList: ## Finished get_iso
03-22 17:44 DEBUG  TaskList: ## Running extract_kernel...
03-22 17:44 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
03-22 17:44 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
03-22 17:44 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
03-22 17:44 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
03-22 17:44 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
03-22 17:44 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
03-22 17:44 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 41d2d275b0aed279030980587f6de7e9 == 41d2d275b0aed279030980587f6de7e9
03-22 17:44 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
03-22 17:44 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 774fcb24611ab59898b1e51df6cfd8d6 == 774fcb24611ab59898b1e51df6cfd8d6
03-22 17:44 DEBUG  TaskList: ## Finished extract_kernel
03-22 17:44 DEBUG  TaskList: ## Running choose_disk_sizes...
03-22 17:44 DEBUG  WindowsBackend: total size=6000
  root=5744
  swap=256
  home=0
  usr=0
03-22 17:44 DEBUG  TaskList: ## Finished choose_disk_sizes
03-22 17:44 DEBUG  TaskList: ## Running create_preseed...
03-22 17:44 DEBUG  TaskList: ## Finished create_preseed
03-22 17:44 DEBUG  TaskList: ## Running modify_bootloader...
03-22 17:44 DEBUG  TaskList: New task modify_bcd
03-22 17:44 DEBUG  TaskList: ### Running modify_bcd...
03-22 17:44 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 20633.15625 mb free ntfs)
03-22 17:44 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84382-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84382-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 17:44 DEBUG  TaskList: # Cancelling tasklist
03-22 17:44 DEBUG  TaskList: New task modify_bcd
03-22 17:44 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84382-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {16e84382-317e-11df-bb8d-f217c2e7383b} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.
The request is not supported.
 
>>stdout=
03-22 17:44 DEBUG  TaskList: New task modify_bcd
03-22 17:44 DEBUG  TaskList: New task modify_bcd
03-22 17:44 DEBUG  TaskList: New task modify_bcd
03-22 17:44 DEBUG  TaskList: ## Finished modify_bootloader
03-22 17:44 DEBUG  TaskList: # Finished tasklist

```
 
 
i tried installing ubuntu from wubi in my G:/ drive 2-3 times and i have 2 log files generated.one i showed above.
And the other is this one - 
**wubi-10.10-rev197 **and here it is - 
 
```
03-22 05:33 INFO   root: === wubi 10.10 rev197 ===
03-22 05:33 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.10-rev197.log
03-22 05:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-22 05:33 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\data
03-22 05:33 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\bin\7z.exe
03-22 05:33 DEBUG  CommonBackend: Fetching basic info...
03-22 05:33 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-22 05:33 DEBUG  CommonBackend: platform=win32
03-22 05:33 DEBUG  CommonBackend: osname=nt
03-22 05:33 DEBUG  CommonBackend: language=en_US
03-22 05:33 DEBUG  CommonBackend: encoding=cp1252
03-22 05:33 DEBUG  WindowsBackend: arch=amd64
03-22 05:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\data\isolist.ini
03-22 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 05:33 DEBUG  WindowsBackend: Fetching host info...
03-22 05:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 05:33 DEBUG  WindowsBackend: windows version=vista
03-22 05:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 05:33 DEBUG  WindowsBackend: windows_sp=None
03-22 05:33 DEBUG  WindowsBackend: windows_build=7601
03-22 05:33 DEBUG  WindowsBackend: gmt=5
03-22 05:33 DEBUG  WindowsBackend: country=US
03-22 05:33 DEBUG  WindowsBackend: timezone=America/New_York
03-22 05:33 DEBUG  WindowsBackend: windows_username=Administrator
03-22 05:33 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 05:33 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 05:33 DEBUG  WindowsBackend: windows_language_code=1033
03-22 05:33 DEBUG  WindowsBackend: windows_language=English
03-22 05:33 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 05:33 DEBUG  WindowsBackend: bootloader=vista
03-22 05:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20470.4296875 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(C: hd 20470.4296875 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(E: hd 18190.5039063 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(G: hd 9243.2421875 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 05:33 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
03-22 05:33 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
03-22 05:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-22 05:33 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 05:33 DEBUG  WindowsBackend: keyboard_layout=us
03-22 05:33 DEBUG  WindowsBackend: keyboard_variant=
03-22 05:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 05:33 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 05:33 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 05:33 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 05:33 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  Distro:   checking Ubuntu Netbook ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
03-22 05:33 DEBUG  Distro:   checking Kubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
03-22 05:33 DEBUG  Distro:   checking Kubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
03-22 05:33 DEBUG  Distro:   checking Kubuntu Netbook ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu Netbook
03-22 05:33 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
03-22 05:33 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
03-22 05:33 DEBUG  Distro:   checking Mythbuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
03-22 05:33 DEBUG  Distro:   checking Mythbuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
03-22 05:33 DEBUG  CommonBackend: Searching for local CDs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl2211.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu Netbook
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
03-22 05:33 INFO   root: Already installed, running the uninstaller...
03-22 05:33 INFO   root: Running the uninstaller...
03-22 05:33 INFO   CommonBackend: Launching previous uninestaller G:\ubuntu\uninstall-wubi.exe
03-22 05:33 DEBUG  root: application.quit
03-22 05:33 DEBUG  root: application.on_quit
03-22 05:33 INFO   root: sys.exit
03-22 05:33 INFO   root: Quitting application
03-22 05:33 INFO   root: === wubi 10.10 rev197 ===
03-22 05:33 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-10.10-rev197.log
03-22 05:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-22 05:33 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\data
03-22 05:33 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\bin\7z.exe
03-22 05:33 DEBUG  CommonBackend: Fetching basic info...
03-22 05:33 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-22 05:33 DEBUG  CommonBackend: platform=win32
03-22 05:33 DEBUG  CommonBackend: osname=nt
03-22 05:33 DEBUG  CommonBackend: language=en_US
03-22 05:33 DEBUG  CommonBackend: encoding=cp1252
03-22 05:33 DEBUG  WindowsBackend: arch=amd64
03-22 05:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\data\isolist.ini
03-22 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-22 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
03-22 05:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
03-22 05:33 DEBUG  WindowsBackend: Fetching host info...
03-22 05:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-22 05:33 DEBUG  WindowsBackend: windows version=vista
03-22 05:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-22 05:33 DEBUG  WindowsBackend: windows_sp=None
03-22 05:33 DEBUG  WindowsBackend: windows_build=7601
03-22 05:33 DEBUG  WindowsBackend: gmt=5
03-22 05:33 DEBUG  WindowsBackend: country=US
03-22 05:33 DEBUG  WindowsBackend: timezone=America/New_York
03-22 05:33 DEBUG  WindowsBackend: windows_username=Administrator
03-22 05:33 DEBUG  WindowsBackend: user_full_name=Administrator
03-22 05:33 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
03-22 05:33 DEBUG  WindowsBackend: windows_language_code=1033
03-22 05:33 DEBUG  WindowsBackend: windows_language=English
03-22 05:33 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 965 Processor
03-22 05:33 DEBUG  WindowsBackend: bootloader=vista
03-22 05:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 20469.953125 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(C: hd 20469.953125 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(D: hd 3513.74609375 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(E: hd 18190.5039063 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(G: hd 9945.81640625 mb free ntfs)
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
03-22 05:33 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
03-22 05:33 DEBUG  WindowsBackend: uninstaller_path=None
03-22 05:33 DEBUG  WindowsBackend: previous_target_dir=None
03-22 05:33 DEBUG  WindowsBackend: previous_distro_name=None
03-22 05:33 DEBUG  WindowsBackend: keyboard_id=67699721
03-22 05:33 DEBUG  WindowsBackend: keyboard_layout=us
03-22 05:33 DEBUG  WindowsBackend: keyboard_variant=
03-22 05:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-22 05:33 DEBUG  CommonBackend: locale=en_US.UTF-8
03-22 05:33 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
03-22 05:33 DEBUG  CommonBackend: Searching ISOs on USB devices
03-22 05:33 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  Distro:   checking Ubuntu Netbook ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
03-22 05:33 DEBUG  Distro:   checking Kubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
03-22 05:33 DEBUG  Distro:   checking Kubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
03-22 05:33 DEBUG  Distro:   checking Kubuntu Netbook ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu Netbook
03-22 05:33 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
03-22 05:33 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
03-22 05:33 DEBUG  Distro:   checking Mythbuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
03-22 05:33 DEBUG  Distro:   checking Mythbuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
03-22 05:33 DEBUG  CommonBackend: Searching for local CDs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
03-22 05:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Ubuntu Netbook
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Kubuntu Netbook
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
03-22 05:33 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
03-22 05:33 INFO   root: Running the installer...
03-22 05:33 DEBUG  WindowsFrontend: __init__...
03-22 05:33 DEBUG  WindowsFrontend: on_init...
03-22 05:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\translations, languages=['en_US', 'en']
03-22 05:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\translations, languages=['en_US', 'en']
03-22 05:33 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=4000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=administrator
03-22 05:33 INFO   root: Received settings
03-22 05:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\translations, languages=['en_US', 'en']
03-22 05:33 DEBUG  TaskList: # Running tasklist...
03-22 05:33 DEBUG  TaskList: ## Running select_target_dir...
03-22 05:33 INFO   WindowsBackend: Installing into G:\ubuntu
03-22 05:33 DEBUG  TaskList: ## Finished select_target_dir
03-22 05:33 DEBUG  TaskList: ## Running create_dir_structure...
03-22 05:33 DEBUG  CommonBackend: Creating dir G:\ubuntu
03-22 05:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
03-22 05:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
03-22 05:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
03-22 05:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
03-22 05:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
03-22 05:33 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
03-22 05:33 DEBUG  TaskList: ## Finished create_dir_structure
03-22 05:33 DEBUG  TaskList: ## Running uncompress_target_dir...
03-22 05:33 DEBUG  TaskList: ## Finished uncompress_target_dir
03-22 05:33 DEBUG  TaskList: ## Running create_uninstaller...
03-22 05:33 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
03-22 05:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
03-22 05:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
03-22 05:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-22 05:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
03-22 05:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
03-22 05:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-22 05:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
03-22 05:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
03-22 05:33 DEBUG  TaskList: ## Finished create_uninstaller
03-22 05:33 DEBUG  TaskList: ## Running copy_installation_files...
03-22 05:33 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
03-22 05:33 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\winboot -> G:\ubuntu\winboot
03-22 05:33 DEBUG  WindowsBackend: Copying C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
03-22 05:33 DEBUG  TaskList: ## Finished copy_installation_files
03-22 05:33 DEBUG  TaskList: ## Running get_iso...
03-22 05:33 DEBUG  CommonBackend: Searching for local CD
03-22 05:33 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl7D6A.tmp\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
03-22 05:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  CommonBackend: Searching for local ISO
03-22 05:33 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.04.2-desktop-amd64.iso
03-22 05:33 DEBUG  Distro: wrong version: 10.04.2 != 10.10
03-22 05:33 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
03-22 05:33 DEBUG  TaskList: New task get_metalink
03-22 05:33 DEBUG  TaskList: ### Running get_metalink...
03-22 05:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink) > G:\ubuntu\install
03-22 05:33 DEBUG  downloader: Download start filename=G:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
03-22 05:34 DEBUG  downloader: download finished (read 9135 bytes)
03-22 05:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > G:\ubuntu\install
03-22 05:34 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
03-22 05:34 DEBUG  downloader: download finished (read 488 bytes)
03-22 05:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > G:\ubuntu\install
03-22 05:34 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
03-22 05:34 DEBUG  downloader: download finished (read 198 bytes)
03-22 05:34 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
03-22 05:34 INFO   saplog: Checking block bindings..
03-22 05:34 INFO   saplog: Key verified successfully.
03-22 05:34 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink
03-22 05:34 DEBUG  TaskList: ### Finished get_metalink
03-22 05:34 DEBUG  TaskList: New task download
03-22 05:34 DEBUG  TaskList: ### Running download...
03-22 05:34 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent) > G:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
03-22 05:34 INFO   WindowsFrontend: Operation cancelled
03-22 05:34 DEBUG  WindowsFrontend: frontend.quit
03-22 05:34 DEBUG  WindowsFrontend: frontend.on_quit
03-22 05:34 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
03-22 05:34 DEBUG  TaskList: # Cancelling tasklist
03-22 05:34 DEBUG  TaskList: ### Finished download
03-22 05:34 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
03-22 05:34 DEBUG  root: application.on_quit
03-22 05:34 DEBUG  root: Forceful exit
03-22 05:34 INFO   root: sys.exit

``` 
 
Now by seeing these message,i suspect that there is a problem installing grub or it is not able to set ubuntu as an option to windows 7 boot loader.I am using windows 7 64bit Ultimate and i am the admin of my computer.
 
My computer specs - AMD Phenom II X4 965 Black Edition Processor.
8GB DDR3 RAM
Asus M4A77TD Pro motherboard.
Asus Formula HD5750 1GB DDR5 graphics card.
 
Can someone please help me out.please guide me in simple language as in step by step instructions as i am new to the installation of Ubuntu on hard drive.
 
**_Bottom line -_**
I want to install ubuntu on my **G:\ drive i.e. 10GB partition.**
Please help me out.

---

### Post by Dutch70 on 2011-03-22
Welcome to UF

Are you using wubi, to install Ubuntu into windows "Programs"? If so, you don't need a partition for it, or Grub.

If you're installing Ubuntu into it's own partition, you don't need Wubi.

---

### Post by Quackers on 2011-03-22
Welcome to UF.
If you want to dual boot Windows and Ubuntu (with Ubuntu actually installed to a separate partition) I would first recommend that you make the Windows recovery dvd's (if you haven't already done that). I would also recommend that you make the Windows repair cd (Start > Control Panel > Restore & Backup Centre, then in the left pane click on "make a recovery cd" - Windows calls it a recovery cd, but most people call it a repair disc.
You may need this disc to repair your hard-drive's mbr at some point.

As you want to install version 10.04 I would recommend that you delete your G: partition from within Windows using the Disk Management Console.
This will leave "unallocated space" for Ubuntu to install into. 
You can then boot from the Ubuntu cd and select "install using largest free space" option, which will automatically create the necessary partitions for Ubuntu.

---

### Post by karan999 on 2011-03-22
> **Quackers said:**
> Welcome to UF.
If you want to dual boot Windows and Ubuntu (with Ubuntu actually installed to a separate partition) I would first recommend that you make the Windows recovery dvd's (if you haven't already done that). I would also recommend that you make the Windows repair cd (Start > Control Panel > Restore & Backup Centre, then in the left pane click on "make a recovery cd" - Windows calls it a recovery cd, but most people call it a repair disc.
You may need this disc to repair your hard-drive's mbr at some point.
 
As you want to install version 10.04 I would recommend that you delete your G: partition from within Windows using the Disk Management Console.
This will leave "unallocated space" for Ubuntu to install into. 
You can then boot from the Ubuntu cd and select "install using largest free space" option, which will automatically create the necessary partitions for Ubuntu.
 
i deleted my G: drive.now it is unallocated.then i tried booting from my ubuntu live USB.but when i click on install(on unetbootin boot loader screen), my computer restarts and the monitor goes off.as if the computer has gone on stand by mode.

---

### Post by Quackers on 2011-03-22
What do you mean by "restarts"? Do you mean it turns off and then reboots the cd? Or do you just mean that the screen goes black?

---

### Post by karan999 on 2011-03-22
> **Quackers said:**
> What do you mean by "restarts"? Do you mean it turns off and then reboots the cd? Or do you just mean that the screen goes black?
 
Firstly,
my usb drive is detected on boot.
my computer boots from live usb.
then i select the option install Ubuntu.
then i get Ubuntu loading screen with ubuntu logo and 5 dots going from red to white.(basically the ubuntu booting screen as u may understand.)
 
And then suddenly during this screen, my computer is automatically restarted and it my cpu doesnt shuts down.just my monitor goes not responding.(like when we shut down our computer our monitor power light turns from blue to orange just before we manually press the monitor button to shut it down.)

---

### Post by Quackers on 2011-03-22
Ok thanks. That's not restarting. That's likely to be a graphics problem. What graphics card are you using?

---

### Post by mhpathfinder on 2011-03-22
> **karan999 said:**
> Firstly,
my usb drive is detected on boot.
my computer boots from live usb.
then i select the option install Ubuntu.
then i get Ubuntu loading screen with ubuntu logo and 5 dots going from red to white.(basically the ubuntu booting screen as u may understand.)
 
And then suddenly during this screen, my computer is automatically restarted and it my cpu doesnt shuts down.just my monitor goes not responding.(like when we shut down our computer our monitor power light turns from blue to orange just before we manually press the monitor button to shut it down.)

It's also possible that that the installation .iso is flawed, or that it didn't transfer intact when you created your live/install USB flash drive.  This doesn't happen often, but I've had this happen before.  I went to Ubuntu's install site and downloaded a fresh .iso of 10.04, and recreated my install flash drive.  Then tried the install again, and all was well.

It may be, as Quacker suggested, a graphics problem, but I doubt if you would even get an Ubuntu logo with five dots if that was the case, although I am not certain.  Good luck.

---

### Post by karan999 on 2011-03-23
> **Quackers said:**
> Ok thanks. That's not restarting. That's likely to be a graphics problem. What graphics card are you using?
 
 
i am using Asus Formula HD5750.(Generic ATI RADEON)
 
> **mhpathfinder said:**
> It's also possible that that the installation .iso is flawed, or that it didn't transfer intact when you created your live/install USB flash drive. This doesn't happen often, but I've had this happen before. I went to Ubuntu's install site and downloaded a fresh .iso of 10.04, and recreated my install flash drive. Then tried the install again, and all was well.
 
It may be, as Quacker suggested, a graphics problem, but I doubt if you would even get an Ubuntu logo with five dots if that was the case, although I am not certain. Good luck.
 
Sure,i think so too.let me give it a try.infact,i formatted my windows 7 64bit Ultimate again so see if anything is wrong there.but still the same problem persists :(
 
will download a fresh copy n then check.

---

### Post by Quackers on 2011-03-23
Try the nomodeset option when booting the disc. Details below
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by karan999 on 2011-03-27
> **Quackers said:**
> Try the nomodeset option when booting the disc. Details below
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
 
 
ok i deleted my E: partition.now im left with my D: drive only with some data on it.
 
And i now run Ubuntu from my Live USB and it works !!!!!!!!!!!!
 
 
here are all my details of my partition.
 
[http://www.mediafire.com/?n54syt5zeo3kya6](http://www.mediafire.com/?n54syt5zeo3kya6)
 
kindly have a look.and please guide me how to make partition for ubuntu.
 
A member of ubuntu forums 'sikanderr' guided me to make partitions like this.
 
1. Primary Partition, NTFS, Windows 50 GB (to hold the games/softwares and all that stuff)
2. Primary Partition, NTFS, 365 GB Data Partition shared between Windows, Fedora and Ubuntu so that you can access all your music, documents, movies in all the Operating Systems.
3. Logical/Extended Partition, ext4, 30 GB, Mount Point '/' Fedora.
4. Logical/Extended Partition, ext4, 30 GB, Mount Point '/' Ubuntu.
5. Logical/Extended Partition, Swap, 4 GB

 
but by seeing my screenshots he told me to post my problem here as my current partitions were't suitable for the installation.kindly have a look and guide me how to make partition.im ready to format everything.i have backed up my data.

---

### Post by Dutch70 on 2011-03-27
Can't see any screenshot from there. You can easily attach a screenshot via the paper clip in the toolbar when posting. 

Since I don't know what issue you're having, see if this helps.
[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by karan999 on 2011-03-27
> **Dutch70 said:**
> Can't see any screenshot from there. You can easily attach a screenshot via the paper clip in the toolbar when posting. 
 
Since I don't know what issue you're having, see if this helps.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
 
 
 
click on the link iv posted.and download the .rar file and extract it to see all my screenshots.

---

### Post by karan999 on 2011-03-27
Found out the problem !!!!!!!!!!!!! its the 100mb Windows Reserved partition which is automatically created while installing Windows 7 64 bit Ultimate edition !!!!!!!
 
This. is recognized as the second partition dev/sda2 which i found out how to remove since my windows 7 is installed in my C: drive.
 
This System reserved partition is used to backup data and contains other windows 7 boot files which can me removed my creating an repair disc of my windows 7 which is an alternate solution to my System reserved partition. :)
 
Now the problem left to identify is the first partition which is automatically created when i insert my live usb stick in which i have installed Ubuntu.
 
Now when i click on install ubuntu from the live usb stick and go to the manually specify the partition space page,here a 1mb partition i.e. dev/sda1 is automatically created.
 
Please tell me what is this.and how to remove it permanently.because when i try to remove this partition it again reappears after some time when i reclick on install ubuntu from ubuntu desktop.

---

### Post by Quackers on 2011-03-27
The 1MB is usually a space between partitions, not a partition. A sort of boundary between partitions.

---

### Post by karan999 on 2011-03-27
> **Quackers said:**
> The 1MB is usually a space between partitions, not a partition. A sort of boundary between partitions.
 
ok..thanks for the info.will make the partitions and installation tomorrow.feeing sleepy now.

---

### Post by Dutch70 on 2011-03-28
> **karan999 said:**
> click on the link iv posted.and download the .rar file and extract it to see all my screenshots.

[-(  

I'll pass.

Good luck.

---

### Post by karan999 on 2011-03-28
> **Dutch70 said:**
> [-( 
 
I'll pass.
 
Good luck.
 
not working :( not able to delete my partitions.
 
Ok,lets start with the basics again.In my computer i have 3 partitions on a 500GB HDD.
1> c: drive of 53GB on which my windows 7 64bit Ultimate edition is installed. NTFS
2>d: drive of 382GB NTFS
3> e: drive of 30GB NTFS

but when in ubuntu,i get to see 4 partitions.
1>a 1mb partition.
2>a 100mb partition.
3>my c: drive
4> my rest of the HDD space merged all into one partition and displayed.

i really dont understand how to delete these two partitions.I have read forums where people have said that the 100mb partition is self created during the installation of windows 7.i also found a fix to this problem but its not working for me.
 
Here is the link to what i have tried - [http://www.sevenforums.com/tutorials/71363-system-reserved-partition-delete.html](http://www.sevenforums.com/tutorials/71363-system-reserved-partition-delete.html)

---

### Post by Quackers on 2011-03-28
Please post a screenshot of what gparted shows.

---

### Post by oldfred on 2011-03-28
In one of your screen shots it showed dynamic partitions. 

Windows normally creates basic partitions which follow the MBR standard of 4 primary partitions. But some versions of windows will convert to dynamic if you try to create more than 4, rather than add the extended partition to hold logicals. Dynamic is a windows only logical volume manager that does not work with anything else.

Windows officially says to back up your system and totally erase it to convert back to basic partitions.


IF you attempt any of this be sure to have good backups.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Only if partitions are in a certain order these may work:
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)

---

### Post by karan999 on 2011-03-28
> **oldfred said:**
> In one of your screen shots it showed dynamic partitions. 
 
Windows normally creates basic partitions which follow the MBR standard of 4 primary partitions. But some versions of windows will convert to dynamic if you try to create more than 4, rather than add the extended partition to hold logicals. Dynamic is a windows only logical volume manager that does not work with anything else.
 
Windows officially says to back up your system and totally erase it to convert back to basic partitions.
 
 
IF you attempt any of this be sure to have good backups.
 
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
 
Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
 
Only if partitions are in a certain order these may work:
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
 
 
sure..i'll look into it.
 
but now a new problem has come up.
 
Here it is.i have written the description inside the uploaded pic itself for better understanding where i screwed up. :(
 
 
[IMG]http://img705.imageshack.us/img705/9779/problemml.png[/IMG]

---

### Post by oldfred on 2011-03-28
I believe dynamic partitions are like logical volumes in Linux. As such it can combine parts of a drive into one logical d: drive. So you do not have 3 D: drives, just one, but it is in 3 locations. So if you attempt to delete part it will want to delete the entire thing as it is just one d: drive.

---

