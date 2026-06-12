---
title: "Installation Error Halts Process-&quot;Cannot download the metalink and therefore the ISO&quot;"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by u2rcrazy on 2010-05-24
10.04 Installation Error Message Halts Process


I originally had Ubuntu 9.10 on my system and tried to upgrade to 10.04.  I encountered an error that prohibited my from continuing further.  I decided to uninstall the Ubuntu from my Windows 7 system and reinstall it from the Ubuntu.com site.

I went to the site ([http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi)) and downloaded it.  I double clicked the download and put in my password in the window that popped up.  The process starts and goes for about 5 seconds when I receive this error message:[INDENT]An error occurred:

Cannot download the metalink and therefore the ISO

for more information, please see the log file:
c:\users\(my user name)\appdata\local\temp\wubi-10.04-rev189.log

[/INDENT][ATTACH]158059[/ATTACH]

What does this mean and how can I solve the problem?  I would like to have a 64bit Ubuntu & Windows 7 dual boot system.  Thanks.

Bob   :guitar:

---

### Post by ronnielsen1 on 2010-05-24
> c:\users\(my user name)\appdata\local\temp\wubi-10.04-rev189.log

Post the output of this file

---

### Post by darkod on 2010-05-24
By installing wubi you won't have a dual boot system. Wubi is installed inside windows, not as full ubuntu on its own linux partition.

I suggest you download the 10.04 image, burn a cd with it and install like that.

If you still want to install wubi, again downloading the image should work because wubi.exe is included on it. But to save you waiting for wubi to download the files, just extract the wubi.exe from the ISO and put both the ISO and wubi.exe in a same folder. Then when you start wubi.exe it will use the ISO, not downloading over the internet.

---

### Post by u2rcrazy on 2010-05-24
ronnielsen1,

Here's the contents of the log file:  


[INDENT]05-16 23:57 INFO   root: === wubi 10.04 rev189 ===
05-16 23:57 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-16 23:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\u2rcrazy\\Downloads\\wubi(2).exe"']
05-16 23:57 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\data
05-16 23:57 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\bin\7z.exe
05-16 23:57 DEBUG  CommonBackend: Fetching basic info...
05-16 23:57 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(2).exe
05-16 23:57 DEBUG  CommonBackend: platform=win32
05-16 23:57 DEBUG  CommonBackend: osname=nt
05-16 23:57 DEBUG  CommonBackend: language=en_US
05-16 23:57 DEBUG  CommonBackend: encoding=cp1252
05-16 23:57 DEBUG  WindowsBackend: arch=amd64
05-16 23:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\data\isolist.ini
05-16 23:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 23:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 23:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 23:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 23:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 23:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 23:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 23:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 23:57 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-16 23:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 23:57 DEBUG  WindowsBackend: Fetching host info...
05-16 23:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 23:57 DEBUG  WindowsBackend: windows version=vista
05-16 23:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-16 23:57 DEBUG  WindowsBackend: windows_sp=None
05-16 23:57 DEBUG  WindowsBackend: windows_build=7600
05-16 23:57 DEBUG  WindowsBackend: gmt=-8
05-16 23:57 DEBUG  WindowsBackend: country=US
05-16 23:57 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-16 23:57 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-16 23:57 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-16 23:57 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-16 23:57 DEBUG  WindowsBackend: windows_language_code=1033
05-16 23:57 DEBUG  WindowsBackend: windows_language=English
05-16 23:57 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-16 23:57 DEBUG  WindowsBackend: bootloader=vista
05-16 23:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 122867.058594 mb free ntfs)
05-16 23:57 DEBUG  WindowsBackend: drive=Drive(C: hd 122867.058594 mb free ntfs)
05-16 23:57 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-16 23:57 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-16 23:57 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-16 23:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-16 23:57 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 23:57 DEBUG  WindowsBackend: keyboard_layout=us
05-16 23:57 DEBUG  WindowsBackend: keyboard_variant=
05-16 23:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 23:57 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 23:57 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-16 23:57 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 23:57 DEBUG  CommonBackend: Searching for local CDs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Ubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Ubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Ubuntu Netbook CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Kubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Kubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Kubuntu Netbook CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Xubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Xubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Mythbuntu CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp is a valid Mythbuntu CD
05-16 23:57 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 23:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 23:57 INFO   root: Already installed, running the uninstaller...
05-16 23:57 INFO   root: Running the uninstaller...
05-16 23:57 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
05-16 23:57 DEBUG  root: application.quit
05-16 23:57 DEBUG  root: application.on_quit
05-16 23:57 INFO   root: sys.exit
05-16 23:57 INFO   root: Quitting application
05-17 00:02 INFO   root: === wubi 10.04 rev189 ===
05-17 00:02 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-17 00:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\u2rcrazy\\Downloads\\wubi(3).exe"']
05-17 00:02 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\data
05-17 00:02 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\bin\7z.exe
05-17 00:02 DEBUG  CommonBackend: Fetching basic info...
05-17 00:02 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(3).exe
05-17 00:02 DEBUG  CommonBackend: platform=win32
05-17 00:02 DEBUG  CommonBackend: osname=nt
05-17 00:02 DEBUG  CommonBackend: language=en_US
05-17 00:02 DEBUG  CommonBackend: encoding=cp1252
05-17 00:02 DEBUG  WindowsBackend: arch=amd64
05-17 00:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\data\isolist.ini
05-17 00:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-17 00:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-17 00:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-17 00:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-17 00:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-17 00:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-17 00:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-17 00:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-17 00:02 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-17 00:02 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-17 00:02 DEBUG  WindowsBackend: Fetching host info...
05-17 00:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-17 00:02 DEBUG  WindowsBackend: windows version=vista
05-17 00:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-17 00:02 DEBUG  WindowsBackend: windows_sp=None
05-17 00:02 DEBUG  WindowsBackend: windows_build=7600
05-17 00:02 DEBUG  WindowsBackend: gmt=-8
05-17 00:02 DEBUG  WindowsBackend: country=US
05-17 00:02 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-17 00:02 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-17 00:02 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-17 00:02 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-17 00:02 DEBUG  WindowsBackend: windows_language_code=1033
05-17 00:02 DEBUG  WindowsBackend: windows_language=English
05-17 00:02 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-17 00:02 DEBUG  WindowsBackend: bootloader=vista
05-17 00:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153602.765625 mb free ntfs)
05-17 00:02 DEBUG  WindowsBackend: drive=Drive(C: hd 153602.765625 mb free ntfs)
05-17 00:02 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-17 00:02 DEBUG  WindowsBackend: uninstaller_path=None
05-17 00:02 DEBUG  WindowsBackend: previous_target_dir=None
05-17 00:02 DEBUG  WindowsBackend: previous_distro_name=None
05-17 00:02 DEBUG  WindowsBackend: keyboard_id=67699721
05-17 00:02 DEBUG  WindowsBackend: keyboard_layout=us
05-17 00:02 DEBUG  WindowsBackend: keyboard_variant=
05-17 00:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-17 00:02 DEBUG  CommonBackend: locale=en_US.UTF-8
05-17 00:02 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-17 00:02 DEBUG  CommonBackend: Searching ISOs on USB devices
05-17 00:02 DEBUG  CommonBackend: Searching for local CDs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Ubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Ubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Ubuntu Netbook CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Kubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Kubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Kubuntu Netbook CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Xubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Xubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Mythbuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Mythbuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 INFO   root: Running the installer...
05-17 00:02 DEBUG  WindowsFrontend: __init__...
05-17 00:02 DEBUG  WindowsFrontend: on_init...
05-17 00:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\translations, languages=['en_US', 'en']
05-17 00:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\translations, languages=['en_US', 'en']
05-17 00:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=u2rcrazy
05-17 00:02 INFO   root: Received settings
05-17 00:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\translations, languages=['en_US', 'en']
05-17 00:02 DEBUG  TaskList: # Running tasklist...
05-17 00:02 DEBUG  TaskList: ## Running select_target_dir...
05-17 00:02 INFO   WindowsBackend: Installing into C:\ubuntu
05-17 00:02 DEBUG  TaskList: ## Finished select_target_dir
05-17 00:02 DEBUG  TaskList: ## Running create_dir_structure...
05-17 00:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-17 00:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-17 00:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-17 00:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-17 00:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-17 00:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-17 00:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-17 00:02 DEBUG  TaskList: ## Finished create_dir_structure
05-17 00:02 DEBUG  TaskList: ## Running uncompress_target_dir...
05-17 00:02 DEBUG  TaskList: ## Finished uncompress_target_dir
05-17 00:02 DEBUG  TaskList: ## Running create_uninstaller...
05-17 00:02 DEBUG  WindowsBackend: Copying uninstaller C:\Users\u2rcrazy\Downloads\wubi(3).exe -> C:\ubuntu\uninstall-wubi.exe
05-17 00:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-17 00:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-17 00:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-17 00:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-17 00:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-17 00:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-17 00:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-17 00:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-17 00:02 DEBUG  TaskList: ## Finished create_uninstaller
05-17 00:02 DEBUG  TaskList: ## Running copy_installation_files...
05-17 00:02 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-17 00:02 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\winboot -> C:\ubuntu\winboot
05-17 00:02 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-17 00:02 DEBUG  TaskList: ## Finished copy_installation_files
05-17 00:02 DEBUG  TaskList: ## Running get_iso...
05-17 00:02 DEBUG  CommonBackend: Searching for local CD
05-17 00:02 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp is a valid Ubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl222.tmp\casper\filesystem.squashfs
05-17 00:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:02 DEBUG  CommonBackend: Searching for local ISO
05-17 00:02 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-17 00:03 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-17 00:03 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:03 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:03 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-17 00:03 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-17 00:03 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:03 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:03 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-17 00:03 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-17 00:03 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:03 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:03 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-17 00:03 DEBUG  TaskList: New task get_metalink
05-17 00:03 DEBUG  TaskList: ### Running get_metalink...
05-17 00:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > C:\ubuntu\install
05-17 00:03 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-17 00:03 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
05-17 00:03 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-17 00:03 DEBUG  TaskList: ### Finished get_metalink
05-17 00:03 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-17 00:03 DEBUG  TaskList: # Cancelling tasklist
05-17 00:03 DEBUG  TaskList: # Finished tasklist
05-17 00:03 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-17 00:03 INFO   root: === wubi 10.04 rev189 ===
05-17 00:03 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-17 00:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\u2rcrazy\\Downloads\\wubi(3).exe"']
05-17 00:03 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\data
05-17 00:03 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\bin\7z.exe
05-17 00:03 DEBUG  CommonBackend: Fetching basic info...
05-17 00:03 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(3).exe
05-17 00:03 DEBUG  CommonBackend: platform=win32
05-17 00:03 DEBUG  CommonBackend: osname=nt
05-17 00:03 DEBUG  CommonBackend: language=en_US
05-17 00:03 DEBUG  CommonBackend: encoding=cp1252
05-17 00:03 DEBUG  WindowsBackend: arch=amd64
05-17 00:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\data\isolist.ini
05-17 00:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-17 00:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-17 00:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-17 00:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-17 00:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-17 00:03 DEBUG  WindowsBackend: Fetching host info...
05-17 00:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-17 00:03 DEBUG  WindowsBackend: windows version=vista
05-17 00:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-17 00:03 DEBUG  WindowsBackend: windows_sp=None
05-17 00:03 DEBUG  WindowsBackend: windows_build=7600
05-17 00:03 DEBUG  WindowsBackend: gmt=-8
05-17 00:03 DEBUG  WindowsBackend: country=US
05-17 00:03 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-17 00:03 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-17 00:03 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-17 00:03 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-17 00:03 DEBUG  WindowsBackend: windows_language_code=1033
05-17 00:03 DEBUG  WindowsBackend: windows_language=English
05-17 00:03 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-17 00:03 DEBUG  WindowsBackend: bootloader=vista
05-17 00:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153576.839844 mb free ntfs)
05-17 00:03 DEBUG  WindowsBackend: drive=Drive(C: hd 153576.839844 mb free ntfs)
05-17 00:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-17 00:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-17 00:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-17 00:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-17 00:03 DEBUG  WindowsBackend: keyboard_id=67699721
05-17 00:03 DEBUG  WindowsBackend: keyboard_layout=us
05-17 00:03 DEBUG  WindowsBackend: keyboard_variant=
05-17 00:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-17 00:03 DEBUG  CommonBackend: locale=en_US.UTF-8
05-17 00:03 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-17 00:03 DEBUG  CommonBackend: Searching ISOs on USB devices
05-17 00:03 DEBUG  CommonBackend: Searching for local CDs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu Netbook CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu Netbook CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Xubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Xubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Mythbuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Mythbuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 INFO   root: Already installed, running the uninstaller...
05-17 00:03 INFO   root: Running the uninstaller...
05-17 00:03 INFO   CommonBackend: This is the uninstaller running
05-17 00:03 DEBUG  WindowsFrontend: __init__...
05-17 00:03 DEBUG  WindowsFrontend: on_init...
05-17 00:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\translations, languages=['en_US', 'en']
05-17 00:03 INFO   root: Received settings
05-17 00:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\translations, languages=['en_US', 'en']
05-17 00:03 DEBUG  TaskList: # Running tasklist...
05-17 00:03 DEBUG  TaskList: ## Running Backup ISO...
05-17 00:03 DEBUG  TaskList: ## Finished Backup ISO
05-17 00:03 DEBUG  TaskList: ## Running Remove bootloader entry...
05-17 00:03 DEBUG  WindowsBackend: Could not find bcd id
05-17 00:03 DEBUG  WindowsBackend: undo_bootini C:
05-17 00:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 153576.839844 mb free ntfs)
05-17 00:03 DEBUG  TaskList: ## Finished Remove bootloader entry
05-17 00:03 DEBUG  TaskList: ## Running Remove target dir...
05-17 00:03 DEBUG  CommonBackend: Deleting C:\ubuntu
05-17 00:03 DEBUG  TaskList: ## Finished Remove target dir
05-17 00:03 DEBUG  TaskList: ## Running Remove registry key...
05-17 00:03 DEBUG  TaskList: ## Finished Remove registry key
05-17 00:03 DEBUG  TaskList: # Finished tasklist
05-17 00:03 INFO   root: Almost finished uninstalling
05-17 00:03 INFO   root: Finished uninstallation
05-17 00:03 DEBUG  CommonBackend: Fetching basic info...
05-17 00:03 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(3).exe
05-17 00:03 DEBUG  CommonBackend: platform=win32
05-17 00:03 DEBUG  CommonBackend: osname=nt
05-17 00:03 DEBUG  WindowsBackend: arch=amd64
05-17 00:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\data\isolist.ini
05-17 00:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-17 00:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-17 00:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-17 00:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-17 00:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-17 00:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-17 00:03 DEBUG  WindowsBackend: Fetching host info...
05-17 00:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-17 00:03 DEBUG  WindowsBackend: windows version=vista
05-17 00:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-17 00:03 DEBUG  WindowsBackend: windows_sp=None
05-17 00:03 DEBUG  WindowsBackend: windows_build=7600
05-17 00:03 DEBUG  WindowsBackend: gmt=-8
05-17 00:03 DEBUG  WindowsBackend: country=US
05-17 00:03 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-17 00:03 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-17 00:03 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-17 00:03 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-17 00:03 DEBUG  WindowsBackend: windows_language_code=1033
05-17 00:03 DEBUG  WindowsBackend: windows_language=English
05-17 00:03 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-17 00:03 DEBUG  WindowsBackend: bootloader=vista
05-17 00:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153578.34375 mb free ntfs)
05-17 00:03 DEBUG  WindowsBackend: drive=Drive(C: hd 153578.34375 mb free ntfs)
05-17 00:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-17 00:03 DEBUG  WindowsBackend: uninstaller_path=None
05-17 00:03 DEBUG  WindowsBackend: previous_target_dir=None
05-17 00:03 DEBUG  WindowsBackend: previous_distro_name=None
05-17 00:03 DEBUG  WindowsBackend: keyboard_id=67699721
05-17 00:03 DEBUG  WindowsBackend: keyboard_layout=us
05-17 00:03 DEBUG  WindowsBackend: keyboard_variant=
05-17 00:03 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-17 00:03 DEBUG  CommonBackend: Searching ISOs on USB devices
05-17 00:03 DEBUG  CommonBackend: Searching for local CDs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu Netbook CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu Netbook CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Xubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Xubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Mythbuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Mythbuntu CD
05-17 00:03 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:03 INFO   root: Running the installer...
05-17 00:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\translations, languages=['en_US', 'en']
05-17 00:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\translations, languages=['en_US', 'en']
05-17 00:04 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=21000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=u2rcrazy
05-17 00:04 INFO   root: Received settings
05-17 00:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\translations, languages=['en_US', 'en']
05-17 00:04 DEBUG  TaskList: # Running tasklist...
05-17 00:04 DEBUG  TaskList: ## Running select_target_dir...
05-17 00:04 INFO   WindowsBackend: Installing into C:\ubuntu
05-17 00:04 DEBUG  TaskList: ## Finished select_target_dir
05-17 00:04 DEBUG  TaskList: ## Running create_dir_structure...
05-17 00:04 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-17 00:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-17 00:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-17 00:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-17 00:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-17 00:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-17 00:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-17 00:04 DEBUG  TaskList: ## Finished create_dir_structure
05-17 00:04 DEBUG  TaskList: ## Running uncompress_target_dir...
05-17 00:04 DEBUG  TaskList: ## Finished uncompress_target_dir
05-17 00:04 DEBUG  TaskList: ## Running create_uninstaller...
05-17 00:04 DEBUG  WindowsBackend: Copying uninstaller C:\Users\u2rcrazy\Downloads\wubi(3).exe -> C:\ubuntu\uninstall-wubi.exe
05-17 00:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-17 00:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-17 00:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-17 00:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-17 00:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-17 00:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-17 00:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-17 00:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-17 00:04 DEBUG  TaskList: ## Finished create_uninstaller
05-17 00:04 DEBUG  TaskList: ## Running copy_installation_files...
05-17 00:04 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-17 00:04 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\winboot -> C:\ubuntu\winboot
05-17 00:04 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-17 00:04 DEBUG  TaskList: ## Finished copy_installation_files
05-17 00:04 DEBUG  TaskList: ## Running get_iso...
05-17 00:04 DEBUG  CommonBackend: Searching for local CD
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  CommonBackend: Searching for local ISO
05-17 00:04 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-17 00:04 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-17 00:04 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:04 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:04 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-17 00:04 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-17 00:04 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:04 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:04 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-17 00:04 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-17 00:04 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:04 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:04 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-17 00:04 DEBUG  TaskList: New task get_metalink
05-17 00:04 DEBUG  TaskList: ### Running get_metalink...
05-17 00:04 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > C:\ubuntu\install
05-17 00:04 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-17 00:04 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
05-17 00:04 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-17 00:04 DEBUG  TaskList: ### Finished get_metalink
05-17 00:04 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-17 00:04 DEBUG  TaskList: # Cancelling tasklist
05-17 00:04 DEBUG  TaskList: # Finished tasklist
05-17 00:04 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-17 00:04 INFO   root: === wubi 10.04 rev189 ===
05-17 00:04 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-17 00:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-17 00:04 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\data
05-17 00:04 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\bin\7z.exe
05-17 00:04 DEBUG  CommonBackend: Fetching basic info...
05-17 00:04 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-17 00:04 DEBUG  CommonBackend: platform=win32
05-17 00:04 DEBUG  CommonBackend: osname=nt
05-17 00:04 DEBUG  CommonBackend: language=en_US
05-17 00:04 DEBUG  CommonBackend: encoding=cp1252
05-17 00:04 DEBUG  WindowsBackend: arch=amd64
05-17 00:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\data\isolist.ini
05-17 00:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-17 00:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-17 00:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-17 00:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-17 00:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-17 00:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-17 00:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-17 00:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-17 00:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-17 00:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-17 00:04 DEBUG  WindowsBackend: Fetching host info...
05-17 00:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-17 00:04 DEBUG  WindowsBackend: windows version=vista
05-17 00:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-17 00:04 DEBUG  WindowsBackend: windows_sp=None
05-17 00:04 DEBUG  WindowsBackend: windows_build=7600
05-17 00:04 DEBUG  WindowsBackend: gmt=-8
05-17 00:04 DEBUG  WindowsBackend: country=US
05-17 00:04 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-17 00:04 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-17 00:04 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-17 00:04 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-17 00:04 DEBUG  WindowsBackend: windows_language_code=1033
05-17 00:04 DEBUG  WindowsBackend: windows_language=English
05-17 00:04 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-17 00:04 DEBUG  WindowsBackend: bootloader=vista
05-17 00:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153568.601563 mb free ntfs)
05-17 00:04 DEBUG  WindowsBackend: drive=Drive(C: hd 153568.601563 mb free ntfs)
05-17 00:04 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-17 00:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-17 00:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-17 00:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-17 00:04 DEBUG  WindowsBackend: keyboard_id=67699721
05-17 00:04 DEBUG  WindowsBackend: keyboard_layout=us
05-17 00:04 DEBUG  WindowsBackend: keyboard_variant=
05-17 00:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-17 00:04 DEBUG  CommonBackend: locale=en_US.UTF-8
05-17 00:04 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-17 00:04 DEBUG  CommonBackend: Searching ISOs on USB devices
05-17 00:04 DEBUG  CommonBackend: Searching for local CDs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Ubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Ubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Ubuntu Netbook CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Kubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Kubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Kubuntu Netbook CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Xubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Xubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Mythbuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp is a valid Mythbuntu CD
05-17 00:04 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:04 INFO   root: Running the uninstaller...
05-17 00:04 INFO   CommonBackend: This is the uninstaller running
05-17 00:04 DEBUG  WindowsFrontend: __init__...
05-17 00:04 DEBUG  WindowsFrontend: on_init...
05-17 00:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\translations, languages=['en_US', 'en']
05-17 00:04 INFO   root: Received settings
05-17 00:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\translations, languages=['en_US', 'en']
05-17 00:04 DEBUG  TaskList: # Running tasklist...
05-17 00:04 DEBUG  TaskList: ## Running Backup ISO...
05-17 00:04 DEBUG  TaskList: ## Finished Backup ISO
05-17 00:04 DEBUG  TaskList: ## Running Remove bootloader entry...
05-17 00:04 DEBUG  WindowsBackend: Could not find bcd id
05-17 00:04 DEBUG  WindowsBackend: undo_bootini C:
05-17 00:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 153568.601563 mb free ntfs)
05-17 00:04 DEBUG  TaskList: ## Finished Remove bootloader entry
05-17 00:04 DEBUG  TaskList: ## Running Remove target dir...
05-17 00:04 DEBUG  CommonBackend: Deleting C:\ubuntu
05-17 00:04 DEBUG  TaskList: ## Finished Remove target dir
05-17 00:04 DEBUG  TaskList: ## Running Remove registry key...
05-17 00:04 DEBUG  TaskList: ## Finished Remove registry key
05-17 00:04 DEBUG  TaskList: # Finished tasklist
05-17 00:04 INFO   root: Almost finished uninstalling
05-17 00:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylFDFD.tmp\translations, languages=['en_US', 'en']
05-17 00:04 INFO   root: Finished uninstallation
05-17 00:04 DEBUG  root: application.quit
05-17 00:04 DEBUG  WindowsFrontend: frontend.quit
05-17 00:04 DEBUG  WindowsFrontend: frontend.on_quit
05-17 00:04 DEBUG  root: application.on_quit
05-17 00:04 INFO   root: sys.exit
05-17 00:08 INFO   root: === wubi 10.04 rev189 ===
05-17 00:08 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-17 00:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\u2rcrazy\\Downloads\\wubi(4).exe"']
05-17 00:08 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\data
05-17 00:08 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\bin\7z.exe
05-17 00:08 DEBUG  CommonBackend: Fetching basic info...
05-17 00:08 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(4).exe
05-17 00:08 DEBUG  CommonBackend: platform=win32
05-17 00:08 DEBUG  CommonBackend: osname=nt
05-17 00:08 DEBUG  CommonBackend: language=en_US
05-17 00:08 DEBUG  CommonBackend: encoding=cp1252
05-17 00:08 DEBUG  WindowsBackend: arch=amd64
05-17 00:08 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\data\isolist.ini
05-17 00:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-17 00:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-17 00:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-17 00:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-17 00:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-17 00:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-17 00:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-17 00:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-17 00:08 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-17 00:08 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-17 00:08 DEBUG  WindowsBackend: Fetching host info...
05-17 00:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-17 00:08 DEBUG  WindowsBackend: windows version=vista
05-17 00:08 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-17 00:08 DEBUG  WindowsBackend: windows_sp=None
05-17 00:08 DEBUG  WindowsBackend: windows_build=7600
05-17 00:08 DEBUG  WindowsBackend: gmt=-8
05-17 00:08 DEBUG  WindowsBackend: country=US
05-17 00:08 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-17 00:08 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-17 00:08 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-17 00:08 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-17 00:08 DEBUG  WindowsBackend: windows_language_code=1033
05-17 00:08 DEBUG  WindowsBackend: windows_language=English
05-17 00:08 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-17 00:08 DEBUG  WindowsBackend: bootloader=vista
05-17 00:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153430.914063 mb free ntfs)
05-17 00:08 DEBUG  WindowsBackend: drive=Drive(C: hd 153430.914063 mb free ntfs)
05-17 00:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-17 00:08 DEBUG  WindowsBackend: uninstaller_path=None
05-17 00:08 DEBUG  WindowsBackend: previous_target_dir=None
05-17 00:08 DEBUG  WindowsBackend: previous_distro_name=None
05-17 00:08 DEBUG  WindowsBackend: keyboard_id=67699721
05-17 00:08 DEBUG  WindowsBackend: keyboard_layout=us
05-17 00:08 DEBUG  WindowsBackend: keyboard_variant=
05-17 00:08 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-17 00:08 DEBUG  CommonBackend: locale=en_US.UTF-8
05-17 00:08 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-17 00:08 DEBUG  CommonBackend: Searching ISOs on USB devices
05-17 00:08 DEBUG  CommonBackend: Searching for local CDs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Ubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Ubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Ubuntu Netbook CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Kubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Kubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Kubuntu Netbook CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Xubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Xubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Mythbuntu CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Mythbuntu CD
05-17 00:08 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-17 00:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:08 INFO   root: Running the installer...
05-17 00:08 DEBUG  WindowsFrontend: __init__...
05-17 00:08 DEBUG  WindowsFrontend: on_init...
05-17 00:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\translations, languages=['en_US', 'en']
05-17 00:08 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\translations, languages=['en_US', 'en']
05-17 00:09 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=u2rcrazy
05-17 00:09 INFO   root: Received settings
05-17 00:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\translations, languages=['en_US', 'en']
05-17 00:09 DEBUG  TaskList: # Running tasklist...
05-17 00:09 DEBUG  TaskList: ## Running select_target_dir...
05-17 00:09 INFO   WindowsBackend: Installing into C:\ubuntu
05-17 00:09 DEBUG  TaskList: ## Finished select_target_dir
05-17 00:09 DEBUG  TaskList: ## Running create_dir_structure...
05-17 00:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-17 00:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-17 00:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-17 00:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-17 00:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-17 00:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-17 00:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-17 00:09 DEBUG  TaskList: ## Finished create_dir_structure
05-17 00:09 DEBUG  TaskList: ## Running uncompress_target_dir...
05-17 00:09 DEBUG  TaskList: ## Finished uncompress_target_dir
05-17 00:09 DEBUG  TaskList: ## Running create_uninstaller...
05-17 00:09 DEBUG  WindowsBackend: Copying uninstaller C:\Users\u2rcrazy\Downloads\wubi(4).exe -> C:\ubuntu\uninstall-wubi.exe
05-17 00:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-17 00:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-17 00:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-17 00:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-17 00:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-17 00:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-17 00:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-17 00:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-17 00:09 DEBUG  TaskList: ## Finished create_uninstaller
05-17 00:09 DEBUG  TaskList: ## Running copy_installation_files...
05-17 00:09 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-17 00:09 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\winboot -> C:\ubuntu\winboot
05-17 00:09 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-17 00:09 DEBUG  TaskList: ## Finished copy_installation_files
05-17 00:09 DEBUG  TaskList: ## Running get_iso...
05-17 00:09 DEBUG  CommonBackend: Searching for local CD
05-17 00:09 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp is a valid Ubuntu CD
05-17 00:09 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylBE5E.tmp\casper\filesystem.squashfs
05-17 00:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-17 00:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-17 00:09 DEBUG  CommonBackend: Searching for local ISO
05-17 00:09 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-17 00:09 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-17 00:09 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:09 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:09 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-17 00:09 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-17 00:09 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:09 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:09 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-17 00:09 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-17 00:09 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-17 00:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-17 00:09 DEBUG  Distro: wrong version: 9.10 != 10.04
05-17 00:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-17 00:09 DEBUG  TaskList: New task get_metalink
05-17 00:09 DEBUG  TaskList: ### Running get_metalink...
05-17 00:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > C:\ubuntu\install
05-17 00:09 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-17 00:09 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
05-17 00:09 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-17 00:09 DEBUG  TaskList: ### Finished get_metalink
05-17 00:09 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-17 00:09 DEBUG  TaskList: # Cancelling tasklist
05-17 00:09 DEBUG  TaskList: # Finished tasklist
05-17 00:09 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-18 00:00 INFO   root: === wubi 10.04 rev189 ===
05-18 00:00 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-18 00:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-18 00:00 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\data
05-18 00:00 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\bin\7z.exe
05-18 00:00 DEBUG  CommonBackend: Fetching basic info...
05-18 00:00 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-18 00:00 DEBUG  CommonBackend: platform=win32
05-18 00:00 DEBUG  CommonBackend: osname=nt
05-18 00:00 DEBUG  CommonBackend: language=en_US
05-18 00:00 DEBUG  CommonBackend: encoding=cp1252
05-18 00:00 DEBUG  WindowsBackend: arch=amd64
05-18 00:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\data\isolist.ini
05-18 00:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 00:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 00:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 00:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 00:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 00:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 00:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 00:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 00:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-18 00:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 00:00 DEBUG  WindowsBackend: Fetching host info...
05-18 00:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 00:00 DEBUG  WindowsBackend: windows version=vista
05-18 00:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 00:00 DEBUG  WindowsBackend: windows_sp=None
05-18 00:00 DEBUG  WindowsBackend: windows_build=7600
05-18 00:00 DEBUG  WindowsBackend: gmt=-8
05-18 00:00 DEBUG  WindowsBackend: country=US
05-18 00:00 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-18 00:00 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-18 00:00 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-18 00:00 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-18 00:00 DEBUG  WindowsBackend: windows_language_code=1033
05-18 00:00 DEBUG  WindowsBackend: windows_language=English
05-18 00:00 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-18 00:00 DEBUG  WindowsBackend: bootloader=vista
05-18 00:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152976.460938 mb free ntfs)
05-18 00:00 DEBUG  WindowsBackend: drive=Drive(C: hd 152976.460938 mb free ntfs)
05-18 00:00 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-18 00:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-18 00:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-18 00:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-18 00:00 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 00:00 DEBUG  WindowsBackend: keyboard_layout=us
05-18 00:00 DEBUG  WindowsBackend: keyboard_variant=
05-18 00:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-18 00:00 DEBUG  CommonBackend: locale=en_US.UTF-8
05-18 00:00 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-18 00:00 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 00:00 DEBUG  CommonBackend: Searching for local CDs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Ubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Ubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Ubuntu Netbook CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Kubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Kubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Kubuntu Netbook CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Xubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Xubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Mythbuntu CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp is a valid Mythbuntu CD
05-18 00:00 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:00 INFO   root: Running the uninstaller...
05-18 00:00 INFO   CommonBackend: This is the uninstaller running
05-18 00:00 DEBUG  WindowsFrontend: __init__...
05-18 00:00 DEBUG  WindowsFrontend: on_init...
05-18 00:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\translations, languages=['en_US', 'en']
05-18 00:01 INFO   root: Received settings
05-18 00:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\translations, languages=['en_US', 'en']
05-18 00:01 DEBUG  TaskList: # Running tasklist...
05-18 00:01 DEBUG  TaskList: ## Running Backup ISO...
05-18 00:01 DEBUG  TaskList: ## Finished Backup ISO
05-18 00:01 DEBUG  TaskList: ## Running Remove bootloader entry...
05-18 00:01 DEBUG  WindowsBackend: Could not find bcd id
05-18 00:01 DEBUG  WindowsBackend: undo_bootini C:
05-18 00:01 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 152976.460938 mb free ntfs)
05-18 00:01 DEBUG  TaskList: ## Finished Remove bootloader entry
05-18 00:01 DEBUG  TaskList: ## Running Remove target dir...
05-18 00:01 DEBUG  CommonBackend: Deleting C:\ubuntu
05-18 00:01 DEBUG  TaskList: ## Finished Remove target dir
05-18 00:01 DEBUG  TaskList: ## Running Remove registry key...
05-18 00:01 DEBUG  TaskList: ## Finished Remove registry key
05-18 00:01 DEBUG  TaskList: # Finished tasklist
05-18 00:01 INFO   root: Almost finished uninstalling
05-18 00:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylD801.tmp\translations, languages=['en_US', 'en']
05-18 00:01 INFO   root: Finished uninstallation
05-18 00:01 DEBUG  root: application.quit
05-18 00:01 DEBUG  WindowsFrontend: frontend.quit
05-18 00:01 DEBUG  WindowsFrontend: frontend.on_quit
05-18 00:01 DEBUG  root: application.on_quit
05-18 00:01 INFO   root: sys.exit
05-18 00:48 INFO   root: === wubi 10.04 rev189 ===
05-18 00:48 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-18 00:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\u2rcrazy\\Downloads\\wubi(5).exe"']
05-18 00:48 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\data
05-18 00:48 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\bin\7z.exe
05-18 00:48 DEBUG  CommonBackend: Fetching basic info...
05-18 00:48 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(5).exe
05-18 00:48 DEBUG  CommonBackend: platform=win32
05-18 00:48 DEBUG  CommonBackend: osname=nt
05-18 00:48 DEBUG  CommonBackend: language=en_US
05-18 00:48 DEBUG  CommonBackend: encoding=cp1252
05-18 00:48 DEBUG  WindowsBackend: arch=amd64
05-18 00:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\data\isolist.ini
05-18 00:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 00:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 00:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 00:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 00:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 00:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 00:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 00:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 00:48 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-18 00:48 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 00:48 DEBUG  WindowsBackend: Fetching host info...
05-18 00:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 00:48 DEBUG  WindowsBackend: windows version=vista
05-18 00:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 00:48 DEBUG  WindowsBackend: windows_sp=None
05-18 00:48 DEBUG  WindowsBackend: windows_build=7600
05-18 00:48 DEBUG  WindowsBackend: gmt=-8
05-18 00:48 DEBUG  WindowsBackend: country=US
05-18 00:48 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-18 00:48 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-18 00:48 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-18 00:48 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-18 00:48 DEBUG  WindowsBackend: windows_language_code=1033
05-18 00:48 DEBUG  WindowsBackend: windows_language=English
05-18 00:48 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-18 00:48 DEBUG  WindowsBackend: bootloader=vista
05-18 00:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152607.75 mb free ntfs)
05-18 00:48 DEBUG  WindowsBackend: drive=Drive(C: hd 152607.75 mb free ntfs)
05-18 00:48 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-18 00:48 DEBUG  WindowsBackend: uninstaller_path=None
05-18 00:48 DEBUG  WindowsBackend: previous_target_dir=None
05-18 00:48 DEBUG  WindowsBackend: previous_distro_name=None
05-18 00:48 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 00:48 DEBUG  WindowsBackend: keyboard_layout=us
05-18 00:48 DEBUG  WindowsBackend: keyboard_variant=
05-18 00:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-18 00:48 DEBUG  CommonBackend: locale=en_US.UTF-8
05-18 00:48 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-18 00:48 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 00:48 DEBUG  CommonBackend: Searching for local CDs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Ubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Ubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Ubuntu Netbook CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Kubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Kubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Kubuntu Netbook CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Xubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Xubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Mythbuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Mythbuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 INFO   root: Running the installer...
05-18 00:48 DEBUG  WindowsFrontend: __init__...
05-18 00:48 DEBUG  WindowsFrontend: on_init...
05-18 00:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\translations, languages=['en_US', 'en']
05-18 00:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\translations, languages=['en_US', 'en']
05-18 00:48 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=u2rcrazy
05-18 00:48 INFO   root: Received settings
05-18 00:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\translations, languages=['en_US', 'en']
05-18 00:48 DEBUG  TaskList: # Running tasklist...
05-18 00:48 DEBUG  TaskList: ## Running select_target_dir...
05-18 00:48 INFO   WindowsBackend: Installing into C:\ubuntu
05-18 00:48 DEBUG  TaskList: ## Finished select_target_dir
05-18 00:48 DEBUG  TaskList: ## Running create_dir_structure...
05-18 00:48 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-18 00:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-18 00:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-18 00:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-18 00:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-18 00:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-18 00:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-18 00:48 DEBUG  TaskList: ## Finished create_dir_structure
05-18 00:48 DEBUG  TaskList: ## Running uncompress_target_dir...
05-18 00:48 DEBUG  TaskList: ## Finished uncompress_target_dir
05-18 00:48 DEBUG  TaskList: ## Running create_uninstaller...
05-18 00:48 DEBUG  WindowsBackend: Copying uninstaller C:\Users\u2rcrazy\Downloads\wubi(5).exe -> C:\ubuntu\uninstall-wubi.exe
05-18 00:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-18 00:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-18 00:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-18 00:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-18 00:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-18 00:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-18 00:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-18 00:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-18 00:48 DEBUG  TaskList: ## Finished create_uninstaller
05-18 00:48 DEBUG  TaskList: ## Running copy_installation_files...
05-18 00:48 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-18 00:48 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\winboot -> C:\ubuntu\winboot
05-18 00:48 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-18 00:48 DEBUG  TaskList: ## Finished copy_installation_files
05-18 00:48 DEBUG  TaskList: ## Running get_iso...
05-18 00:48 DEBUG  CommonBackend: Searching for local CD
05-18 00:48 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp is a valid Ubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl4499.tmp\casper\filesystem.squashfs
05-18 00:48 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:48 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:48 DEBUG  CommonBackend: Searching for local ISO
05-18 00:48 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-18 00:48 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-18 00:48 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-18 00:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-18 00:48 DEBUG  Distro: wrong version: 9.10 != 10.04
05-18 00:48 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-18 00:48 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-18 00:48 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-18 00:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-18 00:48 DEBUG  Distro: wrong version: 9.10 != 10.04
05-18 00:48 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-18 00:48 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-18 00:48 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-18 00:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-18 00:48 DEBUG  Distro: wrong version: 9.10 != 10.04
05-18 00:48 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-18 00:48 DEBUG  TaskList: New task get_metalink
05-18 00:48 DEBUG  TaskList: ### Running get_metalink...
05-18 00:48 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > C:\ubuntu\install
05-18 00:48 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-18 00:48 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
05-18 00:48 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-18 00:48 DEBUG  TaskList: ### Finished get_metalink
05-18 00:48 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-18 00:48 DEBUG  TaskList: # Cancelling tasklist
05-18 00:48 DEBUG  TaskList: # Finished tasklist
05-18 00:48 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-18 00:50 INFO   root: === wubi 10.04 rev189 ===
05-18 00:50 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-18 00:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\u2rcrazy\\Downloads\\wubi(5).exe"']
05-18 00:50 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\data
05-18 00:50 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\bin\7z.exe
05-18 00:50 DEBUG  CommonBackend: Fetching basic info...
05-18 00:50 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(5).exe
05-18 00:50 DEBUG  CommonBackend: platform=win32
05-18 00:50 DEBUG  CommonBackend: osname=nt
05-18 00:50 DEBUG  CommonBackend: language=en_US
05-18 00:50 DEBUG  CommonBackend: encoding=cp1252
05-18 00:50 DEBUG  WindowsBackend: arch=amd64
05-18 00:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\data\isolist.ini
05-18 00:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 00:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 00:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 00:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 00:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 00:50 DEBUG  WindowsBackend: Fetching host info...
05-18 00:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 00:50 DEBUG  WindowsBackend: windows version=vista
05-18 00:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 00:50 DEBUG  WindowsBackend: windows_sp=None
05-18 00:50 DEBUG  WindowsBackend: windows_build=7600
05-18 00:50 DEBUG  WindowsBackend: gmt=-8
05-18 00:50 DEBUG  WindowsBackend: country=US
05-18 00:50 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-18 00:50 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-18 00:50 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-18 00:50 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-18 00:50 DEBUG  WindowsBackend: windows_language_code=1033
05-18 00:50 DEBUG  WindowsBackend: windows_language=English
05-18 00:50 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-18 00:50 DEBUG  WindowsBackend: bootloader=vista
05-18 00:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152610.097656 mb free ntfs)
05-18 00:50 DEBUG  WindowsBackend: drive=Drive(C: hd 152610.097656 mb free ntfs)
05-18 00:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-18 00:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-18 00:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-18 00:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-18 00:50 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 00:50 DEBUG  WindowsBackend: keyboard_layout=us
05-18 00:50 DEBUG  WindowsBackend: keyboard_variant=
05-18 00:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-18 00:50 DEBUG  CommonBackend: locale=en_US.UTF-8
05-18 00:50 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-18 00:50 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 00:50 DEBUG  CommonBackend: Searching for local CDs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Ubuntu Netbook CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Kubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Kubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Kubuntu Netbook CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Xubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Xubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Mythbuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Mythbuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 INFO   root: Already installed, running the uninstaller...
05-18 00:50 INFO   root: Running the uninstaller...
05-18 00:50 INFO   CommonBackend: This is the uninstaller running
05-18 00:50 DEBUG  WindowsFrontend: __init__...
05-18 00:50 DEBUG  WindowsFrontend: on_init...
05-18 00:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\translations, languages=['en_US', 'en']
05-18 00:50 INFO   root: Received settings
05-18 00:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\translations, languages=['en_US', 'en']
05-18 00:50 DEBUG  TaskList: # Running tasklist...
05-18 00:50 DEBUG  TaskList: ## Running Backup ISO...
05-18 00:50 DEBUG  TaskList: ## Finished Backup ISO
05-18 00:50 DEBUG  TaskList: ## Running Remove bootloader entry...
05-18 00:50 DEBUG  WindowsBackend: Could not find bcd id
05-18 00:50 DEBUG  WindowsBackend: undo_bootini C:
05-18 00:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 152610.097656 mb free ntfs)
05-18 00:50 DEBUG  TaskList: ## Finished Remove bootloader entry
05-18 00:50 DEBUG  TaskList: ## Running Remove target dir...
05-18 00:50 DEBUG  CommonBackend: Deleting C:\ubuntu
05-18 00:50 DEBUG  TaskList: ## Finished Remove target dir
05-18 00:50 DEBUG  TaskList: ## Running Remove registry key...
05-18 00:50 DEBUG  TaskList: ## Finished Remove registry key
05-18 00:50 DEBUG  TaskList: # Finished tasklist
05-18 00:50 INFO   root: Almost finished uninstalling
05-18 00:50 INFO   root: Finished uninstallation
05-18 00:50 DEBUG  CommonBackend: Fetching basic info...
05-18 00:50 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(5).exe
05-18 00:50 DEBUG  CommonBackend: platform=win32
05-18 00:50 DEBUG  CommonBackend: osname=nt
05-18 00:50 DEBUG  WindowsBackend: arch=amd64
05-18 00:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\data\isolist.ini
05-18 00:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 00:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 00:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 00:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 00:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-18 00:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 00:50 DEBUG  WindowsBackend: Fetching host info...
05-18 00:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 00:50 DEBUG  WindowsBackend: windows version=vista
05-18 00:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 00:50 DEBUG  WindowsBackend: windows_sp=None
05-18 00:50 DEBUG  WindowsBackend: windows_build=7600
05-18 00:50 DEBUG  WindowsBackend: gmt=-8
05-18 00:50 DEBUG  WindowsBackend: country=US
05-18 00:50 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-18 00:50 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-18 00:50 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-18 00:50 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-18 00:50 DEBUG  WindowsBackend: windows_language_code=1033
05-18 00:50 DEBUG  WindowsBackend: windows_language=English
05-18 00:50 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-18 00:50 DEBUG  WindowsBackend: bootloader=vista
05-18 00:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152611.601563 mb free ntfs)
05-18 00:50 DEBUG  WindowsBackend: drive=Drive(C: hd 152611.601563 mb free ntfs)
05-18 00:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-18 00:50 DEBUG  WindowsBackend: uninstaller_path=None
05-18 00:50 DEBUG  WindowsBackend: previous_target_dir=None
05-18 00:50 DEBUG  WindowsBackend: previous_distro_name=None
05-18 00:50 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 00:50 DEBUG  WindowsBackend: keyboard_layout=us
05-18 00:50 DEBUG  WindowsBackend: keyboard_variant=
05-18 00:50 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-18 00:50 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 00:50 DEBUG  CommonBackend: Searching for local CDs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Ubuntu Netbook CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Kubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Kubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Kubuntu Netbook CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Xubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Xubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Mythbuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Mythbuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 INFO   root: Running the installer...
05-18 00:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\translations, languages=['en_US', 'en']
05-18 00:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\translations, languages=['en_US', 'en']
05-18 00:50 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=u2rcrazy
05-18 00:50 INFO   root: Received settings
05-18 00:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\translations, languages=['en_US', 'en']
05-18 00:50 DEBUG  TaskList: # Running tasklist...
05-18 00:50 DEBUG  TaskList: ## Running select_target_dir...
05-18 00:50 INFO   WindowsBackend: Installing into C:\ubuntu
05-18 00:50 DEBUG  TaskList: ## Finished select_target_dir
05-18 00:50 DEBUG  TaskList: ## Running create_dir_structure...
05-18 00:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-18 00:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-18 00:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-18 00:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-18 00:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-18 00:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-18 00:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-18 00:50 DEBUG  TaskList: ## Finished create_dir_structure
05-18 00:50 DEBUG  TaskList: ## Running uncompress_target_dir...
05-18 00:50 DEBUG  TaskList: ## Finished uncompress_target_dir
05-18 00:50 DEBUG  TaskList: ## Running create_uninstaller...
05-18 00:50 DEBUG  WindowsBackend: Copying uninstaller C:\Users\u2rcrazy\Downloads\wubi(5).exe -> C:\ubuntu\uninstall-wubi.exe
05-18 00:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-18 00:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-18 00:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-18 00:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-18 00:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-18 00:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-18 00:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-18 00:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-18 00:50 DEBUG  TaskList: ## Finished create_uninstaller
05-18 00:50 DEBUG  TaskList: ## Running copy_installation_files...
05-18 00:50 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-18 00:50 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\winboot -> C:\ubuntu\winboot
05-18 00:50 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-18 00:50 DEBUG  TaskList: ## Finished copy_installation_files
05-18 00:50 DEBUG  TaskList: ## Running get_iso...
05-18 00:50 DEBUG  CommonBackend: Searching for local CD
05-18 00:50 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylA0A.tmp\casper\filesystem.squashfs
05-18 00:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:50 DEBUG  CommonBackend: Searching for local ISO
05-18 00:50 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-18 00:50 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-18 00:50 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-18 00:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-18 00:50 DEBUG  Distro: wrong version: 9.10 != 10.04
05-18 00:50 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-18 00:50 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-18 00:50 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-18 00:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-18 00:50 DEBUG  Distro: wrong version: 9.10 != 10.04
05-18 00:50 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-18 00:50 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-18 00:50 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-18 00:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-18 00:50 DEBUG  Distro: wrong version: 9.10 != 10.04
05-18 00:50 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-18 00:50 DEBUG  TaskList: New task get_metalink
05-18 00:50 DEBUG  TaskList: ### Running get_metalink...
05-18 00:50 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > C:\ubuntu\install
05-18 00:50 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-18 00:50 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
05-18 00:50 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-18 00:50 DEBUG  TaskList: ### Finished get_metalink
05-18 00:50 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-18 00:50 DEBUG  TaskList: # Cancelling tasklist
05-18 00:50 DEBUG  TaskList: # Finished tasklist
05-18 00:50 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-18 00:54 INFO   root: === wubi 10.04 rev189 ===
05-18 00:54 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-18 00:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\u2rcrazy\\Downloads\\wubi(5).exe"']
05-18 00:54 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\data
05-18 00:54 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\bin\7z.exe
05-18 00:54 DEBUG  CommonBackend: Fetching basic info...
05-18 00:54 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(5).exe
05-18 00:54 DEBUG  CommonBackend: platform=win32
05-18 00:54 DEBUG  CommonBackend: osname=nt
05-18 00:54 DEBUG  CommonBackend: language=en_US
05-18 00:54 DEBUG  CommonBackend: encoding=cp1252
05-18 00:54 DEBUG  WindowsBackend: arch=amd64
05-18 00:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\data\isolist.ini
05-18 00:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 00:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 00:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 00:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 00:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 00:54 DEBUG  WindowsBackend: Fetching host info...
05-18 00:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 00:54 DEBUG  WindowsBackend: windows version=vista
05-18 00:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 00:54 DEBUG  WindowsBackend: windows_sp=None
05-18 00:54 DEBUG  WindowsBackend: windows_build=7600
05-18 00:54 DEBUG  WindowsBackend: gmt=-8
05-18 00:54 DEBUG  WindowsBackend: country=US
05-18 00:54 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-18 00:54 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-18 00:54 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-18 00:54 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-18 00:54 DEBUG  WindowsBackend: windows_language_code=1033
05-18 00:54 DEBUG  WindowsBackend: windows_language=English
05-18 00:54 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-18 00:54 DEBUG  WindowsBackend: bootloader=vista
05-18 00:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152609.261719 mb free ntfs)
05-18 00:54 DEBUG  WindowsBackend: drive=Drive(C: hd 152609.261719 mb free ntfs)
05-18 00:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-18 00:54 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-18 00:54 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-18 00:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-18 00:54 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 00:54 DEBUG  WindowsBackend: keyboard_layout=us
05-18 00:54 DEBUG  WindowsBackend: keyboard_variant=
05-18 00:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-18 00:54 DEBUG  CommonBackend: locale=en_US.UTF-8
05-18 00:54 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-18 00:54 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 00:54 DEBUG  CommonBackend: Searching for local CDs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Ubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Ubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Ubuntu Netbook CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Kubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Kubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Kubuntu Netbook CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Xubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Xubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Mythbuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Mythbuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 INFO   root: Already installed, running the uninstaller...
05-18 00:54 INFO   root: Running the uninstaller...
05-18 00:54 INFO   CommonBackend: This is the uninstaller running
05-18 00:54 DEBUG  WindowsFrontend: __init__...
05-18 00:54 DEBUG  WindowsFrontend: on_init...
05-18 00:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\translations, languages=['en_US', 'en']
05-18 00:54 INFO   root: Received settings
05-18 00:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\translations, languages=['en_US', 'en']
05-18 00:54 DEBUG  TaskList: # Running tasklist...
05-18 00:54 DEBUG  TaskList: ## Running Backup ISO...
05-18 00:54 DEBUG  TaskList: ## Finished Backup ISO
05-18 00:54 DEBUG  TaskList: ## Running Remove bootloader entry...
05-18 00:54 DEBUG  WindowsBackend: Could not find bcd id
05-18 00:54 DEBUG  WindowsBackend: undo_bootini C:
05-18 00:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 152609.261719 mb free ntfs)
05-18 00:54 DEBUG  TaskList: ## Finished Remove bootloader entry
05-18 00:54 DEBUG  TaskList: ## Running Remove target dir...
05-18 00:54 DEBUG  CommonBackend: Deleting C:\ubuntu
05-18 00:54 DEBUG  TaskList: ## Finished Remove target dir
05-18 00:54 DEBUG  TaskList: ## Running Remove registry key...
05-18 00:54 DEBUG  TaskList: ## Finished Remove registry key
05-18 00:54 DEBUG  TaskList: # Finished tasklist
05-18 00:54 INFO   root: Almost finished uninstalling
05-18 00:54 INFO   root: Finished uninstallation
05-18 00:54 DEBUG  CommonBackend: Fetching basic info...
05-18 00:54 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(5).exe
05-18 00:54 DEBUG  CommonBackend: platform=win32
05-18 00:54 DEBUG  CommonBackend: osname=nt
05-18 00:54 DEBUG  WindowsBackend: arch=amd64
05-18 00:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\data\isolist.ini
05-18 00:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 00:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 00:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 00:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 00:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-18 00:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 00:54 DEBUG  WindowsBackend: Fetching host info...
05-18 00:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 00:54 DEBUG  WindowsBackend: windows version=vista
05-18 00:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 00:54 DEBUG  WindowsBackend: windows_sp=None
05-18 00:54 DEBUG  WindowsBackend: windows_build=7600
05-18 00:54 DEBUG  WindowsBackend: gmt=-8
05-18 00:54 DEBUG  WindowsBackend: country=US
05-18 00:54 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-18 00:54 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-18 00:54 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-18 00:54 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-18 00:54 DEBUG  WindowsBackend: windows_language_code=1033
05-18 00:54 DEBUG  WindowsBackend: windows_language=English
05-18 00:54 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-18 00:54 DEBUG  WindowsBackend: bootloader=vista
05-18 00:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 152610.765625 mb free ntfs)
05-18 00:54 DEBUG  WindowsBackend: drive=Drive(C: hd 152610.765625 mb free ntfs)
05-18 00:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-18 00:54 DEBUG  WindowsBackend: uninstaller_path=None
05-18 00:54 DEBUG  WindowsBackend: previous_target_dir=None
05-18 00:54 DEBUG  WindowsBackend: previous_distro_name=None
05-18 00:54 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 00:54 DEBUG  WindowsBackend: keyboard_layout=us
05-18 00:54 DEBUG  WindowsBackend: keyboard_variant=
05-18 00:54 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-18 00:54 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 00:54 DEBUG  CommonBackend: Searching for local CDs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Ubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Ubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Ubuntu Netbook CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Kubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Kubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Kubuntu Netbook CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Xubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Xubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Mythbuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp is a valid Mythbuntu CD
05-18 00:54 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 00:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 00:54 INFO   root: Running the installer...
05-18 00:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\translations, languages=['en_US', 'en']
05-18 00:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pyl2CC6.tmp\translations, languages=['en_US', 'en']
05-18 00:54 INFO   WindowsFrontend: Operation cancelled
05-18 00:54 DEBUG  WindowsFrontend: frontend.quit
05-18 00:54 DEBUG  WindowsFrontend: frontend.on_quit
05-18 00:54 DEBUG  root: application.on_quit
05-18 00:54 INFO   root: sys.exit
05-24 02:06 INFO   root: === wubi 10.04 rev189 ===
05-24 02:06 DEBUG  root: Logfile is c:\users\u2rcrazy\appdata\local\temp\wubi-10.04-rev189.log
05-24 02:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\u2rcrazy\\Downloads\\wubi(6).exe"']
05-24 02:06 DEBUG  CommonBackend: data_dir=C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\data
05-24 02:06 DEBUG  WindowsBackend: 7z=C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\bin\7z.exe
05-24 02:06 DEBUG  CommonBackend: Fetching basic info...
05-24 02:06 DEBUG  CommonBackend: original_exe=C:\Users\u2rcrazy\Downloads\wubi(6).exe
05-24 02:06 DEBUG  CommonBackend: platform=win32
05-24 02:06 DEBUG  CommonBackend: osname=nt
05-24 02:06 DEBUG  CommonBackend: language=en_US
05-24 02:06 DEBUG  CommonBackend: encoding=cp1252
05-24 02:06 DEBUG  WindowsBackend: arch=amd64
05-24 02:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\data\isolist.ini
05-24 02:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 02:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 02:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 02:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 02:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 02:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 02:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 02:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 02:06 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
05-24 02:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-24 02:06 DEBUG  WindowsBackend: Fetching host info...
05-24 02:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 02:06 DEBUG  WindowsBackend: windows version=vista
05-24 02:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-24 02:06 DEBUG  WindowsBackend: windows_sp=None
05-24 02:06 DEBUG  WindowsBackend: windows_build=7600
05-24 02:06 DEBUG  WindowsBackend: gmt=-8
05-24 02:06 DEBUG  WindowsBackend: country=US
05-24 02:06 DEBUG  WindowsBackend: timezone=America/Los_Angeles
05-24 02:06 DEBUG  WindowsBackend: windows_username=u2rcrazy
05-24 02:06 DEBUG  WindowsBackend: user_full_name=u2rcrazy
05-24 02:06 DEBUG  WindowsBackend: user_directory=C:\Users\u2rcrazy
05-24 02:06 DEBUG  WindowsBackend: windows_language_code=1033
05-24 02:06 DEBUG  WindowsBackend: windows_language=English
05-24 02:06 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) II Dual-Core Mobile M520
05-24 02:06 DEBUG  WindowsBackend: bootloader=vista
05-24 02:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 153322.109375 mb free ntfs)
05-24 02:06 DEBUG  WindowsBackend: drive=Drive(C: hd 153322.109375 mb free ntfs)
05-24 02:06 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-24 02:06 DEBUG  WindowsBackend: uninstaller_path=None
05-24 02:06 DEBUG  WindowsBackend: previous_target_dir=None
05-24 02:06 DEBUG  WindowsBackend: previous_distro_name=None
05-24 02:06 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 02:06 DEBUG  WindowsBackend: keyboard_layout=us
05-24 02:06 DEBUG  WindowsBackend: keyboard_variant=
05-24 02:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 02:06 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 02:06 DEBUG  WindowsBackend: total_memory_mb=3838.359375
05-24 02:06 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 02:06 DEBUG  CommonBackend: Searching for local CDs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Ubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Ubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Ubuntu Netbook CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Kubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Kubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Kubuntu Netbook CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Xubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Xubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Mythbuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Mythbuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 INFO   root: Running the installer...
05-24 02:06 DEBUG  WindowsFrontend: __init__...
05-24 02:06 DEBUG  WindowsFrontend: on_init...
05-24 02:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\translations, languages=['en_US', 'en']
05-24 02:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\translations, languages=['en_US', 'en']
05-24 02:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=u2rcrazy
05-24 02:06 INFO   root: Received settings
05-24 02:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\translations, languages=['en_US', 'en']
05-24 02:06 DEBUG  TaskList: # Running tasklist...
05-24 02:06 DEBUG  TaskList: ## Running select_target_dir...
05-24 02:06 INFO   WindowsBackend: Installing into C:\ubuntu
05-24 02:06 DEBUG  TaskList: ## Finished select_target_dir
05-24 02:06 DEBUG  TaskList: ## Running create_dir_structure...
05-24 02:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-24 02:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-24 02:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-24 02:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-24 02:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-24 02:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-24 02:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-24 02:06 DEBUG  TaskList: ## Finished create_dir_structure
05-24 02:06 DEBUG  TaskList: ## Running uncompress_target_dir...
05-24 02:06 DEBUG  TaskList: ## Finished uncompress_target_dir
05-24 02:06 DEBUG  TaskList: ## Running create_uninstaller...
05-24 02:06 DEBUG  WindowsBackend: Copying uninstaller C:\Users\u2rcrazy\Downloads\wubi(6).exe -> C:\ubuntu\uninstall-wubi.exe
05-24 02:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-24 02:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-24 02:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-24 02:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-24 02:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
05-24 02:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-24 02:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-24 02:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-24 02:06 DEBUG  TaskList: ## Finished create_uninstaller
05-24 02:06 DEBUG  TaskList: ## Running copy_installation_files...
05-24 02:06 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-24 02:06 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\winboot -> C:\ubuntu\winboot
05-24 02:06 DEBUG  WindowsBackend: Copying C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-24 02:06 DEBUG  TaskList: ## Finished copy_installation_files
05-24 02:06 DEBUG  TaskList: ## Running get_iso...
05-24 02:06 DEBUG  CommonBackend: Searching for local CD
05-24 02:06 DEBUG  Distro:   checking whether C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp is a valid Ubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain C:\Users\u2rcrazy\AppData\Local\Temp\pylE212.tmp\casper\filesystem.squashfs
05-24 02:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 02:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 02:06 DEBUG  CommonBackend: Searching for local ISO
05-24 02:06 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-24 02:06 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(2).iso
05-24 02:06 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-24 02:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-24 02:06 DEBUG  Distro: wrong version: 9.10 != 10.04
05-24 02:06 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-24 02:06 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386(3).iso
05-24 02:06 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-24 02:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-24 02:06 DEBUG  Distro: wrong version: 9.10 != 10.04
05-24 02:06 DEBUG  Distro:   checking Ubuntu ISO C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-24 02:06 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\u2rcrazy\Downloads\ubuntu-9.10-desktop-i386.iso
05-24 02:06 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
05-24 02:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}
05-24 02:06 DEBUG  Distro: wrong version: 9.10 != 10.04
05-24 02:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-24 02:06 DEBUG  TaskList: New task get_metalink
05-24 02:06 DEBUG  TaskList: ### Running get_metalink...
05-24 02:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > C:\ubuntu\install
05-24 02:06 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-24 02:06 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
05-24 02:06 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
05-24 02:06 DEBUG  TaskList: ### Finished get_metalink
05-24 02:06 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
05-24 02:06 DEBUG  TaskList: # Cancelling tasklist
05-24 02:06 DEBUG  TaskList: # Finished tasklist
05-24 02:06 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO

[/INDENT]

---

### Post by u2rcrazy on 2010-05-24
darkod,


[LIST=1]
[*]You said:  > **darkod said:**
> I suggest you download the 10.04 image, burn a cd with it and install like that.

I would like to have a dual boot system with separate partitions of Windows 7 64 bit and Ubuntu 10.04 64 bit.  I have the Windows 7 restore DVD copies of the system I made when I bought my computer and I believe I can download and make a CD-Rom copy of Ubuntu just fine.  I don't know how to make two partitions on my computer and tell each OS to go onto said partition.  What are your thoughts?
[*] You said:  > **darkod said:**
> If you still want to install wubi, again downloading the image should  work because wubi.exe is included on it. But to save you waiting for  wubi to download the files, just extract the wubi.exe from the ISO and  put both the ISO and wubi.exe in a same folder. Then when you start  wubi.exe it will use the ISO, not downloading over the internet.

Although I agrea with you that it would be better to create two partitions on my drive to install each OS on, can you elaborate on how to perform this further?  This will grow my understanding and help some that wish to continue with the "[Ubuntu installer  for Windows]("http://www.ubuntu.com/getubuntu/download-wubi")" install method.
[/LIST]

Thanks for your assistance.  :P

---

### Post by darkod on 2010-05-24
> **u2rcrazy said:**
> darkod,


[LIST=1]
[*]You said:  

I would like to have a dual boot system with separate partitions of Windows 7 64 bit and Ubuntu 10.04 64 bit.  I have the Windows 7 restore DVD copies of the system I made when I bought my computer and I believe I can download and make a CD-Rom copy of Ubuntu just fine.  I don't know how to make two partitions on my computer and tell each OS to go onto said partition.  What are your thoughts?
[*] You said:  

Although I agrea with you that it would be better to create two partitions on my drive to install each OS on, can you elaborate on how to perform this further?  This will grow my understanding and help some that wish to continue with the "[Ubuntu installer  for Windows]("http://www.ubuntu.com/getubuntu/download-wubi")" install method.
[/LIST]

Thanks for your assistance.  :P

It's not difficult at all. At this moment I guess win7 is taking the whole hdd. Because this is your first time installing like this, I think the easiest way is:

First decide how much space you want to give to ubuntu, and how much to keep for win7. If you don't save large files like videos, music, photos in ubuntu, it needs about 15GB of space (even better 25GB or 30GB). The more large files you plan to keep there, you have to give it more space. After you have decided this:
1. Boot win7 and use Disk Management to shrink the win7 partition to the size you decided to keep for win7. Leave the unallocated space that will be created as unallocated, do NOT create any partitions in it. After that boot win7 few times to let it do its disk checks.
2. Then boot with the ubuntu cd, start the installer and in step 4 select Use Largest Available Free space option. That will install ubuntu inside the unallocated space you left, creating a standard install with root + swap partitions. And that's it.

Later on when you get more experience, you can try other stuff, like separate /home partition, manually partitioning during install, etc.

---

### Post by u2rcrazy on 2010-05-24
darkod,

Thanks for the great info.  :)    This makes sense.  I'm glad I'll be able to resize my drives' partition within Windows 7 and don't have to do it with a third party tool.  I have a couple more questions.


[LIST=1]
[*]Once I finish, will I be able to choose which OS will load and also the default OS?
[*]Is it possible to create a third partition that I can have as my "large" partition for videos, music and such that both Ubuntu and Windows will be able to read and write to?  I was thinking I would just leave enough space on the OS partitions for the respected OS, programs, drivers and future additions, etc. and save the "large", third partition for my personal documents, music, videos, downloads, etc.
[/LIST]
What do you think?  Thanks again!:popcorn:

---

### Post by darkod on 2010-05-24
> **u2rcrazy said:**
> darkod,

Thanks for the great info.  :)    This makes sense.  I'm glad I'll be able to resize my drives' partition within Windows 7 and don't have to do it with a third party tool.  I have a couple more questions.


[LIST=1]
[*]Once I finish, will I be able to choose which OS will load and also the default OS?
[*]Is it possible to create a third partition that I can have as my "large" partition for videos, music and such that both Ubuntu and Windows will be able to read and write to?  I was thinking I would just leave enough space on the OS partitions for the respected OS, programs, drivers and future additions, etc. and save the "large", third partition for my personal documents, music, videos, downloads, etc.
[/LIST]
What do you think?  Thanks again!:popcorn:

Yes, you will get the grub2 menu at boot where you can select which OS you want to boot. And also which will be the default OS and the timeout how long menu to be shown before the default entry is booted if nothing is pressed.

The idea about common ntfs partition is very good. Actually, that is the setup I have, and because all large files will be on that partition then you don't need large space for ubuntu. Personally, I also have separate /home partition which makes it easier to do clean installs, but that's not necessary for you to do, not right now.
The common data partition has to be ntfs so both windows and ubuntu can see it.
If it helps you, here is how I have my 250GB hdd split up:

/dev/sda1 primary 65GB ntfs win7 system C:
/dev/sda2 primary 141GB ntfs data D:
/dev/sda3 primary 15GB ext4 /

/dev/sda5 logical 2GB swap
/dev/sda6 logical 10GB ext4 /home

The logical partitions in linux always start to be counted from 5 and above. If you also plan separate /home, you will have to use manual partitioning in the ubuntu installer. The guided methods create only / + swap.

---

### Post by ronnielsen1 on 2010-05-24
Good advice. Good luck. Don't underestimate the size you want to give Ubuntu. You have a tendency to want more but it's easy to add once you figure it out

---

### Post by u2rcrazy on 2010-05-25
darkod,

Thanks for the explanation.  :P    You where correct when you said, 

> **darkod said:**
> The idea about common ntfs partition is very good. Actually, that is the setup I have, and because all large files will be on that partition then you don't need large space for ubuntu. Personally, I also have separate /home partition which makes it easier to do clean installs, but that's not necessary for you to do, not right now.

That's exactly what I was thinking:)   I did it with a Win98 about ten years ago and it was really convenient in case I need to do a reformat and reinstall of the OS.


Darkod, you also gave me a blueprint on how you set up your system as notated below.

> **darkod said:**
> /dev/sda1 primary 65GB ntfs win7 system C:
/dev/sda2 primary 141GB ntfs data D:
/dev/sda3 primary 15GB ext4 /

/dev/sda5 logical 2GB swap
/dev/sda6 logical 10GB ext4 /home

I understand some of what you stated.  

[LIST]
[*]You have 6 drives, correct?
[*]I thought that a drive has a primary and secondary drive, and that the secondary drive can be split into many different logical drives.  Am I correct or am I confusing this with Fat32?
[*]The following is how I understand the use of each drive:
[LIST=1]
[*]Win7
[*]My personal data
[*]I don't understand what should go here
[*]Is there a 4th drive?  I didn't see any information
[*]I don't understand what a swap drive is.  Can you explain in more detail what the purpose of it is?
[*]I think this is the Ubuntu/Linux drive as you stated /home.  Am I right?
[/LIST]
[*]Here is a screen shot of what my Disk management looks like know.  I'm  not quite sure what these other two partitions (1st @ 1.46GB and 4th @  8.93GB) are doing here (see attachment).

darkod, I was thinking of having three drives for my Win7, Ubuntu, and my personal date.  Can I have 3 drives or do I need to have at least 5 drives for Ubuntu to function?  I didn't quite understand what you said about needing to have 5 drives here, > **darkod said:**
> The logical partitions in Linux always start to be counted from 5 and  above. If you also plan separate /home, you will have to use manual  partitioning in the ubuntu installer. The guided methods create only / +  swap.
[*]When I attempt to install Ubuntu onto the Unallocated space you stated I should, > 2. Then boot with the ubuntu cd, start the installer and in step 4  select Use Largest Available Free space option. That will install ubuntu  inside the unallocated space you left, creating a standard install with  root + swap partitions. And that's it.  Once I've used the entire unallocated space and installed Ubuntu, can I plit it up and use the 2nd have as storage for my personal date?  I would like to move my personal date from C: and then shrink C: and add that extra space to the new logical drive created after the Ubuntu system drive.  Did I make sense on what my goals are?
[/LIST]
 Thank for your help.  let me know if you need me to clarify anything for you.  Have a great day and thanks for your help again!!:guitar:

---

### Post by darkod on 2010-05-25
The main partition where the ubuntu system is installed is called root, and marked with /
This is the same like C: in windows.
Your personal files and settings are saved in your Home folder. That folder can be a folder in the / partition, but it can also be a partition on its own which is then marked as mount point /home. In that case it is independent from / and during reinstall you can keep it easily.
Like you said yourself, when having second data partition in windows, you can format C: and reinstall at any time, you still keep your files from D:. This is the same.

The swap partition is space temporarily used if the ram memory gets full. In windows you have a file called swap file, in linux you usually have a partition (although you can also have just a file).

From your Disk Management screenshot, you need to think first whether you want to shrink C:. Right now it is 200GB but if you plan to have common ntfs partition for data, I guess it's better to shrink C: and make the common partition as large as possible.

If you want to keep C: as 200GB that's still fine. The unallocated space is enough for installation of ubuntu.

---

### Post by rob45 on 2010-05-26
Hi just like to say that i had some problems downloading using wubi.....similar error...access denied....i think it was down to my firewall...zonealarm....unloaded zonealarm,and the installation went through no problems.

So have you got a firewall?If so unload it and try again.

---

### Post by u2rcrazy on 2010-05-28
Darko,

Thanks for sharing.  I have gone over your posts and tried to implement what we talked about.  Since we talked I did shrink my C partition down with left a large Unallocated Partition.  I booted up using the Ubuntu 10.04 64bit disk and had it take that unused space.  I then went back into Disk Manager and thought I could shrink Ubuntu's Partition, but couldn't.  I decided to delete Ubuntu's Partition and go back into Windows 7 and start over.  I tried to reboot in and the system could reboot so I decided to restore Windows 7.  I'm basically back to where I was, and still unclear on how I can achieve this.

How can I implement the following dual boot system with the following  partition setup?

[LIST=1]
[*]Windows 7      (with a little extra space for growth)
65GB as suggested
[*]Ubuntu 10.04   (with a little extra space for growth)
10GB as suggested
[*]Partition for my personal data storage
As large as I can get  
*I'll keep all my data here in case I need to do another restore and so  each OS can access this information*
[/LIST]
NOTE:  I don't know what to do with these other two partitions  (i.e., 1st @ 1.46GB or 3rd @ 8.93)

I feel totally lost and stupid:(  

Bob

---

