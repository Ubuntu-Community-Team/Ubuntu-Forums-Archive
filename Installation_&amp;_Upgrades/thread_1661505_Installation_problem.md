---
title: "Installation problem"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by pumber on 2011-01-06
I got the following error 

> An error occoured. Permission denied. For more information, please see the log file.

The following is the log file. I am running WinXP prof and trying to install wubi.

> 01-06 19:04 INFO   root: === wubi 10.10 rev197 ===
01-06 19:04 DEBUG  root: Logfile is r:\temp\wubi-10.10-rev197.log
01-06 19:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"']
01-06 19:04 DEBUG  CommonBackend: data_dir=r:\temp\pyl4.tmp\data
01-06 19:04 DEBUG  WindowsBackend: 7z=r:\temp\pyl4.tmp\bin\7z.exe
01-06 19:04 DEBUG  CommonBackend: Fetching basic info...
01-06 19:04 DEBUG  CommonBackend: original_exe=J:\wubi.exe
01-06 19:04 DEBUG  CommonBackend: platform=win32
01-06 19:04 DEBUG  CommonBackend: osname=nt
01-06 19:04 DEBUG  CommonBackend: language=zh_TW
01-06 19:04 DEBUG  CommonBackend: encoding=cp950
01-06 19:04 DEBUG  WindowsBackend: arch=amd64
01-06 19:04 DEBUG  CommonBackend: Parsing isolist=r:\temp\pyl4.tmp\data\isolist.ini
01-06 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-06 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-06 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-06 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-06 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-06 19:04 DEBUG  WindowsBackend: Fetching host info...
01-06 19:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-06 19:04 DEBUG  WindowsBackend: windows version=xp
01-06 19:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-06 19:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
01-06 19:04 DEBUG  WindowsBackend: windows_build=2600
01-06 19:04 DEBUG  WindowsBackend: gmt=8
01-06 19:04 DEBUG  WindowsBackend: country=TW
01-06 19:04 DEBUG  WindowsBackend: timezone=Asia/Taipei
01-06 19:04 DEBUG  WindowsBackend: windows_username=william
01-06 19:04 DEBUG  WindowsBackend: user_full_name=william
01-06 19:04 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\william
01-06 19:04 DEBUG  WindowsBackend: windows_language_code=1028
01-06 19:04 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
01-06 19:04 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X2 545 Processor
01-06 19:04 DEBUG  WindowsBackend: bootloader=xp
01-06 19:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65829.2734375 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(C: hd 65829.2734375 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(D: hd 2416.71875 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(E: hd 43968.703125 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(F: hd 7820.83984375 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(G: hd 2266.7265625 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(H: hd 26382.625 mb free fat32)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(J: removable 1235.5625 mb free fat)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(R: hd 466.19921875 mb free fat32)
01-06 19:04 DEBUG  WindowsBackend: uninstaller_path=H:\ubuntu\uninstall-wubi.exe
01-06 19:04 DEBUG  WindowsBackend: previous_target_dir=H:\ubuntu
01-06 19:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-06 19:04 DEBUG  WindowsBackend: keyboard_id=67372036
01-06 19:04 DEBUG  WindowsBackend: keyboard_layout=us
01-06 19:04 DEBUG  WindowsBackend: keyboard_variant=
01-06 19:04 DEBUG  CommonBackend: python locale=('zh_TW', 'cp950')
01-06 19:04 DEBUG  CommonBackend: locale=zh_TW.UTF-8
01-06 19:04 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
01-06 19:04 DEBUG  CommonBackend: Searching ISOs on USB devices
01-06 19:04 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Ubuntu Netbook ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Kubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Kubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Kubuntu Netbook ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Mythbuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Mythbuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  CommonBackend: Searching for local CDs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
01-06 19:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
01-06 19:04 INFO   Distro: Found a valid CD for Ubuntu: J:\
01-06 19:04 INFO   root: Running the CD menu...
01-06 19:04 DEBUG  WindowsFrontend: __init__...
01-06 19:04 DEBUG  WindowsFrontend: on_init...
01-06 19:04 INFO   WinuiPage: appname=wubi, localedir=r:\temp\pyl4.tmp\translations, languages=['zh_TW', 'zh']
01-06 19:04 INFO   WinuiPage: appname=wubi, localedir=r:\temp\pyl4.tmp\translations, languages=['zh_TW', 'zh']
01-06 19:04 INFO   root: CD menu finished
01-06 19:04 INFO   root: Already installed, running the uninstaller...
01-06 19:04 INFO   root: Running the uninstaller...
01-06 19:04 INFO   CommonBackend: This is the uninstaller running
01-06 19:04 INFO   WinuiPage: appname=wubi, localedir=r:\temp\pyl4.tmp\translations, languages=['zh_TW', 'zh']
01-06 19:04 INFO   root: Received settings
01-06 19:04 INFO   WinuiPage: appname=wubi, localedir=r:\temp\pyl4.tmp\translations, languages=['zh_TW', 'zh']
01-06 19:04 DEBUG  TaskList: # Running tasklist...
01-06 19:04 DEBUG  TaskList: ## Running &#22791;&#20221; ISO &#20809;&#30424;&#38236;&#20687;&#25991;&#20214;...
01-06 19:04 DEBUG  TaskList: ## Finished &#22791;&#20221; ISO &#20809;&#30424;&#38236;&#20687;&#25991;&#20214;
01-06 19:04 DEBUG  TaskList: ## Running &#21024;&#38500;&#24341;&#23548;&#39033;...
01-06 19:04 ERROR  WindowsBackend: Cannot find bcdedit
01-06 19:04 DEBUG  WindowsBackend: undo_bootini C:
01-06 19:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 65829.2734375 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: undo_bootini D:
01-06 19:04 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 2416.71875 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: undo_bootini E:
01-06 19:04 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 43968.703125 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: undo_bootini F:
01-06 19:04 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 7820.83984375 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: undo_bootini G:
01-06 19:04 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 2266.7265625 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: undo_bootini H:
01-06 19:04 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 26382.625 mb free fat32)
01-06 19:04 DEBUG  WindowsBackend: undo_bootini J:
01-06 19:04 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 1235.5625 mb free fat)
01-06 19:04 DEBUG  WindowsBackend: undo_bootini R:
01-06 19:04 DEBUG  WindowsBackend: undo_configsys Drive(R: hd 466.19921875 mb free fat32)
01-06 19:04 DEBUG  TaskList: ## Finished &#21024;&#38500;&#24341;&#23548;&#39033;
01-06 19:04 DEBUG  TaskList: ## Running &#21024;&#38500;&#30446;&#26631;&#30446;&#24405;...
01-06 19:04 DEBUG  CommonBackend: Deleting H:\ubuntu
01-06 19:04 DEBUG  TaskList: ## Finished &#21024;&#38500;&#30446;&#26631;&#30446;&#24405;
01-06 19:04 DEBUG  TaskList: ## Running &#21024;&#38500;&#27880;&#20876;&#34920;&#38190;&#20540;...
01-06 19:04 DEBUG  TaskList: ## Finished &#21024;&#38500;&#27880;&#20876;&#34920;&#38190;&#20540;
01-06 19:04 DEBUG  TaskList: # Finished tasklist
01-06 19:04 INFO   root: Almost finished uninstalling
01-06 19:04 INFO   root: Finished uninstallation
01-06 19:04 DEBUG  CommonBackend: Fetching basic info...
01-06 19:04 DEBUG  CommonBackend: original_exe=J:\wubi.exe
01-06 19:04 DEBUG  CommonBackend: platform=win32
01-06 19:04 DEBUG  CommonBackend: osname=nt
01-06 19:04 DEBUG  WindowsBackend: arch=amd64
01-06 19:04 DEBUG  CommonBackend: Parsing isolist=r:\temp\pyl4.tmp\data\isolist.ini
01-06 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-06 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-06 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-06 19:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-06 19:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
01-06 19:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
01-06 19:04 DEBUG  WindowsBackend: Fetching host info...
01-06 19:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-06 19:04 DEBUG  WindowsBackend: windows version=xp
01-06 19:04 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
01-06 19:04 DEBUG  WindowsBackend: windows_sp=Service Pack 3
01-06 19:04 DEBUG  WindowsBackend: windows_build=2600
01-06 19:04 DEBUG  WindowsBackend: gmt=8
01-06 19:04 DEBUG  WindowsBackend: country=TW
01-06 19:04 DEBUG  WindowsBackend: timezone=Asia/Taipei
01-06 19:04 DEBUG  WindowsBackend: windows_username=william
01-06 19:04 DEBUG  WindowsBackend: user_full_name=william
01-06 19:04 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\william
01-06 19:04 DEBUG  WindowsBackend: windows_language_code=1028
01-06 19:04 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
01-06 19:04 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X2 545 Processor
01-06 19:04 DEBUG  WindowsBackend: bootloader=xp
01-06 19:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 65829.3164063 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(C: hd 65829.3164063 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(D: hd 2416.71875 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(E: hd 43968.703125 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(F: hd 7820.83984375 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(G: hd 2266.7265625 mb free ntfs)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(H: hd 28623.546875 mb free fat32)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(J: removable 1235.5625 mb free fat)
01-06 19:04 DEBUG  WindowsBackend: drive=Drive(R: hd 466.09765625 mb free fat32)
01-06 19:04 DEBUG  WindowsBackend: uninstaller_path=None
01-06 19:04 DEBUG  WindowsBackend: previous_target_dir=None
01-06 19:04 DEBUG  WindowsBackend: previous_distro_name=None
01-06 19:04 DEBUG  WindowsBackend: keyboard_id=67372036
01-06 19:04 DEBUG  WindowsBackend: keyboard_layout=us
01-06 19:04 DEBUG  WindowsBackend: keyboard_variant=
01-06 19:04 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
01-06 19:04 DEBUG  CommonBackend: Searching ISOs on USB devices
01-06 19:04 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Ubuntu Netbook ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Kubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Kubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Kubuntu Netbook ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Xubuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Mythbuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  Distro:   checking Mythbuntu ISO E:\ubuntu-10.10-desktop-i386.iso
01-06 19:04 DEBUG  Distro:     wrong size: 60770336 < 600000000
01-06 19:04 DEBUG  CommonBackend: Searching for local CDs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD

01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-06 19:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-06 19:04 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-06 19:04 INFO   Distro: Found a valid CD for Ubuntu: J:\
01-06 19:04 INFO   root: Running the installer...
01-06 19:04 INFO   WinuiPage: appname=wubi, localedir=r:\temp\pyl4.tmp\translations, languages=['zh_TW', 'zh']
01-06 19:04 INFO   WinuiPage: appname=wubi, localedir=r:\temp\pyl4.tmp\translations, languages=['zh_TW', 'zh']
01-06 19:05 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=william
01-06 19:05 INFO   root: Received settings
01-06 19:05 INFO   WinuiPage: appname=wubi, localedir=r:\temp\pyl4.tmp\translations, languages=['en_US', 'en']
01-06 19:05 DEBUG  TaskList: # Running tasklist...
01-06 19:05 DEBUG  TaskList: ## Running select_target_dir...
01-06 19:05 INFO   WindowsBackend: Installing into H:\ubuntu
01-06 19:05 DEBUG  TaskList: ## Finished select_target_dir
01-06 19:05 DEBUG  TaskList: ## Running create_dir_structure...
01-06 19:05 DEBUG  CommonBackend: Creating dir H:\ubuntu
01-06 19:05 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
01-06 19:05 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
01-06 19:05 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
01-06 19:05 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
01-06 19:05 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
01-06 19:05 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
01-06 19:05 DEBUG  TaskList: ## Finished create_dir_structure
01-06 19:05 DEBUG  TaskList: ## Running uncompress_target_dir...
01-06 19:05 DEBUG  TaskList: ## Finished uncompress_target_dir
01-06 19:05 DEBUG  TaskList: ## Running create_uninstaller...
01-06 19:05 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
01-06 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
01-06 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
01-06 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-06 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
01-06 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
01-06 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-06 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-06 19:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-06 19:05 DEBUG  TaskList: ## Finished create_uninstaller
01-06 19:05 DEBUG  TaskList: ## Running copy_installation_files...
01-06 19:05 DEBUG  WindowsBackend: Copying r:\temp\pyl4.tmp\data\custom-installation -> H:\ubuntu\install\custom-installation
01-06 19:05 DEBUG  WindowsBackend: Copying r:\temp\pyl4.tmp\winboot -> H:\ubuntu\winboot
01-06 19:05 DEBUG  WindowsBackend: Copying r:\temp\pyl4.tmp\data\images\Ubuntu.ico -> H:\ubuntu\Ubuntu.ico
01-06 19:05 DEBUG  TaskList: ## Finished copy_installation_files
01-06 19:05 DEBUG  TaskList: ## Running get_iso...
01-06 19:05 DEBUG  TaskList: New task copy_file
01-06 19:05 DEBUG  TaskList: ### Running copy_file...
01-06 19:08 DEBUG  TaskList: ### Finished copy_file
01-06 19:08 DEBUG  TaskList: New task check_iso
01-06 19:08 DEBUG  TaskList: ### Running check_iso...
01-06 19:08 DEBUG  CommonBackend: Checking H:\ubuntu\install\installation.iso
01-06 19:08 DEBUG  Distro:   checking Ubuntu ISO H:\ubuntu\install\installation.iso
01-06 19:08 DEBUG  Distro:     wrong size: 2029502464 > 900000000
01-06 19:08 DEBUG  TaskList: ### Finished check_iso
01-06 19:08 DEBUG  CommonBackend: Searching for local ISO
01-06 19:08 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
01-06 19:08 DEBUG  TaskList: New task get_metalink
01-06 19:08 DEBUG  TaskList: ### Running get_metalink...
01-06 19:08 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10](http://releases.ubuntu.com/10.10) ... ktop-amd64.metalink > H:\ubuntu\install
01-06 19:08 DEBUG  downloader: Download start filename=H:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
01-06 19:08 DEBUG  downloader: download finished (read 9135 bytes)
01-06 19:08 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink](http://releases.ubuntu.com/10.10/MD5SUMS-metalink) > H:\ubuntu\install
01-06 19:08 DEBUG  downloader: Download start filename=H:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
01-06 19:08 DEBUG  downloader: download finished (read 488 bytes)
01-06 19:08 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg) > H:\ubuntu\install
01-06 19:08 DEBUG  downloader: Download start filename=H:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
01-06 19:08 DEBUG  downloader: download finished (read 198 bytes)
01-06 19:08 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
01-06 19:08 INFO   saplog: Checking block bindings..
01-06 19:08 INFO   saplog: Key verified successfully.
01-06 19:08 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

01-06 19:08 DEBUG  TaskList: ### Finished get_metalink
01-06 19:08 DEBUG  TaskList: New task download
01-06 19:08 DEBUG  TaskList: ### Running download...
01-06 19:08 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.10](http://releases.ubuntu.com/10.10) ... p-amd64.iso.torrent > H:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
01-06 20:43 ERROR  TaskList: Traceback (most recent call last):
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


01-06 20:43 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

in task download
01-06 20:43 DEBUG  TaskList: ### Finished download
01-06 20:43 ERROR  TaskList: [Errno 13] Permission denied: u'H:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'H:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
01-06 20:43 DEBUG  TaskList: # Cancelling tasklist
01-06 20:43 DEBUG  TaskList: # Finished tasklist
01-06 20:43 ERROR  root: [Errno 13] Permission denied: u'H:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'H:\\ubuntu\\install\\ubuntu-10.10-desktop-amd64.iso'



---

### Post by bcbc on 2011-01-07
It's complaining that the .iso is too big. 

Take the downloaded .iso file, copy the wubi.exe you have, place them in the same folder and run wubi from there. That's the easiest way.

Once you have it installed, never update packages grub-pc and grub-common for wubi installs.

---

### Post by pumber on 2011-01-07
However, I install it from the same USB drive to another computer, it works. Why is it so ? Is it something related to the ramdrive in the PC ?

---

