---
title: "problem installing from wubi.exe"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by jimdukecenter on 2011-02-21
I am trying to install from wubi.exe and have a problem. I get a window from pyrun.exe - not disk.   The text says " There is no disk in the drive.  Please insert a disk into drive
\Device\Harddisk4\DR4

The system is Windows 7 on a Dell system :
64 bit system
Intel Core i7 CPU
920@2.67 GHZ
Windows 7 Premium
497 GB free HD space

WHAT IS WRONG - HELP
Thanks
[email]jimwill@cableone.net[/email]

---

### Post by Frogs Hair on 2011-02-21
See this thread. [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2011-02-21
That error is an unhandled exception from python (wubi is written in python) when it finds a drive letter assigned that is empty. E.g. when you have a multimedia card reader attached.

So, you can either click Continue (forever, not really forever but it will seem that way). Or remove all assigned empty drives.

You can also kill pyrun.exe to terminate the process from the task manager.

---

### Post by jimdukecenter on 2011-02-21
> **bcbc said:**
> That error is an unhandled exception from python (wubi is written in python) when it finds a drive letter assigned that is empty. E.g. when you have a multimedia card reader attached.

So, you can either click Continue (forever, not really forever but it will seem that way). Or remove all assigned empty drives.

You can also kill pyrun.exe to terminate the process from the task manager.

I clicked the message about 40 times and it processed about 25 minutes.  My download speed should be about 5 mb.sec. It then gave an error and said to check the log file.  There were all kinds of errors in the file and I didn't understand the significance of any.  Several refered to py***. I guess I will just have to forget the whole thing.  Any other ideas?  Thanks

---

### Post by bcbc on 2011-02-21
> **jimdukecenter said:**
> I clicked the message about 40 times and it processed about 25 minutes.  My download speed should be about 5 mb.sec. It then gave an error and said to check the log file.  There were all kinds of errors in the file and I didn't understand the significance of any.  Several refered to py***. I guess I will just have to forget the whole thing.  Any other ideas?  Thanks

The log file is in the %temp% directory. It'll probably be called wubi-10.10-rev197.log (I'm assuming you're running 10.10). If you decide to try again post it here between code tags (press # above) and I'll have a look.

Also, see the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I install Wubi on a machine with no Internet connection?") on how to install without internet (this method is actually the most fool proof even if you do have internet).

---

### Post by jimdukecenter on 2011-02-21
```
02-21 13:40 INFO   root: === wubi 10.04.1 rev190 ===
02-21 13:40 DEBUG  root: Logfile is c:\users\jim\appdata\local\temp\wubi-10.04.1-rev190.log
02-21 13:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\My Download Files\\Linux\\wubi.exe"']
02-21 13:40 DEBUG  CommonBackend: data_dir=C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\data
02-21 13:40 DEBUG  WindowsBackend: 7z=C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\bin\7z.exe
02-21 13:40 DEBUG  CommonBackend: Fetching basic info...
02-21 13:40 DEBUG  CommonBackend: original_exe=C:\My Download Files\Linux\wubi.exe
02-21 13:40 DEBUG  CommonBackend: platform=win32
02-21 13:40 DEBUG  CommonBackend: osname=nt
02-21 13:40 DEBUG  CommonBackend: language=en_US
02-21 13:40 DEBUG  CommonBackend: encoding=cp1252
02-21 13:40 DEBUG  WindowsBackend: arch=amd64
02-21 13:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\data\isolist.ini
02-21 13:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-21 13:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-21 13:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-21 13:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-21 13:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-21 13:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-21 13:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-21 13:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-21 13:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-21 13:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-21 13:40 DEBUG  WindowsBackend: Fetching host info...
02-21 13:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-21 13:40 DEBUG  WindowsBackend: windows version=vista
02-21 13:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-21 13:40 DEBUG  WindowsBackend: windows_sp=None
02-21 13:40 DEBUG  WindowsBackend: windows_build=7600
02-21 13:40 DEBUG  WindowsBackend: gmt=-6
02-21 13:40 DEBUG  WindowsBackend: country=US
02-21 13:40 DEBUG  WindowsBackend: timezone=America/Chicago
02-21 13:40 DEBUG  WindowsBackend: windows_username=Jim
02-21 13:40 DEBUG  WindowsBackend: user_full_name=Jim
02-21 13:40 DEBUG  WindowsBackend: user_directory=C:\Users\Jim
02-21 13:40 DEBUG  WindowsBackend: windows_language_code=1033
02-21 13:40 DEBUG  WindowsBackend: windows_language=English
02-21 13:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
02-21 13:40 DEBUG  WindowsBackend: bootloader=vista
02-21 13:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 509536.246094 mb free ntfs)
02-21 13:40 DEBUG  WindowsBackend: drive=Drive(C: hd 509536.246094 mb free ntfs)
02-21 13:40 DEBUG  WindowsBackend: drive=Drive(D: hd 2.08203125 mb free ntfs)
02-21 13:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-21 13:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-21 13:41 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
02-21 13:41 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
02-21 13:41 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
02-21 13:43 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
02-21 13:43 DEBUG  WindowsBackend: drive=Drive(K: hd 180615.496094 mb free ntfs)
02-21 13:43 DEBUG  WindowsBackend: uninstaller_path=None
02-21 13:43 DEBUG  WindowsBackend: previous_target_dir=None
02-21 13:43 DEBUG  WindowsBackend: previous_distro_name=None
02-21 13:43 DEBUG  WindowsBackend: keyboard_id=67699721
02-21 13:43 DEBUG  WindowsBackend: keyboard_layout=us
02-21 13:43 DEBUG  WindowsBackend: keyboard_variant=
02-21 13:43 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-21 13:43 DEBUG  CommonBackend: locale=en_US.UTF-8
02-21 13:43 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-21 13:43 DEBUG  CommonBackend: Searching ISOs on USB devices
02-21 13:44 DEBUG  CommonBackend: Searching for local CDs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Ubuntu Netbook CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Kubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Kubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Kubuntu Netbook CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Xubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Xubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Mythbuntu CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp is a valid Mythbuntu CD
02-21 13:44 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl94D0.tmp\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 13:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-21 13:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-21 13:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-21 13:44 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 13:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-21 13:52 INFO   root: === wubi 10.04.1 rev190 ===
02-21 13:52 DEBUG  root: Logfile is c:\users\jim\appdata\local\temp\wubi-10.04.1-rev190.log
02-21 13:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\My Download Files\\Linux\\wubi.exe"']
02-21 13:52 DEBUG  CommonBackend: data_dir=C:\Users\Jim\AppData\Local\Temp\pylE149.tmp\data
02-21 13:52 DEBUG  WindowsBackend: 7z=C:\Users\Jim\AppData\Local\Temp\pylE149.tmp\bin\7z.exe
02-21 13:52 DEBUG  CommonBackend: Fetching basic info...
02-21 13:52 DEBUG  CommonBackend: original_exe=C:\My Download Files\Linux\wubi.exe
02-21 13:52 DEBUG  CommonBackend: platform=win32
02-21 13:52 DEBUG  CommonBackend: osname=nt
02-21 13:52 DEBUG  CommonBackend: language=en_US
02-21 13:52 DEBUG  CommonBackend: encoding=cp1252
02-21 13:52 DEBUG  WindowsBackend: arch=amd64
02-21 13:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jim\AppData\Local\Temp\pylE149.tmp\data\isolist.ini
02-21 13:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-21 13:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-21 13:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-21 13:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-21 13:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-21 13:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-21 13:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-21 13:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-21 13:52 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-21 13:52 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-21 13:52 DEBUG  WindowsBackend: Fetching host info...
02-21 13:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-21 13:52 DEBUG  WindowsBackend: windows version=vista
02-21 13:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-21 13:52 DEBUG  WindowsBackend: windows_sp=None
02-21 13:52 DEBUG  WindowsBackend: windows_build=7600
02-21 13:52 DEBUG  WindowsBackend: gmt=-6
02-21 13:52 DEBUG  WindowsBackend: country=US
02-21 13:52 DEBUG  WindowsBackend: timezone=America/Chicago
02-21 13:52 DEBUG  WindowsBackend: windows_username=Jim
02-21 13:52 DEBUG  WindowsBackend: user_full_name=Jim
02-21 13:52 DEBUG  WindowsBackend: user_directory=C:\Users\Jim
02-21 13:52 DEBUG  WindowsBackend: windows_language_code=1033
02-21 13:52 DEBUG  WindowsBackend: windows_language=English
02-21 13:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
02-21 13:52 DEBUG  WindowsBackend: bootloader=vista
02-21 13:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 509592.441406 mb free ntfs)
02-21 13:52 DEBUG  WindowsBackend: drive=Drive(C: hd 509592.441406 mb free ntfs)
02-21 13:52 DEBUG  WindowsBackend: drive=Drive(D: hd 2.08203125 mb free ntfs)
02-21 13:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-21 13:52 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-21 13:53 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
02-21 13:53 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
02-21 13:53 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
02-21 14:33 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
02-21 14:33 DEBUG  WindowsBackend: drive=Drive(K: hd 180615.496094 mb free ntfs)
02-21 14:33 DEBUG  WindowsBackend: uninstaller_path=None
02-21 14:33 DEBUG  WindowsBackend: previous_target_dir=None
02-21 14:33 DEBUG  WindowsBackend: previous_distro_name=None
02-21 14:33 DEBUG  WindowsBackend: keyboard_id=67699721
02-21 14:33 DEBUG  WindowsBackend: keyboard_layout=us
02-21 14:33 DEBUG  WindowsBackend: keyboard_variant=
02-21 14:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-21 14:33 DEBUG  CommonBackend: locale=en_US.UTF-8
02-21 14:33 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-21 14:33 DEBUG  CommonBackend: Searching ISOs on USB devices
02-21 16:58 INFO   root: === wubi 10.04.1 rev190 ===
02-21 16:58 DEBUG  root: Logfile is c:\users\jim\appdata\local\temp\wubi-10.04.1-rev190.log
02-21 16:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\My Download Files\\Linux\\wubi.exe"']
02-21 16:58 DEBUG  CommonBackend: data_dir=C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\data
02-21 16:58 DEBUG  WindowsBackend: 7z=C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\bin\7z.exe
02-21 16:58 DEBUG  CommonBackend: Fetching basic info...
02-21 16:58 DEBUG  CommonBackend: original_exe=C:\My Download Files\Linux\wubi.exe
02-21 16:58 DEBUG  CommonBackend: platform=win32
02-21 16:58 DEBUG  CommonBackend: osname=nt
02-21 16:58 DEBUG  CommonBackend: language=en_US
02-21 16:58 DEBUG  CommonBackend: encoding=cp1252
02-21 16:58 DEBUG  WindowsBackend: arch=amd64
02-21 16:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\data\isolist.ini
02-21 16:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-21 16:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-21 16:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-21 16:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-21 16:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-21 16:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-21 16:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-21 16:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-21 16:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
02-21 16:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
02-21 16:58 DEBUG  WindowsBackend: Fetching host info...
02-21 16:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-21 16:58 DEBUG  WindowsBackend: windows version=vista
02-21 16:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-21 16:58 DEBUG  WindowsBackend: windows_sp=None
02-21 16:58 DEBUG  WindowsBackend: windows_build=7600
02-21 16:58 DEBUG  WindowsBackend: gmt=-6
02-21 16:58 DEBUG  WindowsBackend: country=US
02-21 16:58 DEBUG  WindowsBackend: timezone=America/Chicago
02-21 16:58 DEBUG  WindowsBackend: windows_username=Jim
02-21 16:58 DEBUG  WindowsBackend: user_full_name=Jim
02-21 16:58 DEBUG  WindowsBackend: user_directory=C:\Users\Jim
02-21 16:58 DEBUG  WindowsBackend: windows_language_code=1033
02-21 16:58 DEBUG  WindowsBackend: windows_language=English
02-21 16:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU         920  @ 2.67GHz
02-21 16:58 DEBUG  WindowsBackend: bootloader=vista
02-21 16:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 509543.667969 mb free ntfs)
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(C: hd 509543.667969 mb free ntfs)
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(D: hd 2.08203125 mb free ntfs)
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
02-21 16:58 DEBUG  WindowsBackend: drive=Drive(K: hd 180416.871094 mb free ntfs)
02-21 16:58 DEBUG  WindowsBackend: uninstaller_path=None
02-21 16:58 DEBUG  WindowsBackend: previous_target_dir=None
02-21 16:58 DEBUG  WindowsBackend: previous_distro_name=None
02-21 16:58 DEBUG  WindowsBackend: keyboard_id=67699721
02-21 16:58 DEBUG  WindowsBackend: keyboard_layout=us
02-21 16:58 DEBUG  WindowsBackend: keyboard_variant=
02-21 16:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
02-21 16:58 DEBUG  CommonBackend: locale=en_US.UTF-8
02-21 16:58 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
02-21 16:58 DEBUG  CommonBackend: Searching ISOs on USB devices
02-21 16:59 DEBUG  CommonBackend: Searching for local CDs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu Netbook CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-21 16:59 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 16:59 INFO   root: Running the installer...
02-21 16:59 DEBUG  WindowsFrontend: __init__...
02-21 16:59 DEBUG  WindowsFrontend: on_init...
02-21 16:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\translations, languages=['en_US', 'en']
02-21 16:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\translations, languages=['en_US', 'en']
02-21 17:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jim
02-21 17:00 INFO   root: Received settings
02-21 17:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\translations, languages=['en_US', 'en']
02-21 17:00 DEBUG  TaskList: # Running tasklist...
02-21 17:00 DEBUG  TaskList: ## Running select_target_dir...
02-21 17:00 INFO   WindowsBackend: Installing into C:\ubuntu
02-21 17:00 DEBUG  TaskList: ## Finished select_target_dir
02-21 17:00 DEBUG  TaskList: ## Running create_dir_structure...
02-21 17:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-21 17:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-21 17:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-21 17:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-21 17:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-21 17:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-21 17:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-21 17:00 DEBUG  TaskList: ## Finished create_dir_structure
02-21 17:00 DEBUG  TaskList: ## Running uncompress_target_dir...
02-21 17:00 DEBUG  TaskList: ## Finished uncompress_target_dir
02-21 17:00 DEBUG  TaskList: ## Running create_uninstaller...
02-21 17:00 DEBUG  WindowsBackend: Copying uninstaller C:\My Download Files\Linux\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-21 17:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-21 17:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-21 17:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-21 17:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-21 17:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
02-21 17:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-21 17:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-21 17:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-21 17:00 DEBUG  TaskList: ## Finished create_uninstaller
02-21 17:00 DEBUG  TaskList: ## Running copy_installation_files...
02-21 17:00 DEBUG  WindowsBackend: Copying C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-21 17:00 DEBUG  WindowsBackend: Copying C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\winboot -> C:\ubuntu\winboot
02-21 17:00 DEBUG  WindowsBackend: Copying C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-21 17:00 DEBUG  TaskList: ## Finished copy_installation_files
02-21 17:00 DEBUG  TaskList: ## Running get_iso...
02-21 17:00 DEBUG  CommonBackend: Searching for local CD
02-21 17:00 DEBUG  Distro:   checking whether C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain C:\Users\Jim\AppData\Local\Temp\pyl40B9.tmp\casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-21 17:00 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-21 17:00 DEBUG  CommonBackend: Searching for local ISO
02-21 17:00 DEBUG  Distro:   checking Ubuntu ISO C:\My Download Files\Linux\ubuntu-5.10-install-i386(1).iso
02-21 17:00 DEBUG  Distro:     does not contain casper\filesystem.squashfs
02-21 17:00 DEBUG  Distro:   checking Ubuntu ISO C:\My Download Files\Linux\ubuntu-5.10-install-i386.iso
02-21 17:00 DEBUG  Distro:     does not contain casper\filesystem.squashfs
02-21 17:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
02-21 17:00 DEBUG  TaskList: New task get_metalink
02-21 17:00 DEBUG  TaskList: ### Running get_metalink...
02-21 17:00 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink > C:\ubuntu\install
02-21 17:00 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink err=[Errno 14] HTTP Error 404: Not Found
02-21 17:00 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink > C:\ubuntu\install
02-21 17:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink, basename=lucid-desktop-amd64.metalink, length=1010, text=None
02-21 17:00 DEBUG  downloader: download finished (read 1010 bytes)
02-21 17:00 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink > C:\ubuntu\install
02-21 17:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=257, text=None
02-21 17:00 DEBUG  downloader: download finished (read 257 bytes)
02-21 17:00 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg > C:\ubuntu\install
02-21 17:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
02-21 17:00 DEBUG  downloader: download finished (read 198 bytes)
02-21 17:00 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
02-21 17:00 INFO   saplog: Checking block bindings..
02-21 17:00 INFO   saplog: Key verified successfully.
02-21 17:00 DEBUG  CommonBackend: metalink md5sums:
2b8731d74a30fcb3ad22ae5b58c8b0d6  natty-desktop-amd64+mac.metalink
d16cf0bd4223dd0150ec785c6a57b0e9  natty-desktop-amd64.metalink
1ec2a8e66cf5e5b128916e9933681ac1  natty-desktop-i386.metalink
08ba9f6620fe3b99a93ba1af30fc2e96  natty-desktop-powerpc.metalink

02-21 17:00 ERROR  CommonBackend: The md5 of the metalink does match
02-21 17:00 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
02-21 17:00 DEBUG  TaskList: ### Finished get_metalink
02-21 17:00 DEBUG  TaskList: New task download
02-21 17:00 DEBUG  TaskList: ### Running download...
02-21 17:00 DEBUG  btdownloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso.torrent > C:\ubuntu\install\lucid-desktop-amd64.iso
02-21 17:00 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
02-21 17:00 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
02-21 17:00 DEBUG  TaskList: ### Finished download
02-21 17:00 DEBUG  TaskList: New task download
02-21 17:00 DEBUG  TaskList: ### Running download...
02-21 17:00 DEBUG  downloader: downloading http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso > C:\ubuntu\install\lucid-desktop-amd64.iso
02-21 17:00 DEBUG  downloader: Download start filename=C:\ubuntu\install\lucid-desktop-amd64.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20110211.1/lucid-desktop-amd64.iso, basename=lucid-desktop-amd64.iso, length=721129472, text=None
02-21 17:18 DEBUG  TaskList: ### Finished download
02-21 17:18 DEBUG  downloader: download finished (read 721129472 bytes)
02-21 17:18 DEBUG  TaskList: New task check_iso
02-21 17:18 DEBUG  TaskList: ### Running check_iso...
02-21 17:18 DEBUG  CommonBackend: Checking C:\ubuntu\install\lucid-desktop-amd64.iso
02-21 17:18 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\lucid-desktop-amd64.iso
02-21 17:18 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\lucid-desktop-amd64.iso
02-21 17:18 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.2 LTS "Lucid Lynx" - Release amd64 (20110211.1)
02-21 17:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.2', 'build': '20110211.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
02-21 17:18 DEBUG  Distro: wrong version: 10.04.2 != 10.04.1
02-21 17:18 DEBUG  TaskList: ### Finished check_iso
02-21 17:18 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files
02-21 17:18 DEBUG  TaskList: # Cancelling tasklist
02-21 17:18 DEBUG  TaskList: # Finished tasklist
02-21 17:18 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 498, in get_iso
Exception: Could not retrieve the required installation files

```

---

### Post by bcbc on 2011-02-21
The version of wubi.exe you have is 10.04.1. This doesn't work anymore since 10.04.2 was released. Unfortunately it appears they've left the wrong version at [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) so that won't work.

hmmm. This is pretty recent since 10.04.2 was only released a few days ago. I suppose a bug report should be created as no one on ubuntuforums.org has the ability to update this website.

In the meantime you could use this wubi: [http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe](http://people.canonical.com/~evand/wubi/lucid/wubi-r191.exe) (that's 10.04.2)

Either that or download the Ubuntu image you want from [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) and burn it to disk. I assume that they got the right version of wubi on it... I'll have to check that as well though. So far the safe bet is that R191 version.

New bug: [https://bugs.launchpad.net/wubi/+bug/722955](https://bugs.launchpad.net/wubi/+bug/722955)

---

