---
title: "An Error Occured: Unscriptable Object"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by Monycker on 2011-10-20
Hiya!

Okay so I'm a complete and total n00b with all things linux, Ubuntu... essentially anything that isn't Windows.  Anyways...

The fan in my desktop PC recently blew, so I ripped out the HD, transferred the files to my laptop, and formatted the drive.  It's in an external enclosure, so it's essentially operating as a USB drive.

I tried running Wubi off of my laptop (heretofore referred to as "C:\" to get things running on the HD (heretofore referred to as "H:\").

On C:\ I'm running as the Administrator account.  I've changed all effective permissions of H:\ to Full Control for "Administrator".  I've changed ownership to "Administrator".  Everything on H:\ is set as far as I can tell.

But when I run wubi off of C:\, I get an error during the final stage of installation: 

> An error occurred: 

unscriptable object

For more information, please see the log file:
c:\blahblahblah\wubi-11.10-rev245.log

Upon opening that log, we find:

```
10-20 14:40 INFO   root: === wubi 11.10 rev245 ===
10-20 14:40 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
10-20 14:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Stephen\\Downloads\\Chrome\\wubi.exe"']
10-20 14:40 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\data
10-20 14:40 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\bin\7z.exe
10-20 14:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-20 14:40 DEBUG  CommonBackend: Fetching basic info...
10-20 14:40 DEBUG  CommonBackend: original_exe=C:\Users\Stephen\Downloads\Chrome\wubi.exe
10-20 14:40 DEBUG  CommonBackend: platform=win32
10-20 14:40 DEBUG  CommonBackend: osname=nt
10-20 14:40 DEBUG  CommonBackend: language=en_US
10-20 14:40 DEBUG  CommonBackend: encoding=cp1252
10-20 14:40 DEBUG  WindowsBackend: arch=amd64
10-20 14:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\data\isolist.ini
10-20 14:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-20 14:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-20 14:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-20 14:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-20 14:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-20 14:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-20 14:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-20 14:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-20 14:40 DEBUG  WindowsBackend: Fetching host info...
10-20 14:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-20 14:40 DEBUG  WindowsBackend: windows version=vista
10-20 14:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-20 14:40 DEBUG  WindowsBackend: windows_sp=None
10-20 14:40 DEBUG  WindowsBackend: windows_build=7601
10-20 14:40 DEBUG  WindowsBackend: gmt=-5
10-20 14:40 DEBUG  WindowsBackend: country=US
10-20 14:40 DEBUG  WindowsBackend: timezone=America/New_York
10-20 14:40 DEBUG  WindowsBackend: windows_username=Administrator
10-20 14:40 DEBUG  WindowsBackend: user_full_name=Administrator
10-20 14:40 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
10-20 14:40 DEBUG  WindowsBackend: windows_language_code=1033
10-20 14:40 DEBUG  WindowsBackend: windows_language=English
10-20 14:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
10-20 14:40 DEBUG  WindowsBackend: bootloader=vista
10-20 14:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 496122.78125 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(C: hd 496122.78125 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(D: hd 1645.20703125 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(G: hd 84.9296875 mb free fat32)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(H: hd 283098.882813 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(I: hd 838511.726563 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-20 14:40 DEBUG  WindowsBackend: uninstaller_path=H:\ubuntu\uninstall-wubi.exe
10-20 14:40 DEBUG  WindowsBackend: previous_target_dir=H:\ubuntu
10-20 14:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-20 14:40 DEBUG  WindowsBackend: keyboard_id=67699721
10-20 14:40 DEBUG  WindowsBackend: keyboard_layout=us
10-20 14:40 DEBUG  WindowsBackend: keyboard_variant=
10-20 14:40 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-20 14:40 DEBUG  CommonBackend: locale=en_US.UTF-8
10-20 14:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-20 14:40 DEBUG  CommonBackend: Searching ISOs on USB devices
10-20 14:40 DEBUG  CommonBackend: Searching for local CDs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 INFO   root: Already installed, running the uninstaller...
10-20 14:40 INFO   root: Running the uninstaller...
10-20 14:40 INFO   CommonBackend: This is the uninstaller running
10-20 14:40 DEBUG  WindowsFrontend: __init__...
10-20 14:40 DEBUG  WindowsFrontend: on_init...
10-20 14:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\translations, languages=['en_US', 'en']
10-20 14:40 INFO   root: Received settings
10-20 14:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\translations, languages=['en_US', 'en']
10-20 14:40 DEBUG  TaskList: # Running tasklist...
10-20 14:40 DEBUG  TaskList: ## Running Remove bootloader entry...
10-20 14:40 DEBUG  WindowsBackend: Removing bcd entry {c04027c7-d536-11e0-be0b-a69e1ac33f85}
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
10-20 14:40 DEBUG  WindowsBackend: undo_bootini C:
10-20 14:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 496122.78125 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: undo_bootini D:
10-20 14:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1645.20703125 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: undo_bootini G:
10-20 14:40 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 84.9296875 mb free fat32)
10-20 14:40 DEBUG  WindowsBackend: undo_bootini H:
10-20 14:40 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 283098.882813 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: undo_bootini I:
10-20 14:40 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 838511.726563 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: undo_bootini Q:
10-20 14:40 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
10-20 14:40 DEBUG  TaskList: ## Finished Remove bootloader entry
10-20 14:40 DEBUG  TaskList: ## Running Remove target dir...
10-20 14:40 DEBUG  CommonBackend: Deleting H:\ubuntu
10-20 14:40 DEBUG  TaskList: ## Finished Remove target dir
10-20 14:40 DEBUG  TaskList: ## Running Remove registry key...
10-20 14:40 DEBUG  TaskList: ## Finished Remove registry key
10-20 14:40 DEBUG  TaskList: # Finished tasklist
10-20 14:40 INFO   root: Almost finished uninstalling
10-20 14:40 INFO   root: Finished uninstallation
10-20 14:40 DEBUG  CommonBackend: Fetching basic info...
10-20 14:40 DEBUG  CommonBackend: original_exe=C:\Users\Stephen\Downloads\Chrome\wubi.exe
10-20 14:40 DEBUG  CommonBackend: platform=win32
10-20 14:40 DEBUG  CommonBackend: osname=nt
10-20 14:40 DEBUG  WindowsBackend: arch=amd64
10-20 14:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\data\isolist.ini
10-20 14:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-20 14:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-20 14:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-20 14:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-20 14:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-20 14:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-20 14:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-20 14:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-20 14:40 DEBUG  WindowsBackend: Fetching host info...
10-20 14:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-20 14:40 DEBUG  WindowsBackend: windows version=vista
10-20 14:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-20 14:40 DEBUG  WindowsBackend: windows_sp=None
10-20 14:40 DEBUG  WindowsBackend: windows_build=7601
10-20 14:40 DEBUG  WindowsBackend: gmt=-5
10-20 14:40 DEBUG  WindowsBackend: country=US
10-20 14:40 DEBUG  WindowsBackend: timezone=America/New_York
10-20 14:40 DEBUG  WindowsBackend: windows_username=Administrator
10-20 14:40 DEBUG  WindowsBackend: user_full_name=Administrator
10-20 14:40 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
10-20 14:40 DEBUG  WindowsBackend: windows_language_code=1033
10-20 14:40 DEBUG  WindowsBackend: windows_language=English
10-20 14:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
10-20 14:40 DEBUG  WindowsBackend: bootloader=vista
10-20 14:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 496122.878906 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(C: hd 496122.878906 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(D: hd 1645.3359375 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(G: hd 85.05859375 mb free fat32)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(H: hd 286654.488281 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(I: hd 838511.855469 mb free ntfs)
10-20 14:40 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-20 14:40 DEBUG  WindowsBackend: uninstaller_path=None
10-20 14:40 DEBUG  WindowsBackend: previous_target_dir=None
10-20 14:40 DEBUG  WindowsBackend: previous_distro_name=None
10-20 14:40 DEBUG  WindowsBackend: keyboard_id=67699721
10-20 14:40 DEBUG  WindowsBackend: keyboard_layout=us
10-20 14:40 DEBUG  WindowsBackend: keyboard_variant=
10-20 14:40 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-20 14:40 DEBUG  CommonBackend: Searching ISOs on USB devices
10-20 14:40 DEBUG  CommonBackend: Searching for local CDs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 INFO   root: Running the installer...
10-20 14:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\translations, languages=['en_US', 'en']
10-20 14:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\translations, languages=['en_US', 'en']
10-20 14:40 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=stephen
10-20 14:40 INFO   root: Received settings
10-20 14:40 DEBUG  CommonBackend: Searching for local CD
10-20 14:40 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:40 DEBUG  CommonBackend: Searching for local ISO
10-20 14:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl6424.tmp\translations, languages=['en_US', 'en']
10-20 14:40 DEBUG  TaskList: # Running tasklist...
10-20 14:40 DEBUG  TaskList: ## Running select_target_dir...
10-20 14:40 INFO   WindowsBackend: Installing into H:\ubuntu
10-20 14:40 DEBUG  TaskList: ## Finished select_target_dir
10-20 14:40 DEBUG  TaskList: ## Running create_dir_structure...
10-20 14:40 DEBUG  CommonBackend: Creating dir H:\ubuntu
10-20 14:40 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
10-20 14:40 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
10-20 14:40 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
10-20 14:40 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
10-20 14:40 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
10-20 14:40 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
10-20 14:40 DEBUG  TaskList: ## Finished create_dir_structure
10-20 14:40 DEBUG  TaskList: ## Running create_uninstaller...
10-20 14:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Stephen\Downloads\Chrome\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-20 14:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-20 14:40 DEBUG  TaskList: ## Finished create_uninstaller
10-20 14:40 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-20 14:40 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-20 14:40 DEBUG  TaskList: ## Running get_diskimage...
10-20 14:40 DEBUG  TaskList: New task download
10-20 14:40 DEBUG  TaskList: ### Running download...
10-20 14:40 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > H:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-20 14:40 DEBUG  downloader: Download start filename=H:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
10-20 14:41 DEBUG  downloader: download finished (read 96911360 bytes)
10-20 14:41 DEBUG  TaskList: ### Finished download
10-20 14:41 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 915, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1207, in _do_grab
IOError: [Errno 13] Permission denied
10-20 14:41 ERROR  TaskList: Non fatal error [Errno 13] Permission denied in task download
10-20 14:41 DEBUG  TaskList: ### Finished download
10-20 14:41 DEBUG  TaskList: ## Finished get_diskimage
10-20 14:41 DEBUG  TaskList: ## Running extract_diskimage...
10-20 14:41 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
10-20 14:41 DEBUG  TaskList: # Cancelling tasklist
10-20 14:41 DEBUG  TaskList: # Finished tasklist
10-20 14:41 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
10-20 14:47 INFO   root: === wubi 11.10 rev245 ===
10-20 14:47 DEBUG  root: Logfile is c:\users\admini~1\appdata\local\temp\wubi-11.10-rev245.log
10-20 14:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Stephen\\Downloads\\Chrome\\wubi.exe"']
10-20 14:47 DEBUG  CommonBackend: data_dir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\data
10-20 14:47 DEBUG  WindowsBackend: 7z=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\bin\7z.exe
10-20 14:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-20 14:47 DEBUG  CommonBackend: Fetching basic info...
10-20 14:47 DEBUG  CommonBackend: original_exe=C:\Users\Stephen\Downloads\Chrome\wubi.exe
10-20 14:47 DEBUG  CommonBackend: platform=win32
10-20 14:47 DEBUG  CommonBackend: osname=nt
10-20 14:47 DEBUG  CommonBackend: language=en_US
10-20 14:47 DEBUG  CommonBackend: encoding=cp1252
10-20 14:47 DEBUG  WindowsBackend: arch=amd64
10-20 14:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\data\isolist.ini
10-20 14:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-20 14:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-20 14:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-20 14:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-20 14:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-20 14:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-20 14:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-20 14:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-20 14:47 DEBUG  WindowsBackend: Fetching host info...
10-20 14:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-20 14:47 DEBUG  WindowsBackend: windows version=vista
10-20 14:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-20 14:47 DEBUG  WindowsBackend: windows_sp=None
10-20 14:47 DEBUG  WindowsBackend: windows_build=7601
10-20 14:47 DEBUG  WindowsBackend: gmt=-5
10-20 14:47 DEBUG  WindowsBackend: country=US
10-20 14:47 DEBUG  WindowsBackend: timezone=America/New_York
10-20 14:47 DEBUG  WindowsBackend: windows_username=Administrator
10-20 14:47 DEBUG  WindowsBackend: user_full_name=Administrator
10-20 14:47 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
10-20 14:47 DEBUG  WindowsBackend: windows_language_code=1033
10-20 14:47 DEBUG  WindowsBackend: windows_language=English
10-20 14:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
10-20 14:47 DEBUG  WindowsBackend: bootloader=vista
10-20 14:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 503849.066406 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(C: hd 503849.066406 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(D: hd 1645.3359375 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(G: hd 85.05859375 mb free fat32)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(H: hd 286567.109375 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(I: hd 838511.855469 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-20 14:47 DEBUG  WindowsBackend: uninstaller_path=H:\ubuntu\uninstall-wubi.exe
10-20 14:47 DEBUG  WindowsBackend: previous_target_dir=H:\ubuntu
10-20 14:47 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-20 14:47 DEBUG  WindowsBackend: keyboard_id=67699721
10-20 14:47 DEBUG  WindowsBackend: keyboard_layout=us
10-20 14:47 DEBUG  WindowsBackend: keyboard_variant=
10-20 14:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-20 14:47 DEBUG  CommonBackend: locale=en_US.UTF-8
10-20 14:47 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-20 14:47 DEBUG  CommonBackend: Searching ISOs on USB devices
10-20 14:47 DEBUG  CommonBackend: Searching for local CDs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 INFO   root: Already installed, running the uninstaller...
10-20 14:47 INFO   root: Running the uninstaller...
10-20 14:47 INFO   CommonBackend: This is the uninstaller running
10-20 14:47 DEBUG  WindowsFrontend: __init__...
10-20 14:47 DEBUG  WindowsFrontend: on_init...
10-20 14:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\translations, languages=['en_US', 'en']
10-20 14:47 INFO   root: Received settings
10-20 14:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\translations, languages=['en_US', 'en']
10-20 14:47 DEBUG  TaskList: # Running tasklist...
10-20 14:47 DEBUG  TaskList: ## Running Remove bootloader entry...
10-20 14:47 DEBUG  WindowsBackend: Could not find bcd id
10-20 14:47 DEBUG  WindowsBackend: undo_bootini C:
10-20 14:47 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 503849.066406 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: undo_bootini D:
10-20 14:47 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1645.3359375 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: undo_bootini G:
10-20 14:47 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 85.05859375 mb free fat32)
10-20 14:47 DEBUG  WindowsBackend: undo_bootini H:
10-20 14:47 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 286567.109375 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: undo_bootini I:
10-20 14:47 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 838511.855469 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: undo_bootini Q:
10-20 14:47 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
10-20 14:47 DEBUG  TaskList: ## Finished Remove bootloader entry
10-20 14:47 DEBUG  TaskList: ## Running Remove target dir...
10-20 14:47 DEBUG  CommonBackend: Deleting H:\ubuntu
10-20 14:47 DEBUG  TaskList: ## Finished Remove target dir
10-20 14:47 DEBUG  TaskList: ## Running Remove registry key...
10-20 14:47 DEBUG  TaskList: ## Finished Remove registry key
10-20 14:47 DEBUG  TaskList: # Finished tasklist
10-20 14:47 INFO   root: Almost finished uninstalling
10-20 14:47 INFO   root: Finished uninstallation
10-20 14:47 DEBUG  CommonBackend: Fetching basic info...
10-20 14:47 DEBUG  CommonBackend: original_exe=C:\Users\Stephen\Downloads\Chrome\wubi.exe
10-20 14:47 DEBUG  CommonBackend: platform=win32
10-20 14:47 DEBUG  CommonBackend: osname=nt
10-20 14:47 DEBUG  WindowsBackend: arch=amd64
10-20 14:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\data\isolist.ini
10-20 14:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-20 14:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-20 14:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-20 14:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-20 14:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-20 14:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-20 14:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-20 14:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-20 14:47 DEBUG  WindowsBackend: Fetching host info...
10-20 14:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-20 14:47 DEBUG  WindowsBackend: windows version=vista
10-20 14:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
10-20 14:47 DEBUG  WindowsBackend: windows_sp=None
10-20 14:47 DEBUG  WindowsBackend: windows_build=7601
10-20 14:47 DEBUG  WindowsBackend: gmt=-5
10-20 14:47 DEBUG  WindowsBackend: country=US
10-20 14:47 DEBUG  WindowsBackend: timezone=America/New_York
10-20 14:47 DEBUG  WindowsBackend: windows_username=Administrator
10-20 14:47 DEBUG  WindowsBackend: user_full_name=Administrator
10-20 14:47 DEBUG  WindowsBackend: user_directory=C:\Users\Administrator
10-20 14:47 DEBUG  WindowsBackend: windows_language_code=1033
10-20 14:47 DEBUG  WindowsBackend: windows_language=English
10-20 14:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
10-20 14:47 DEBUG  WindowsBackend: bootloader=vista
10-20 14:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 503849.046875 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(C: hd 503849.046875 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(D: hd 1645.3359375 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(G: hd 85.05859375 mb free fat32)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(H: hd 286654.488281 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(I: hd 838511.855469 mb free ntfs)
10-20 14:47 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
10-20 14:47 DEBUG  WindowsBackend: uninstaller_path=None
10-20 14:47 DEBUG  WindowsBackend: previous_target_dir=None
10-20 14:47 DEBUG  WindowsBackend: previous_distro_name=None
10-20 14:47 DEBUG  WindowsBackend: keyboard_id=67699721
10-20 14:47 DEBUG  WindowsBackend: keyboard_layout=us
10-20 14:47 DEBUG  WindowsBackend: keyboard_variant=
10-20 14:47 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-20 14:47 DEBUG  CommonBackend: Searching ISOs on USB devices
10-20 14:47 DEBUG  CommonBackend: Searching for local CDs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 INFO   root: Running the installer...
10-20 14:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\translations, languages=['en_US', 'en']
10-20 14:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\translations, languages=['en_US', 'en']
10-20 14:47 DEBUG  WinuiInstallationPage: target_drive=H:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=stephen
10-20 14:47 INFO   root: Received settings
10-20 14:47 DEBUG  CommonBackend: Searching for local CD
10-20 14:47 DEBUG  Distro:   checking whether C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-20 14:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
10-20 14:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
10-20 14:47 DEBUG  CommonBackend: Searching for local ISO
10-20 14:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ADMINI~1\AppData\Local\Temp\pyl948.tmp\translations, languages=['en_US', 'en']
10-20 14:47 DEBUG  TaskList: # Running tasklist...
10-20 14:47 DEBUG  TaskList: ## Running select_target_dir...
10-20 14:47 INFO   WindowsBackend: Installing into H:\ubuntu
10-20 14:47 DEBUG  TaskList: ## Finished select_target_dir
10-20 14:47 DEBUG  TaskList: ## Running create_dir_structure...
10-20 14:47 DEBUG  CommonBackend: Creating dir H:\ubuntu
10-20 14:47 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks
10-20 14:47 DEBUG  CommonBackend: Creating dir H:\ubuntu\install
10-20 14:47 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot
10-20 14:47 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot
10-20 14:47 DEBUG  CommonBackend: Creating dir H:\ubuntu\disks\boot\grub
10-20 14:47 DEBUG  CommonBackend: Creating dir H:\ubuntu\install\boot\grub
10-20 14:47 DEBUG  TaskList: ## Finished create_dir_structure
10-20 14:47 DEBUG  TaskList: ## Running create_uninstaller...
10-20 14:47 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Stephen\Downloads\Chrome\wubi.exe -> H:\ubuntu\uninstall-wubi.exe
10-20 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString H:\ubuntu\uninstall-wubi.exe
10-20 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir H:\ubuntu
10-20 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-20 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon H:\ubuntu\Ubuntu.ico
10-20 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
10-20 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-20 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
10-20 14:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
10-20 14:47 DEBUG  TaskList: ## Finished create_uninstaller
10-20 14:47 DEBUG  TaskList: ## Running create_preseed_diskimage...
10-20 14:47 DEBUG  TaskList: ## Finished create_preseed_diskimage
10-20 14:47 DEBUG  TaskList: ## Running get_diskimage...
10-20 14:47 DEBUG  TaskList: New task download
10-20 14:47 DEBUG  TaskList: ### Running download...
10-20 14:47 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > H:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
10-20 14:47 DEBUG  downloader: Download start filename=H:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
10-20 14:49 DEBUG  downloader: download finished (read 116490240 bytes)
10-20 14:49 DEBUG  TaskList: ### Finished download
10-20 14:49 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 915, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1207, in _do_grab
IOError: [Errno 13] Permission denied
10-20 14:49 ERROR  TaskList: Non fatal error [Errno 13] Permission denied in task download
10-20 14:49 DEBUG  TaskList: ### Finished download
10-20 14:49 DEBUG  TaskList: ## Finished get_diskimage
10-20 14:49 DEBUG  TaskList: ## Running extract_diskimage...
10-20 14:49 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
10-20 14:49 DEBUG  TaskList: # Cancelling tasklist
10-20 14:49 DEBUG  TaskList: # Finished tasklist
10-20 14:49 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object

```

Could somebody help me out?  I'm excited to become an Ubuntu user.

Thanks!

---

### Post by Monycker on 2011-10-22
Bump.  Please help!

---

### Post by bcbc on 2011-10-22
Looks like you lost your connection while downloading:
> 10-20 14:49 DEBUG  downloader: download finished (read **[COLOR="Blue"]116490240[/COLOR]** bytes)
10-20 14:49 DEBUG  TaskList: ### Finished download

That should have downloaded about 500MB and you only got about 100MB.

There are some alternative options to install:
1. [download]("http://www.ubuntu.com/download/ubuntu/download") the 11.10 desktop cd ISO
2. [download]("http://www.ubuntu.com/download/ubuntu/windows-installer") wubi.exe into the same folder
3. run wubi and it will use the ISO

Wubi is good to try out Ubuntu. For long term use a direct dual boot is better.

PS if you have a flaky connection (if that's the reason for the failure to download the full image) you might instead consider a bittorrent client. You can get the links here: [http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/)

---

### Post by Monycker on 2011-10-22
So wubi.exe wasn't working out for me... I extracted the ISO to a flash drive and managed to locate my boot menu.  I booted the extracted files (of 11.10) and it ran and actually wound up running Ubuntu on my system.

So I actually now have it set up on my computer so that can dual-boot.  This was mostly accidental, as my goal was to have my laptop HD running ONLY Windows, and my external HD running ONLY Ubuntu.  I thought there would be some sort of option to select a drive onto which I would install Ubuntu, or even a screen asking me how many gigabytes I wanted to partition for Ubuntu, if it was just going to install on my local drive anyway.

So now I have some questions:
[INDENT]A) Is it possible, from here, to install Ubuntu on my external HD and UNINSTALL it from my internal HD?

B) Why does my Ubuntu Filesystem say that it only has 301GB of space?  It's running on a 640GB hard drive.  
[/INDENT]And relatedly,
[INDENT]C) Why does my C:\ drive in Windows say that I still have 640GB?  I imagine that number would be smaller if the drive had been partitioned.
[/INDENT]Anyone who can answer one, two, or all of these questions, please feel free to post below.  Your assistance is greatly appreciated.

---

### Post by bcbc on 2011-10-22
Post the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That should explain the situation nicely.

---

### Post by sourabh.anand on 2011-10-28
almost 650 mb of 700 mb was downloaded...when the message popped 'unscriptable object'
what should i do???
pls help

---

### Post by Rubi1200 on 2011-10-28
> **sourabh.anand said:**
> almost 650 mb of 700 mb was downloaded...when the message popped 'unscriptable object'
what should i do???
pls help
Hi and welcome to the forums :)

Try the advice posted in post 3 by bcbc. If that doesn't work you may want to consider trying an older version such as 11.04 or even 10.10.

Posting the specifications and the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") would also help.

---

### Post by bcbc on 2011-10-28
> **sourabh.anand said:**
> almost 650 mb of 700 mb was downloaded...when the message popped 'unscriptable object'
what should i do???
pls help

I just want to add to Rubi1200's comments - Wubi has 2 distinct methods of installing now. One downloads a preinstalled image (~500MB) and the other downloads the desktop CD ISO (~700B).

In addition, the exception messages are generally unhelpful - the log file is the only decent way to see what is going on. But likely if the dowload stopped short then the problem is the same as the original poster - it rejects the download as it's not valid.

---

