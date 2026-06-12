---
title: "Unable to uninstall Ubunto 11.10"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by Kraut55 on 2012-02-10
Hi,
I am a complete novice having used Windows all my (computer)life.
After having read so many positive things about Linux I wanted to give it a try. I downloaded Ubuntu 11.10, burned it on a disc and ran the installation after I rebooted my PC (Windows7).
Ubuntu suggested installation on a USB drive, I agreed, it created a partition and installed, I guess, everything without a problem as I received a message at the end that the ibstallation was finished and I should take the disc out and hit Enter.
On reboot I expected to get a dual-boot message asking me if I wanted to use Ubuntu or Windows7. No such thing. I ended up on my Windows7 desktop. Rebooted, same thing. So I decided to uninstall Ubuntu to get back the 25% of my 1TB USB-drive. Instead I got an error message saying that a file could not be found.
I enclose the log. I would appreciate if anybody could help me getting Ubuntu to uninstall.
Thank you.
Kraut55

```


02-09 14:09 INFO   root: === wubi 11.10 rev245 ===
02-09 14:09 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-09 14:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Schniedel\\Desktop\\wubi.exe"']
02-09 14:09 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\data
02-09 14:09 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\bin\7z.exe
02-09 14:09 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-09 14:09 DEBUG  CommonBackend: Fetching basic info...
02-09 14:09 DEBUG  CommonBackend: original_exe=C:\Users\Schniedel\Desktop\wubi.exe
02-09 14:09 DEBUG  CommonBackend: platform=win32
02-09 14:09 DEBUG  CommonBackend: osname=nt
02-09 14:09 DEBUG  CommonBackend: language=de_DE
02-09 14:09 DEBUG  CommonBackend: encoding=cp1252
02-09 14:09 DEBUG  WindowsBackend: arch=amd64
02-09 14:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\data\isolist.ini
02-09 14:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-09 14:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-09 14:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-09 14:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-09 14:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-09 14:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-09 14:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-09 14:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-09 14:09 DEBUG  WindowsBackend: Fetching host info...
02-09 14:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-09 14:09 DEBUG  WindowsBackend: windows version=vista
02-09 14:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-09 14:09 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-09 14:09 DEBUG  WindowsBackend: windows_build=7601
02-09 14:09 DEBUG  WindowsBackend: gmt=1
02-09 14:09 DEBUG  WindowsBackend: country=DE
02-09 14:09 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-09 14:09 DEBUG  WindowsBackend: windows_username=Schniedel
02-09 14:09 DEBUG  WindowsBackend: user_full_name=Schniedel
02-09 14:09 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-09 14:09 DEBUG  WindowsBackend: windows_language_code=1031
02-09 14:09 DEBUG  WindowsBackend: windows_language=German
02-09 14:09 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-09 14:09 DEBUG  WindowsBackend: bootloader=vista
02-09 14:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 176754.269531 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(C: hd 176754.269531 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.7734375 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.429688 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(G: removable 3553.53125 mb free fat32)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.28125 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.9179688 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.3242188 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.7539063 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free )
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(O: hd 328984.078125 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(T: hd 44937.921875 mb free ntfs)
02-09 14:09 DEBUG  WindowsBackend: drive=Drive(Z: hd 545799.75 mb free fat32)
02-09 14:09 DEBUG  WindowsBackend: uninstaller_path=None
02-09 14:09 DEBUG  WindowsBackend: previous_target_dir=None
02-09 14:09 DEBUG  WindowsBackend: previous_distro_name=None
02-09 14:09 DEBUG  WindowsBackend: keyboard_id=67699721
02-09 14:09 DEBUG  WindowsBackend: keyboard_layout=us
02-09 14:09 DEBUG  WindowsBackend: keyboard_variant=
02-09 14:09 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-09 14:09 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-09 14:09 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-09 14:09 DEBUG  CommonBackend: Searching ISOs on USB devices
02-09 14:09 DEBUG  CommonBackend: Searching for local CDs
02-09 14:09 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether O:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether O:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether O:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether O:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether O:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether O:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether O:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether O:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether T:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether T:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether T:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain T:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether Z:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether Z:\ is a valid Xubuntu CD
02-09 14:09 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:09 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
02-09 14:09 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:09 INFO   root: Running the installer...
02-09 14:09 DEBUG  WindowsFrontend: __init__...
02-09 14:09 DEBUG  WindowsFrontend: on_init...
02-09 14:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\translations, languages=['de_DE', 'de']
02-09 14:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\translations, languages=['de_DE', 'de']
02-09 14:10 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=schniedel
02-09 14:10 INFO   root: Received settings
02-09 14:10 DEBUG  CommonBackend: Searching for local CD
02-09 14:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether O:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 14:10 DEBUG  Distro:   checking whether T:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     dir does not exist
02-09 14:10 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-09 14:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 14:10 DEBUG  CommonBackend: Searching for local ISO
02-09 14:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\translations, languages=['en_US', 'en']
02-09 14:10 DEBUG  TaskList: # Running tasklist...
02-09 14:10 DEBUG  TaskList: ## Running select_target_dir...
02-09 14:10 INFO   WindowsBackend: Installing into C:\ubuntu
02-09 14:10 DEBUG  TaskList: ## Finished select_target_dir
02-09 14:10 DEBUG  TaskList: ## Running create_dir_structure...
02-09 14:10 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-09 14:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-09 14:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-09 14:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-09 14:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-09 14:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-09 14:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-09 14:10 DEBUG  TaskList: ## Finished create_dir_structure
02-09 14:10 DEBUG  TaskList: ## Running create_uninstaller...
02-09 14:10 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Schniedel\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-09 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-09 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-09 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-09 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-09 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-09 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-09 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-09 14:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-09 14:10 DEBUG  TaskList: ## Finished create_uninstaller
02-09 14:10 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-09 14:10 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-09 14:10 DEBUG  TaskList: ## Running get_diskimage...
02-09 14:10 DEBUG  TaskList: New task download
02-09 14:10 DEBUG  TaskList: ### Running download...
02-09 14:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-09 14:10 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-09 14:34 DEBUG  TaskList: ### Finished download
02-09 14:34 DEBUG  downloader: download finished (read 507143012 bytes)
02-09 14:34 DEBUG  TaskList: ## Finished get_diskimage
02-09 14:34 DEBUG  TaskList: ## Running extract_diskimage...
02-09 14:36 DEBUG  TaskList: ## Finished extract_diskimage
02-09 14:36 DEBUG  TaskList: ## Running choose_disk_sizes...
02-09 14:36 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-09 14:36 DEBUG  TaskList: ## Finished choose_disk_sizes
02-09 14:36 DEBUG  TaskList: ## Running expand_diskimage...
02-09 14:38 DEBUG  TaskList: ## Finished expand_diskimage
02-09 14:38 DEBUG  TaskList: ## Running create_swap_diskimage...
02-09 14:38 DEBUG  TaskList: ## Finished create_swap_diskimage
02-09 14:38 DEBUG  TaskList: ## Running modify_bootloader...
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 176754.269531 mb free ntfs)
02-09 14:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a}
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 1700.7734375 mb free ntfs)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(E: hd 476799.429688 mb free ntfs)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(G: removable 3553.53125 mb free fat32)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 53656.28125 mb free ntfs)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(I: hd 16477.9179688 mb free ntfs)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(J: hd 16724.3242188 mb free ntfs)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(K: hd 41302.7539063 mb free ntfs)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(O: hd 328984.078125 mb free ntfs)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(T: hd 44937.921875 mb free ntfs)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: New task modify_bcd
02-09 14:38 DEBUG  TaskList: ### Running modify_bcd...
02-09 14:38 DEBUG  WindowsBackend: modify_bcd Drive(Z: hd 545799.75 mb free fat32)
02-09 14:38 DEBUG  WindowsBackend: BCD has already been modified
02-09 14:38 DEBUG  TaskList: ### Finished modify_bcd
02-09 14:38 DEBUG  TaskList: ## Finished modify_bootloader
02-09 14:38 DEBUG  TaskList: ## Running diskimage_bootloader...
02-09 14:38 DEBUG  WindowsBackend: Copying C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\winboot -> C:\ubuntu\winboot
02-09 14:38 ERROR  TaskList: [Errno 2] No such file or directory: 'T:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'T:\\wubildr'
02-09 14:38 DEBUG  TaskList: # Cancelling tasklist
02-09 14:38 DEBUG  TaskList: # Finished tasklist
02-09 14:38 ERROR  root: [Errno 2] No such file or directory: 'T:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'T:\\wubildr'
02-09 15:14 INFO   root: === wubi 11.10 rev245 ===
02-09 15:14 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-09 15:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Schniedel\\Desktop\\wubi.exe"']
02-09 15:14 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\data
02-09 15:14 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\bin\7z.exe
02-09 15:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-09 15:14 DEBUG  CommonBackend: Fetching basic info...
02-09 15:14 DEBUG  CommonBackend: original_exe=C:\Users\Schniedel\Desktop\wubi.exe
02-09 15:14 DEBUG  CommonBackend: platform=win32
02-09 15:14 DEBUG  CommonBackend: osname=nt
02-09 15:14 DEBUG  CommonBackend: language=de_DE
02-09 15:14 DEBUG  CommonBackend: encoding=cp1252
02-09 15:14 DEBUG  WindowsBackend: arch=amd64
02-09 15:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\data\isolist.ini
02-09 15:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-09 15:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-09 15:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-09 15:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-09 15:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-09 15:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-09 15:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-09 15:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-09 15:14 DEBUG  WindowsBackend: Fetching host info...
02-09 15:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-09 15:14 DEBUG  WindowsBackend: windows version=vista
02-09 15:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-09 15:14 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-09 15:14 DEBUG  WindowsBackend: windows_build=7601
02-09 15:14 DEBUG  WindowsBackend: gmt=1
02-09 15:14 DEBUG  WindowsBackend: country=DE
02-09 15:14 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-09 15:14 DEBUG  WindowsBackend: windows_username=Schniedel
02-09 15:14 DEBUG  WindowsBackend: user_full_name=Schniedel
02-09 15:14 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-09 15:14 DEBUG  WindowsBackend: windows_language_code=1031
02-09 15:14 DEBUG  WindowsBackend: windows_language=German
02-09 15:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-09 15:14 DEBUG  WindowsBackend: bootloader=vista
02-09 15:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 173431.253906 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(C: hd 173431.253906 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(G: removable 3553.375 mb free fat32)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free )
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(O: hd 328983.949219 mb free ntfs)
02-09 15:14 DEBUG  WindowsBackend: drive=Drive(Z: hd 545799.75 mb free fat32)
02-09 15:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-09 15:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-09 15:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-09 15:14 DEBUG  WindowsBackend: keyboard_id=67699721
02-09 15:14 DEBUG  WindowsBackend: keyboard_layout=us
02-09 15:14 DEBUG  WindowsBackend: keyboard_variant=
02-09 15:14 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-09 15:14 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-09 15:14 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-09 15:14 DEBUG  CommonBackend: Searching ISOs on USB devices
02-09 15:14 DEBUG  CommonBackend: Searching for local CDs
02-09 15:14 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether O:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether O:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether O:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether O:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether O:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether O:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether O:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether O:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether Z:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether Z:\ is a valid Xubuntu CD
02-09 15:14 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:14 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
02-09 15:14 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:14 INFO   root: Already installed, running the uninstaller...
02-09 15:14 INFO   root: Running the uninstaller...
02-09 15:14 INFO   CommonBackend: This is the uninstaller running
02-09 15:14 DEBUG  WindowsFrontend: __init__...
02-09 15:14 DEBUG  WindowsFrontend: on_init...
02-09 15:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\translations, languages=['de_DE', 'de']
02-09 15:15 INFO   root: Received settings
02-09 15:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylF2C6.tmp\translations, languages=['de_DE', 'de']
02-09 15:15 DEBUG  TaskList: # Running tasklist...
02-09 15:15 DEBUG  TaskList: ## Running Bootloader-Eintrag wird entfernt...
02-09 15:15 DEBUG  WindowsBackend: Removing bcd entry {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a}
02-09 15:15 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-09 15:15 DEBUG  TaskList: # Cancelling tasklist
02-09 15:15 DEBUG  TaskList: # Finished tasklist
02-09 15:15 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 145, in run_installer
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-09 15:16 INFO   root: === wubi 11.10 rev245 ===
02-09 15:16 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-09 15:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Schniedel\\Desktop\\wubi.exe"']
02-09 15:16 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\data
02-09 15:16 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\bin\7z.exe
02-09 15:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-09 15:16 DEBUG  CommonBackend: Fetching basic info...
02-09 15:16 DEBUG  CommonBackend: original_exe=C:\Users\Schniedel\Desktop\wubi.exe
02-09 15:16 DEBUG  CommonBackend: platform=win32
02-09 15:16 DEBUG  CommonBackend: osname=nt
02-09 15:16 DEBUG  CommonBackend: language=de_DE
02-09 15:16 DEBUG  CommonBackend: encoding=cp1252
02-09 15:16 DEBUG  WindowsBackend: arch=amd64
02-09 15:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\data\isolist.ini
02-09 15:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-09 15:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-09 15:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-09 15:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-09 15:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-09 15:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-09 15:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-09 15:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-09 15:16 DEBUG  WindowsBackend: Fetching host info...
02-09 15:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-09 15:16 DEBUG  WindowsBackend: windows version=vista
02-09 15:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-09 15:16 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-09 15:16 DEBUG  WindowsBackend: windows_build=7601
02-09 15:16 DEBUG  WindowsBackend: gmt=1
02-09 15:16 DEBUG  WindowsBackend: country=DE
02-09 15:16 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-09 15:16 DEBUG  WindowsBackend: windows_username=Schniedel
02-09 15:16 DEBUG  WindowsBackend: user_full_name=Schniedel
02-09 15:16 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-09 15:16 DEBUG  WindowsBackend: windows_language_code=1031
02-09 15:16 DEBUG  WindowsBackend: windows_language=German
02-09 15:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-09 15:16 DEBUG  WindowsBackend: bootloader=vista
02-09 15:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 176518.15625 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(C: hd 176518.15625 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(G: removable 3553.375 mb free fat32)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free )
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(O: hd 328983.949219 mb free ntfs)
02-09 15:16 DEBUG  WindowsBackend: drive=Drive(Z: hd 545799.75 mb free fat32)
02-09 15:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-09 15:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-09 15:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-09 15:16 DEBUG  WindowsBackend: keyboard_id=67699721
02-09 15:16 DEBUG  WindowsBackend: keyboard_layout=us
02-09 15:16 DEBUG  WindowsBackend: keyboard_variant=
02-09 15:16 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-09 15:16 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-09 15:16 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-09 15:16 DEBUG  CommonBackend: Searching ISOs on USB devices
02-09 15:16 DEBUG  CommonBackend: Searching for local CDs
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Xubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 INFO   root: Running the installer...
02-09 15:16 DEBUG  WindowsFrontend: __init__...
02-09 15:16 DEBUG  WindowsFrontend: on_init...
02-09 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\translations, languages=['de_DE', 'de']
02-09 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\translations, languages=['de_DE', 'de']
02-09 15:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=de_DE, locale=de_DE.UTF-8, username=schniedel
02-09 15:16 INFO   root: Received settings
02-09 15:16 DEBUG  CommonBackend: Searching for local CD
02-09 15:16 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether O:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain O:\casper\filesystem.squashfs
02-09 15:16 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-09 15:16 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-09 15:16 DEBUG  CommonBackend: Searching for local ISO
02-09 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl195.tmp\translations, languages=['de_DE', 'de']
02-09 15:16 DEBUG  TaskList: # Running tasklist...
02-09 15:16 DEBUG  TaskList: ## Running select_target_dir...
02-09 15:16 INFO   WindowsBackend: Installing into C:\ubuntu
02-09 15:16 DEBUG  TaskList: ## Finished select_target_dir
02-09 15:16 DEBUG  TaskList: ## Running create_dir_structure...
02-09 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-09 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-09 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-09 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-09 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-09 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-09 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-09 15:16 DEBUG  TaskList: ## Finished create_dir_structure
02-09 15:16 DEBUG  TaskList: ## Running create_uninstaller...
02-09 15:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Schniedel\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-09 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-09 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-09 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-09 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-09 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-09 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-09 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-09 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-09 15:16 DEBUG  TaskList: ## Finished create_uninstaller
02-09 15:16 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-09 15:16 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-09 15:16 DEBUG  TaskList: ## Running get_diskimage...
02-09 15:16 DEBUG  TaskList: New task download
02-09 15:16 DEBUG  TaskList: ### Running download...
02-09 15:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-09 15:16 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-09 15:16 INFO   WindowsFrontend: Operation cancelled
02-09 15:16 DEBUG  WindowsFrontend: frontend.quit
02-09 15:16 DEBUG  WindowsFrontend: frontend.on_quit
02-09 15:16 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
02-09 15:16 DEBUG  TaskList: # Cancelling tasklist
02-09 15:16 DEBUG  downloader: download finished (read 9928704 bytes)
02-09 15:16 DEBUG  TaskList: ### Finished download
02-09 15:16 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
02-09 15:16 DEBUG  root: application.on_quit
02-09 15:16 DEBUG  root: Forceful exit
02-09 15:16 INFO   root: sys.exit
02-10 15:10 INFO   root: === wubi 11.10 rev245 ===
02-10 15:10 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-10 15:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-10 15:10 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\data
02-10 15:10 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\bin\7z.exe
02-10 15:10 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-10 15:10 DEBUG  CommonBackend: Fetching basic info...
02-10 15:10 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-10 15:10 DEBUG  CommonBackend: platform=win32
02-10 15:10 DEBUG  CommonBackend: osname=nt
02-10 15:10 DEBUG  CommonBackend: language=de_DE
02-10 15:10 DEBUG  CommonBackend: encoding=cp1252
02-10 15:10 DEBUG  WindowsBackend: arch=amd64
02-10 15:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\data\isolist.ini
02-10 15:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-10 15:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-10 15:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-10 15:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-10 15:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-10 15:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-10 15:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-10 15:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-10 15:10 DEBUG  WindowsBackend: Fetching host info...
02-10 15:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-10 15:10 DEBUG  WindowsBackend: windows version=vista
02-10 15:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-10 15:10 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-10 15:10 DEBUG  WindowsBackend: windows_build=7601
02-10 15:10 DEBUG  WindowsBackend: gmt=1
02-10 15:10 DEBUG  WindowsBackend: country=DE
02-10 15:10 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-10 15:10 DEBUG  WindowsBackend: windows_username=Schniedel
02-10 15:10 DEBUG  WindowsBackend: user_full_name=Schniedel
02-10 15:10 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-10 15:10 DEBUG  WindowsBackend: windows_language_code=1031
02-10 15:10 DEBUG  WindowsBackend: windows_language=German
02-10 15:10 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-10 15:10 DEBUG  WindowsBackend: bootloader=vista
02-10 15:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175226.375 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(C: hd 175226.375 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free )
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(O: hd 326667.988281 mb free ntfs)
02-10 15:10 DEBUG  WindowsBackend: drive=Drive(Z: hd 271651.0 mb free fat32)
02-10 15:10 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-10 15:10 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-10 15:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-10 15:10 DEBUG  WindowsBackend: keyboard_id=67699721
02-10 15:10 DEBUG  WindowsBackend: keyboard_layout=us
02-10 15:10 DEBUG  WindowsBackend: keyboard_variant=
02-10 15:10 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-10 15:10 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-10 15:10 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-10 15:10 DEBUG  CommonBackend: Searching ISOs on USB devices
02-10 15:10 DEBUG  CommonBackend: Searching for local CDs
02-10 15:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain O:\TV\GrabIt Downloads\Barry Eisler   Requiem for an Assassin\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether Z:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether Z:\ is a valid Xubuntu CD
02-10 15:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-10 15:10 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
02-10 15:10 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
02-10 15:10 INFO   root: Running the uninstaller...
02-10 15:10 INFO   CommonBackend: This is the uninstaller running
02-10 15:10 DEBUG  WindowsFrontend: __init__...
02-10 15:10 DEBUG  WindowsFrontend: on_init...
02-10 15:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\translations, languages=['de_DE', 'de']
02-10 15:10 INFO   root: Received settings
02-10 15:10 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEA10.tmp\translations, languages=['de_DE', 'de']
02-10 15:10 DEBUG  TaskList: # Running tasklist...
02-10 15:10 DEBUG  TaskList: ## Running Bootloader-Eintrag wird entfernt...
02-10 15:10 DEBUG  WindowsBackend: Removing bcd entry {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a}
02-10 15:10 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-10 15:10 DEBUG  TaskList: # Cancelling tasklist
02-10 15:10 DEBUG  TaskList: # Finished tasklist
02-10 15:10 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-10 15:18 INFO   root: === wubi 11.10 rev245 ===
02-10 15:18 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-10 15:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
02-10 15:18 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\data
02-10 15:18 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\bin\7z.exe
02-10 15:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-10 15:18 DEBUG  CommonBackend: Fetching basic info...
02-10 15:18 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-10 15:18 DEBUG  CommonBackend: platform=win32
02-10 15:18 DEBUG  CommonBackend: osname=nt
02-10 15:18 DEBUG  CommonBackend: language=de_DE
02-10 15:18 DEBUG  CommonBackend: encoding=cp1252
02-10 15:18 DEBUG  WindowsBackend: arch=amd64
02-10 15:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\data\isolist.ini
02-10 15:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-10 15:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-10 15:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-10 15:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-10 15:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-10 15:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-10 15:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-10 15:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-10 15:18 DEBUG  WindowsBackend: Fetching host info...
02-10 15:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-10 15:18 DEBUG  WindowsBackend: windows version=vista
02-10 15:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-10 15:18 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-10 15:18 DEBUG  WindowsBackend: windows_build=7601
02-10 15:18 DEBUG  WindowsBackend: gmt=1
02-10 15:18 DEBUG  WindowsBackend: country=DE
02-10 15:18 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-10 15:18 DEBUG  WindowsBackend: windows_username=Schniedel
02-10 15:18 DEBUG  WindowsBackend: user_full_name=Schniedel
02-10 15:18 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-10 15:18 DEBUG  WindowsBackend: windows_language_code=1031
02-10 15:18 DEBUG  WindowsBackend: windows_language=German
02-10 15:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-10 15:18 DEBUG  WindowsBackend: bootloader=vista
02-10 15:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175209.15625 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(C: hd 175209.15625 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(O: hd 326440.035156 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(Z: hd 271651.0 mb free fat32)
02-10 15:18 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-10 15:18 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-10 15:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-10 15:18 DEBUG  WindowsBackend: keyboard_id=67699721
02-10 15:18 DEBUG  WindowsBackend: keyboard_layout=us
02-10 15:18 DEBUG  WindowsBackend: keyboard_variant=
02-10 15:18 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-10 15:18 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-10 15:18 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-10 15:18 DEBUG  CommonBackend: Searching ISOs on USB devices
02-10 15:18 DEBUG  CommonBackend: Searching for local CDs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
02-10 15:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
02-10 15:18 INFO   Distro: Found a valid CD for Ubuntu: N:\
02-10 15:18 INFO   root: Running the uninstaller...
02-10 15:18 INFO   CommonBackend: This is the uninstaller running
02-10 15:18 DEBUG  WindowsFrontend: __init__...
02-10 15:18 DEBUG  WindowsFrontend: on_init...
02-10 15:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\translations, languages=['de_DE', 'de']
02-10 15:18 INFO   root: Received settings
02-10 15:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl9B74.tmp\translations, languages=['de_DE', 'de']
02-10 15:18 DEBUG  TaskList: # Running tasklist...
02-10 15:18 DEBUG  TaskList: ## Running Bootloader-Eintrag wird entfernt...
02-10 15:18 DEBUG  WindowsBackend: Removing bcd entry {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a}
02-10 15:18 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-10 15:18 DEBUG  TaskList: # Cancelling tasklist
02-10 15:18 DEBUG  TaskList: # Finished tasklist
02-10 15:18 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-10 15:19 INFO   root: === wubi 11.10 rev245 ===
02-10 15:19 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-10 15:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
02-10 15:19 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\data
02-10 15:19 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\bin\7z.exe
02-10 15:19 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-10 15:19 DEBUG  CommonBackend: Fetching basic info...
02-10 15:19 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-10 15:19 DEBUG  CommonBackend: platform=win32
02-10 15:19 DEBUG  CommonBackend: osname=nt
02-10 15:19 DEBUG  CommonBackend: language=de_DE
02-10 15:19 DEBUG  CommonBackend: encoding=cp1252
02-10 15:19 DEBUG  WindowsBackend: arch=amd64
02-10 15:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\data\isolist.ini
02-10 15:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-10 15:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-10 15:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-10 15:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-10 15:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-10 15:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-10 15:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-10 15:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-10 15:19 DEBUG  WindowsBackend: Fetching host info...
02-10 15:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-10 15:19 DEBUG  WindowsBackend: windows version=vista
02-10 15:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-10 15:19 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-10 15:19 DEBUG  WindowsBackend: windows_build=7601
02-10 15:19 DEBUG  WindowsBackend: gmt=1
02-10 15:19 DEBUG  WindowsBackend: country=DE
02-10 15:19 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-10 15:19 DEBUG  WindowsBackend: windows_username=Schniedel
02-10 15:19 DEBUG  WindowsBackend: user_full_name=Schniedel
02-10 15:19 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-10 15:19 DEBUG  WindowsBackend: windows_language_code=1031
02-10 15:19 DEBUG  WindowsBackend: windows_language=German
02-10 15:19 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-10 15:19 DEBUG  WindowsBackend: bootloader=vista
02-10 15:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175208.433594 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(C: hd 175208.433594 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(O: hd 326419.183594 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(Z: hd 271651.0 mb free fat32)
02-10 15:19 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-10 15:19 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-10 15:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-10 15:19 DEBUG  WindowsBackend: keyboard_id=67699721
02-10 15:19 DEBUG  WindowsBackend: keyboard_layout=us
02-10 15:19 DEBUG  WindowsBackend: keyboard_variant=
02-10 15:19 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-10 15:19 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-10 15:19 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-10 15:19 DEBUG  CommonBackend: Searching ISOs on USB devices
02-10 15:19 DEBUG  CommonBackend: Searching for local CDs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
02-10 15:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
02-10 15:19 INFO   Distro: Found a valid CD for Ubuntu: N:\
02-10 15:19 INFO   root: Running the uninstaller...
02-10 15:19 INFO   CommonBackend: This is the uninstaller running
02-10 15:19 DEBUG  WindowsFrontend: __init__...
02-10 15:19 DEBUG  WindowsFrontend: on_init...
02-10 15:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\translations, languages=['de_DE', 'de']
02-10 15:19 INFO   root: Received settings
02-10 15:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylEEE.tmp\translations, languages=['de_DE', 'de']
02-10 15:19 DEBUG  TaskList: # Running tasklist...
02-10 15:19 DEBUG  TaskList: ## Running Bootloader-Eintrag wird entfernt...
02-10 15:19 DEBUG  WindowsBackend: Removing bcd entry {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a}
02-10 15:19 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-10 15:19 DEBUG  TaskList: # Cancelling tasklist
02-10 15:19 DEBUG  TaskList: # Finished tasklist
02-10 15:19 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-10 15:20 INFO   root: === wubi 11.10 rev245 ===
02-10 15:20 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-10 15:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-10 15:20 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\data
02-10 15:20 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\bin\7z.exe
02-10 15:20 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-10 15:20 DEBUG  CommonBackend: Fetching basic info...
02-10 15:20 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-10 15:20 DEBUG  CommonBackend: platform=win32
02-10 15:20 DEBUG  CommonBackend: osname=nt
02-10 15:20 DEBUG  CommonBackend: language=de_DE
02-10 15:20 DEBUG  CommonBackend: encoding=cp1252
02-10 15:20 DEBUG  WindowsBackend: arch=amd64
02-10 15:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\data\isolist.ini
02-10 15:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-10 15:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-10 15:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-10 15:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-10 15:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-10 15:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-10 15:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-10 15:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-10 15:20 DEBUG  WindowsBackend: Fetching host info...
02-10 15:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-10 15:20 DEBUG  WindowsBackend: windows version=vista
02-10 15:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-10 15:20 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-10 15:20 DEBUG  WindowsBackend: windows_build=7601
02-10 15:20 DEBUG  WindowsBackend: gmt=1
02-10 15:20 DEBUG  WindowsBackend: country=DE
02-10 15:20 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-10 15:20 DEBUG  WindowsBackend: windows_username=Schniedel
02-10 15:20 DEBUG  WindowsBackend: user_full_name=Schniedel
02-10 15:20 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-10 15:20 DEBUG  WindowsBackend: windows_language_code=1031
02-10 15:20 DEBUG  WindowsBackend: windows_language=German
02-10 15:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-10 15:20 DEBUG  WindowsBackend: bootloader=vista
02-10 15:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175208.785156 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(C: hd 175208.785156 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(O: hd 326456.015625 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(Z: hd 271651.0 mb free fat32)
02-10 15:20 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-10 15:20 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-10 15:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-10 15:20 DEBUG  WindowsBackend: keyboard_id=67699721
02-10 15:20 DEBUG  WindowsBackend: keyboard_layout=us
02-10 15:20 DEBUG  WindowsBackend: keyboard_variant=
02-10 15:20 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-10 15:20 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-10 15:20 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-10 15:20 DEBUG  CommonBackend: Searching ISOs on USB devices
02-10 15:20 DEBUG  CommonBackend: Searching for local CDs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
02-10 15:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
02-10 15:20 INFO   Distro: Found a valid CD for Ubuntu: N:\
02-10 15:20 INFO   root: Running the uninstaller...
02-10 15:20 INFO   CommonBackend: This is the uninstaller running
02-10 15:20 DEBUG  WindowsFrontend: __init__...
02-10 15:20 DEBUG  WindowsFrontend: on_init...
02-10 15:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl691E.tmp\translations, languages=['de_DE', 'de']
02-10 15:20 INFO   root: === wubi 11.10 rev245 ===
02-10 15:20 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-10 15:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-10 15:20 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\data
02-10 15:20 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\bin\7z.exe
02-10 15:20 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-10 15:20 DEBUG  CommonBackend: Fetching basic info...
02-10 15:20 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-10 15:20 DEBUG  CommonBackend: platform=win32
02-10 15:20 DEBUG  CommonBackend: osname=nt
02-10 15:20 DEBUG  CommonBackend: language=de_DE
02-10 15:20 DEBUG  CommonBackend: encoding=cp1252
02-10 15:20 DEBUG  WindowsBackend: arch=amd64
02-10 15:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\data\isolist.ini
02-10 15:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-10 15:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-10 15:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-10 15:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-10 15:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-10 15:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-10 15:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-10 15:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-10 15:20 DEBUG  WindowsBackend: Fetching host info...
02-10 15:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-10 15:20 DEBUG  WindowsBackend: windows version=vista
02-10 15:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-10 15:20 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-10 15:20 DEBUG  WindowsBackend: windows_build=7601
02-10 15:20 DEBUG  WindowsBackend: gmt=1
02-10 15:20 DEBUG  WindowsBackend: country=DE
02-10 15:20 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-10 15:20 DEBUG  WindowsBackend: windows_username=Schniedel
02-10 15:20 DEBUG  WindowsBackend: user_full_name=Schniedel
02-10 15:20 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-10 15:20 DEBUG  WindowsBackend: windows_language_code=1031
02-10 15:20 DEBUG  WindowsBackend: windows_language=German
02-10 15:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-10 15:20 DEBUG  WindowsBackend: bootloader=vista
02-10 15:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175209.234375 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(C: hd 175209.234375 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(O: hd 326495.582031 mb free ntfs)
02-10 15:20 DEBUG  WindowsBackend: drive=Drive(Z: hd 271651.0 mb free fat32)
02-10 15:20 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-10 15:20 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-10 15:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-10 15:20 DEBUG  WindowsBackend: keyboard_id=67699721
02-10 15:20 DEBUG  WindowsBackend: keyboard_layout=us
02-10 15:20 DEBUG  WindowsBackend: keyboard_variant=
02-10 15:20 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-10 15:20 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-10 15:20 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-10 15:20 DEBUG  CommonBackend: Searching ISOs on USB devices
02-10 15:20 DEBUG  CommonBackend: Searching for local CDs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:20 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:20 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-10 15:20 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
02-10 15:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
02-10 15:20 INFO   Distro: Found a valid CD for Ubuntu: N:\
02-10 15:20 INFO   root: Running the uninstaller...
02-10 15:20 INFO   CommonBackend: This is the uninstaller running
02-10 15:20 DEBUG  WindowsFrontend: __init__...
02-10 15:20 DEBUG  WindowsFrontend: on_init...
02-10 15:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\translations, languages=['de_DE', 'de']
02-10 15:21 INFO   root: Received settings
02-10 15:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylA2C4.tmp\translations, languages=['de_DE', 'de']
02-10 15:21 DEBUG  TaskList: # Running tasklist...
02-10 15:21 DEBUG  TaskList: ## Running Bootloader-Eintrag wird entfernt...
02-10 15:21 DEBUG  WindowsBackend: Removing bcd entry {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a}
02-10 15:21 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
02-10 15:21 DEBUG  TaskList: # Cancelling tasklist
02-10 15:21 DEBUG  TaskList: # Finished tasklist
02-10 15:21 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 562, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 746, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9ee7bb03-0677-11e0-83f2-ca4484ddcb0a} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
```

---

### Post by C.S.Cameron on 2012-02-11
Boot from the Live CD, start gparted and check what partitions you have on sda.

Is there an ext partition "/" ? If not, you probably installed to the USB.
Plug in your USB drive and in BIOS select it as your first HDD, then boot. 

If you want to install Ubuntu to dual boot next to Win 7, boot your CD and select install.

---

### Post by ottosykora on 2012-02-11
But this seems to be a wubi installation.

How exactly did you install linux? Executing some program under windows and installing it from a CD or iso?
Where was the installation going? In general wubi will make some advise as where is would fit, so far I have not met it will install on a usb drive, but I did not use it for long time.

Note, that wubi will not produce any partitions, it just produces virtual drives and they are just files on your hard drive.

To unistall wubi , you simply go to the windows place for unistalling programs and run the wubi unistall.
If you still find the disk files around, then you can delet them manually.

Should the wubi install its parts to an usb drive, well the drive has to be there and running during the operation.

---

### Post by Kraut55 on 2012-02-12
As I mentioned I did the install from a CD. Everything went automatically (apart from the prompts like keyboard etc.). So maybe wubi was wrong. I just assumed that would be the correct title.

It was definitely installed on the USB. I solved my problem now by using the Windows Disk Management where I just formatted the partition where Ubuntu had been installed. I guess this concludes my excursion into the world of Linux.

Thanj you for your help.

---

### Post by Deuce1912 on 2012-02-12
Oh I really hope your not going to give up on Linux that easy. Its an amazing operating system that is easier (In my opinion) to use and operate/maintain than Windows.

I due hope you will give Linux another try. As with anything new there is a learning curve.

- Deuce1912

---

### Post by ottosykora on 2012-02-12
> **Kraut55 said:**
> As I mentioned I did the install from a CD. Everything went automatically (apart from the prompts like keyboard etc.). So maybe wubi was wrong. I just assumed that would be the correct title.

It was definitely installed on the USB. I solved my problem now by using the Windows Disk Management where I just formatted the partition where Ubuntu had been installed. I guess this concludes my excursion into the world of Linux.

Thanj you for your help.

The log you included was concerning some wubi install, so this is what made the confusion.
Installation with wubi (windows software) will produce virtual drive installation located on your hard drive

Installation on usb device is possible, but more involved then starting the CD and is not so preferred as it works then rather slow over a usb2 connection.


```
02-09 14:09 INFO   root: === wubi 11.10 rev245 ===
02-09 14:09 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev245.log
02-09 14:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Schniedel\\Desktop\\wubi.exe"']
02-09 14:09 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\data
02-09 14:09 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl5A4F.tmp\bin\7z.exe
02-09 14:09 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-09 14:09 DEBUG  CommonBackend: Fetching basic info...
02-09 14:09 DEBUG  CommonBackend: original_exe=C:\Users\Schniedel\Desktop\wubi.exe
02-09 14:09 DEBUG  CommonBackend: platform=win32
```

---

### Post by Kraut55 on 2012-02-12
Before using the CD I had tried using a setup file from the Windows desktop. When I received an error message there (some file could not be found) I erased everything and assumed there was no trace left when I started the CD. Sorry for the confusion.
When I have time I will try again with the virtual disk.
Thanks again.
Kraut55

---

### Post by Kraut55 on 2012-02-12
I tried it again. This time from the Windows 7 desktop. I used the CD and picked the 2nd menu item (Installation from within Windows).
Again an error. Here is the log:


02-09 23:37 INFO   root: === wubi 11.10 rev241 ===
02-09 23:37 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev241.log
02-09 23:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="N:\\wubi.exe"']
02-09 23:37 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\data
02-09 23:37 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\bin\7z.exe
02-09 23:37 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-09 23:37 DEBUG  CommonBackend: Fetching basic info...
02-09 23:37 DEBUG  CommonBackend: original_exe=N:\wubi.exe
02-09 23:37 DEBUG  CommonBackend: platform=win32
02-09 23:37 DEBUG  CommonBackend: osname=nt
02-09 23:37 DEBUG  CommonBackend: language=de_DE
02-09 23:37 DEBUG  CommonBackend: encoding=cp1252
02-09 23:37 DEBUG  WindowsBackend: arch=amd64
02-09 23:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\data\isolist.ini
02-09 23:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-09 23:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-09 23:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-09 23:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-09 23:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-09 23:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-09 23:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-09 23:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-09 23:37 DEBUG  WindowsBackend: Fetching host info...
02-09 23:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-09 23:37 DEBUG  WindowsBackend: windows version=vista
02-09 23:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-09 23:37 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-09 23:37 DEBUG  WindowsBackend: windows_build=7601
02-09 23:37 DEBUG  WindowsBackend: gmt=1
02-09 23:37 DEBUG  WindowsBackend: country=DE
02-09 23:37 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-09 23:37 DEBUG  WindowsBackend: windows_username=Schniedel
02-09 23:37 DEBUG  WindowsBackend: user_full_name=Schniedel
02-09 23:37 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-09 23:37 DEBUG  WindowsBackend: windows_language_code=1031
02-09 23:37 DEBUG  WindowsBackend: windows_language=German
02-09 23:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-09 23:37 DEBUG  WindowsBackend: bootloader=vista
02-09 23:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175348.277344 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(C: hd 175348.277344 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(O: hd 326666.988281 mb free ntfs)
02-09 23:37 DEBUG  WindowsBackend: drive=Drive(Z: hd 545799.75 mb free fat32)
02-09 23:37 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-09 23:37 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-09 23:37 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-09 23:37 DEBUG  WindowsBackend: keyboard_id=67699721
02-09 23:37 DEBUG  WindowsBackend: keyboard_layout=us
02-09 23:37 DEBUG  WindowsBackend: keyboard_variant=
02-09 23:37 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-09 23:37 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-09 23:37 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-09 23:37 DEBUG  CommonBackend: Searching ISOs on USB devices
02-09 23:37 DEBUG  CommonBackend: Searching for local CDs
02-09 23:37 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-09 23:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-09 23:37 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-09 23:37 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-09 23:37 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
02-09 23:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
02-09 23:37 INFO   Distro: Found a valid CD for Ubuntu: N:\
02-09 23:37 INFO   root: Running the CD menu...
02-09 23:37 DEBUG  WindowsFrontend: __init__...
02-09 23:37 DEBUG  WindowsFrontend: on_init...
02-09 23:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\translations, languages=['de_DE', 'de']
02-09 23:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl2342.tmp\translations, languages=['de_DE', 'de']
02-09 23:38 DEBUG  root: application.quit
02-09 23:38 DEBUG  WindowsFrontend: frontend.quit
02-09 23:38 DEBUG  WindowsFrontend: frontend.on_quit
02-09 23:38 DEBUG  root: application.on_quit
02-09 23:38 INFO   root: sys.exit
02-10 15:18 INFO   root: === wubi 11.10 rev241 ===
02-10 15:18 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev241.log
02-10 15:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="N:\\wubi.exe"', '--cdmenu']
02-10 15:18 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\data
02-10 15:18 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\bin\7z.exe
02-10 15:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-10 15:18 DEBUG  CommonBackend: Fetching basic info...
02-10 15:18 DEBUG  CommonBackend: original_exe=N:\wubi.exe
02-10 15:18 DEBUG  CommonBackend: platform=win32
02-10 15:18 DEBUG  CommonBackend: osname=nt
02-10 15:18 DEBUG  CommonBackend: language=de_DE
02-10 15:18 DEBUG  CommonBackend: encoding=cp1252
02-10 15:18 DEBUG  WindowsBackend: arch=amd64
02-10 15:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\data\isolist.ini
02-10 15:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-10 15:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-10 15:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-10 15:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-10 15:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-10 15:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-10 15:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-10 15:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-10 15:18 DEBUG  WindowsBackend: Fetching host info...
02-10 15:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-10 15:18 DEBUG  WindowsBackend: windows version=vista
02-10 15:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-10 15:18 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-10 15:18 DEBUG  WindowsBackend: windows_build=7601
02-10 15:18 DEBUG  WindowsBackend: gmt=1
02-10 15:18 DEBUG  WindowsBackend: country=DE
02-10 15:18 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-10 15:18 DEBUG  WindowsBackend: windows_username=Schniedel
02-10 15:18 DEBUG  WindowsBackend: user_full_name=Schniedel
02-10 15:18 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-10 15:18 DEBUG  WindowsBackend: windows_language_code=1031
02-10 15:18 DEBUG  WindowsBackend: windows_language=German
02-10 15:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-10 15:18 DEBUG  WindowsBackend: bootloader=vista
02-10 15:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175218.992188 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(C: hd 175218.992188 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(O: hd 326448.242188 mb free ntfs)
02-10 15:18 DEBUG  WindowsBackend: drive=Drive(Z: hd 271651.0 mb free fat32)
02-10 15:18 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-10 15:18 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-10 15:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-10 15:18 DEBUG  WindowsBackend: keyboard_id=67699721
02-10 15:18 DEBUG  WindowsBackend: keyboard_layout=us
02-10 15:18 DEBUG  WindowsBackend: keyboard_variant=
02-10 15:18 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-10 15:18 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-10 15:18 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-10 15:18 DEBUG  CommonBackend: Searching ISOs on USB devices
02-10 15:18 DEBUG  CommonBackend: Searching for local CDs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:18 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:18 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-10 15:18 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
02-10 15:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
02-10 15:18 INFO   Distro: Found a valid CD for Ubuntu: N:\
02-10 15:18 INFO   root: Running the CD menu...
02-10 15:18 DEBUG  WindowsFrontend: __init__...
02-10 15:18 DEBUG  WindowsFrontend: on_init...
02-10 15:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\translations, languages=['de_DE', 'de']
02-10 15:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pyl6815.tmp\translations, languages=['de_DE', 'de']
02-10 15:18 INFO   root: CD menu finished
02-10 15:18 INFO   root: Already installed, running the uninstaller...
02-10 15:18 INFO   root: Running the uninstaller...
02-10 15:18 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
02-10 15:18 DEBUG  root: application.quit
02-10 15:18 DEBUG  WindowsFrontend: frontend.quit
02-10 15:18 DEBUG  WindowsFrontend: frontend.on_quit
02-10 15:18 DEBUG  root: application.on_quit
02-10 15:18 INFO   root: sys.exit
02-10 15:19 INFO   root: === wubi 11.10 rev241 ===
02-10 15:19 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev241.log
02-10 15:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="N:\\wubi.exe"']
02-10 15:19 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\data
02-10 15:19 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\bin\7z.exe
02-10 15:19 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-10 15:19 DEBUG  CommonBackend: Fetching basic info...
02-10 15:19 DEBUG  CommonBackend: original_exe=N:\wubi.exe
02-10 15:19 DEBUG  CommonBackend: platform=win32
02-10 15:19 DEBUG  CommonBackend: osname=nt
02-10 15:19 DEBUG  CommonBackend: language=de_DE
02-10 15:19 DEBUG  CommonBackend: encoding=cp1252
02-10 15:19 DEBUG  WindowsBackend: arch=amd64
02-10 15:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\data\isolist.ini
02-10 15:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-10 15:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-10 15:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-10 15:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-10 15:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-10 15:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-10 15:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-10 15:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-10 15:19 DEBUG  WindowsBackend: Fetching host info...
02-10 15:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-10 15:19 DEBUG  WindowsBackend: windows version=vista
02-10 15:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-10 15:19 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-10 15:19 DEBUG  WindowsBackend: windows_build=7601
02-10 15:19 DEBUG  WindowsBackend: gmt=1
02-10 15:19 DEBUG  WindowsBackend: country=DE
02-10 15:19 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-10 15:19 DEBUG  WindowsBackend: windows_username=Schniedel
02-10 15:19 DEBUG  WindowsBackend: user_full_name=Schniedel
02-10 15:19 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-10 15:19 DEBUG  WindowsBackend: windows_language_code=1031
02-10 15:19 DEBUG  WindowsBackend: windows_language=German
02-10 15:19 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-10 15:19 DEBUG  WindowsBackend: bootloader=vista
02-10 15:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 175217.714844 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(C: hd 175217.714844 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(F: hd 197137.054688 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1523438 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(I: hd 16477.7890625 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(L: hd 51132.8164063 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(M: hd 2228.90625 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(O: hd 326423.269531 mb free ntfs)
02-10 15:19 DEBUG  WindowsBackend: drive=Drive(Z: hd 271651.0 mb free fat32)
02-10 15:19 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-10 15:19 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-10 15:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-10 15:19 DEBUG  WindowsBackend: keyboard_id=67699721
02-10 15:19 DEBUG  WindowsBackend: keyboard_layout=us
02-10 15:19 DEBUG  WindowsBackend: keyboard_variant=
02-10 15:19 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-10 15:19 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-10 15:19 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-10 15:19 DEBUG  CommonBackend: Searching ISOs on USB devices
02-10 15:19 DEBUG  CommonBackend: Searching for local CDs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Kubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Xubuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether M:\ is a valid Mythbuntu CD
02-10 15:19 DEBUG  Distro:     does not contain M:\casper\filesystem.squashfs
02-10 15:19 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-10 15:19 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
02-10 15:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
02-10 15:19 INFO   Distro: Found a valid CD for Ubuntu: N:\
02-10 15:19 INFO   root: Running the CD menu...
02-10 15:19 DEBUG  WindowsFrontend: __init__...
02-10 15:19 DEBUG  WindowsFrontend: on_init...
02-10 15:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\translations, languages=['de_DE', 'de']
02-10 15:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylFB5E.tmp\translations, languages=['de_DE', 'de']
02-10 15:19 INFO   root: CD menu finished
02-10 15:19 INFO   root: Already installed, running the uninstaller...
02-10 15:19 INFO   root: Running the uninstaller...
02-10 15:19 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
02-10 15:19 DEBUG  root: application.quit
02-10 15:19 DEBUG  WindowsFrontend: frontend.quit
02-10 15:19 DEBUG  WindowsFrontend: frontend.on_quit
02-10 15:19 DEBUG  root: application.on_quit
02-10 15:19 INFO   root: sys.exit
02-12 21:24 INFO   root: === wubi 11.10 rev241 ===
02-12 21:24 DEBUG  root: Logfile is c:\users\schnie~1\appdata\local\temp\wubi-11.10-rev241.log
02-12 21:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="N:\\wubi.exe"', '--cdmenu']
02-12 21:24 DEBUG  CommonBackend: data_dir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\data
02-12 21:24 DEBUG  WindowsBackend: 7z=C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\bin\7z.exe
02-12 21:24 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-12 21:24 DEBUG  CommonBackend: Fetching basic info...
02-12 21:24 DEBUG  CommonBackend: original_exe=N:\wubi.exe
02-12 21:24 DEBUG  CommonBackend: platform=win32
02-12 21:24 DEBUG  CommonBackend: osname=nt
02-12 21:24 DEBUG  CommonBackend: language=de_DE
02-12 21:24 DEBUG  CommonBackend: encoding=cp1252
02-12 21:24 DEBUG  WindowsBackend: arch=amd64
02-12 21:24 DEBUG  CommonBackend: Parsing isolist=C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\data\isolist.ini
02-12 21:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-12 21:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-12 21:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-12 21:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-12 21:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-12 21:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-12 21:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-12 21:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-12 21:24 DEBUG  WindowsBackend: Fetching host info...
02-12 21:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-12 21:24 DEBUG  WindowsBackend: windows version=vista
02-12 21:24 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-12 21:24 DEBUG  WindowsBackend: windows_sp=Service Pack 1
02-12 21:24 DEBUG  WindowsBackend: windows_build=7601
02-12 21:24 DEBUG  WindowsBackend: gmt=1
02-12 21:24 DEBUG  WindowsBackend: country=DE
02-12 21:24 DEBUG  WindowsBackend: timezone=Europe/Berlin
02-12 21:24 DEBUG  WindowsBackend: windows_username=Schniedel
02-12 21:24 DEBUG  WindowsBackend: user_full_name=Schniedel
02-12 21:24 DEBUG  WindowsBackend: user_directory=C:\Users\Schniedel
02-12 21:24 DEBUG  WindowsBackend: windows_language_code=1031
02-12 21:24 DEBUG  WindowsBackend: windows_language=German
02-12 21:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
02-12 21:24 DEBUG  WindowsBackend: bootloader=vista
02-12 21:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 176943.949219 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(C: hd 176943.949219 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(D: hd 1700.64453125 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(E: hd 476799.296875 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(H: hd 53656.1328125 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(I: hd 18346.1757813 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(J: hd 16724.1953125 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(K: hd 41302.625 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(N: cd 0.0 mb free cdfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(O: hd 315295.019531 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(Y: hd 274136.378906 mb free ntfs)
02-12 21:24 DEBUG  WindowsBackend: drive=Drive(Z: hd 271651.0 mb free fat32)
02-12 21:24 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-12 21:24 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-12 21:24 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-12 21:24 DEBUG  WindowsBackend: keyboard_id=67699721
02-12 21:24 DEBUG  WindowsBackend: keyboard_layout=us
02-12 21:24 DEBUG  WindowsBackend: keyboard_variant=
02-12 21:24 DEBUG  CommonBackend: python locale=('de_DE', 'cp1252')
02-12 21:24 DEBUG  CommonBackend: locale=de_DE.UTF-8
02-12 21:24 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-12 21:24 DEBUG  CommonBackend: Searching ISOs on USB devices
02-12 21:24 DEBUG  CommonBackend: Searching for local CDs
02-12 21:24 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
02-12 21:24 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
02-12 21:24 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
02-12 21:24 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-12 21:24 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
02-12 21:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
02-12 21:24 INFO   Distro: Found a valid CD for Ubuntu: N:\
02-12 21:24 INFO   root: Running the CD menu...
02-12 21:24 DEBUG  WindowsFrontend: __init__...
02-12 21:24 DEBUG  WindowsFrontend: on_init...
02-12 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\translations, languages=['de_DE', 'de']
02-12 21:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\translations, languages=['de_DE', 'de']
02-12 21:25 INFO   root: CD menu finished
02-12 21:25 INFO   root: Running the installer...
02-12 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\translations, languages=['de_DE', 'de']
02-12 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\translations, languages=['de_DE', 'de']
02-12 21:25 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=schniedel
02-12 21:25 INFO   root: Received settings
02-12 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\translations, languages=['en_US', 'en']
02-12 21:25 DEBUG  TaskList: # Running tasklist...
02-12 21:25 DEBUG  TaskList: ## Running select_target_dir...
02-12 21:25 INFO   WindowsBackend: Installing into C:\ubuntu
02-12 21:25 DEBUG  TaskList: ## Finished select_target_dir
02-12 21:25 DEBUG  TaskList: ## Running create_dir_structure...
02-12 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-12 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-12 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-12 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-12 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-12 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-12 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-12 21:25 DEBUG  TaskList: ## Finished create_dir_structure
02-12 21:25 DEBUG  TaskList: ## Running uncompress_target_dir...
02-12 21:25 DEBUG  TaskList: ## Finished uncompress_target_dir
02-12 21:25 DEBUG  TaskList: ## Running create_uninstaller...
02-12 21:25 DEBUG  WindowsBackend: Copying uninstaller N:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-12 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-12 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-12 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-12 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-12 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
02-12 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-12 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
02-12 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-12 21:25 DEBUG  TaskList: ## Finished create_uninstaller
02-12 21:25 DEBUG  TaskList: ## Running copy_installation_files...
02-12 21:25 DEBUG  WindowsBackend: Copying C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
02-12 21:25 DEBUG  WindowsBackend: Copying C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\winboot -> C:\ubuntu\winboot
02-12 21:25 DEBUG  WindowsBackend: Copying C:\Users\SCHNIE~1\AppData\Local\Temp\pylBC8C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
02-12 21:25 DEBUG  TaskList: ## Finished copy_installation_files
02-12 21:25 DEBUG  TaskList: ## Running get_iso...
02-12 21:25 DEBUG  TaskList: New task copy_file
02-12 21:25 DEBUG  TaskList: ### Running copy_file...
02-12 21:28 DEBUG  TaskList: ### Finished copy_file
02-12 21:28 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 13] Permission denied
02-12 21:28 DEBUG  TaskList: # Cancelling tasklist
02-12 21:28 DEBUG  TaskList: New task check_iso
02-12 21:28 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 202, in copy_file
IOError: [Errno 13] Permission denied
02-12 21:28 ERROR  TaskList: 'WindowsBackend' object has no attribute 'iso_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 579, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 565, in use_iso
AttributeError: 'WindowsBackend' object has no attribute 'iso_path'
02-12 21:28 DEBUG  TaskList: # Cancelling tasklist
02-12 21:28 DEBUG  TaskList: # Finished tasklist

---

