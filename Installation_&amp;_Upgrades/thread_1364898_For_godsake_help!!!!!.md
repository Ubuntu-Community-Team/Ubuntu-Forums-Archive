---
title: "For godsake help!!!!!"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by furqanbhai on 2009-12-26
I have downloaded ubuntu 9.10 first from the ubuntu website which was an iso which was corrupt, I tried only 2(alternate,desktop), and then I downloaded it from torrent which was suggested on the homepage but still it did not worked when I tried installing it from within windows, in the end it gave an error, "Argument ......" cant remember it correctly, sorry..... but now what, please give me a 100% certified and guaranteed link from where I can download ubuntu 9.10 and install it from either within windows or directly.... also please tell me the difference between alternate and desktop editions........... PLEASE GUYS HELP ME, ITS DAMN DAMN DAMN URGENT!!!!!!!!!!!!!!!!

---

### Post by phillw on 2009-12-26
> **furqanbhai said:**
> I have downloaded ubuntu 9.10 first from the ubuntu website which was an iso which was corrupt, I tried only 2(alternate,desktop), and then I downloaded it from torrent which was suggested on the homepage but still it did not worked when I tried installing it from within windows, in the end it gave an error, "Argument ......" cant remember it correctly, sorry..... but now what, please give me a 100% certified and guaranteed link from where I can download ubuntu 9.10 and install it from either within windows or directly.... also please tell me the difference between alternate and desktop editions........... PLEASE GUYS HELP ME, ITS DAMN DAMN DAMN URGENT!!!!!!!!!!!!!!!!

Hi & welcome ... "Please Help" does not help us to help you.
Try to use a title that is the issue - in this case - problem with downloading.

Anyways,  at what point did you realise the original iso from ubuntu was corrupt ?
1) as a file on your computer
2) as a CD

Answering that will allow us to move forward with your problem.

On your next query, you have the choice of Wubi - which installs within windows, or a 'true' ubuntu installation which lives side by side with windows.
The alternate CD is for those who need text only installs, as opposed to using a window / mouse orientated install.

Please decide whether you want dual boot or wubi.

Regards,

Phill.

---

### Post by taurus on 2009-12-26
Do you want to install Ubuntu on it own partition or do you want to install it in windows?  Those two are not the same.

Just so you know, when you burn the ISO image, burn it at a slow speed like 4x instead of the default speed.  Burning at a fast speed will guarantee to have a bad CD.

---

### Post by furqanbhai on 2009-12-26
Thanks for the urgent help and really sorry for the subject line.....



@phillw---- pal, When I burned the image on the cd and tried to install ubuntu from it, I came to know....


@taurus---- I wanted to use wubi, ubuntu within windows but right at the end of installation it says, "Argument Incorrect" or perhaps "Argument not valid"


Atleast guys tell me if u r using ubuntu 9.10, then from where u both have downloaded and also from where majority of the ubuntu users are downloading???????

---

### Post by oldsoundguy on 2009-12-26
did you run the chksum and compare before you bothered to burn?

Did you burn at the slowest speed possible on your system?

Did you burn it as an .iso and not a data disk?

Did you run the disk verification utility that comes on the disk before attempting an install?

I had an issue recently and found it was BAD MEDIA.

---

### Post by jmszr on 2009-12-26
furqanbhai,

For Wubi: [http://wubi-installer.org/](http://wubi-installer.org/) . It is not necessary to burn an .iso to install Wubi if you use this. Also, be sure to defrag Windows a couple of times first.

For Ubuntu torrent download:[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

Also read these: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) .

Hope that helps.

---

### Post by furqanbhai on 2010-01-22
Hi guys,



I think you can help me a lot better since I am attaching the error snap and also tell me what do u mean by saying that I do not need burn the .iso?
Please help.....

Following is the log file which was created after I got the error....





01-21 07:37 INFO   root: === wubi 9.10ubuntu1 rev160 ===

01-21 07:37 DEBUG  root: Logfile is c:\docume~1\furqan\locals~1\temp\wubi-9.10ubuntu1-rev160.log

01-21 07:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']

01-21 07:37 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\data

01-21 07:37 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\bin\7z.exe

01-21 07:37 DEBUG  CommonBackend: Fetching basic info...

01-21 07:37 DEBUG  CommonBackend: original_exe=F:\wubi.exe

01-21 07:37 DEBUG  CommonBackend: platform=win32

01-21 07:37 DEBUG  CommonBackend: osname=nt

01-21 07:37 DEBUG  CommonBackend: language=en_US

01-21 07:37 DEBUG  CommonBackend: encoding=cp1252

01-21 07:37 DEBUG  WindowsBackend: arch=i386

01-21 07:37 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\data\isolist.ini

01-21 07:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386

01-21 07:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64

01-21 07:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64

01-21 07:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386

01-21 07:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64

01-21 07:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386

01-21 07:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64

01-21 07:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386

01-21 07:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386

01-21 07:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386

01-21 07:37 DEBUG  WindowsBackend: Fetching host info...

01-21 07:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

01-21 07:37 DEBUG  WindowsBackend: windows version=xp

01-21 07:37 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP

01-21 07:37 DEBUG  WindowsBackend: windows_sp=Service Pack 2

01-21 07:37 DEBUG  WindowsBackend: windows_build=2600

01-21 07:37 DEBUG  WindowsBackend: gmt=5

01-21 07:37 DEBUG  WindowsBackend: country=US

01-21 07:37 DEBUG  WindowsBackend: timezone=America/New_York

01-21 07:37 DEBUG  WindowsBackend: windows_username=Furqan

01-21 07:37 DEBUG  WindowsBackend: user_full_name=Furqan

01-21 07:37 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan

01-21 07:37 DEBUG  WindowsBackend: windows_language_code=1033

01-21 07:37 DEBUG  WindowsBackend: windows_language=English

01-21 07:37 DEBUG  WindowsBackend: processor_name=None

01-21 07:37 DEBUG  WindowsBackend: bootloader=xp

01-21 07:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 18415.4179688 mb free ntfs)

01-21 07:37 DEBUG  WindowsBackend: drive=Drive(C: hd 18415.4179688 mb free ntfs)

01-21 07:37 DEBUG  WindowsBackend: drive=Drive(D: hd 20416.203125 mb free ntfs)

01-21 07:37 DEBUG  WindowsBackend: drive=Drive(E: hd 35625.71875 mb free ntfs)

01-21 07:37 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)

01-21 07:37 DEBUG  WindowsBackend: uninstaller_path=None

01-21 07:37 DEBUG  WindowsBackend: previous_target_dir=None

01-21 07:37 DEBUG  WindowsBackend: previous_distro_name=None

01-21 07:37 DEBUG  WindowsBackend: keyboard_id=67699721

01-21 07:37 DEBUG  WindowsBackend: keyboard_layout=us

01-21 07:37 DEBUG  WindowsBackend: keyboard_variant=

01-21 07:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')

01-21 07:37 DEBUG  CommonBackend: locale=en_US.UTF-8

01-21 07:37 DEBUG  WindowsBackend: total_memory_mb=254.484375

01-21 07:37 DEBUG  CommonBackend: Searching ISOs on USB devices

01-21 07:37 DEBUG  CommonBackend: Searching for local CDs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Ubuntu Netbook Remix CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Kubuntu Netbook CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Xubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp is a valid Mythbuntu CD

01-21 07:37 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD

01-21 07:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD

01-21 07:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD

01-21 07:37 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)

01-21 07:37 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}

01-21 07:37 DEBUG  Distro: wrong arch: i386 != amd64

01-21 07:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD

01-21 07:37 INFO   Distro: Found a valid CD for Ubuntu: F:\

01-21 07:37 INFO   root: Running the CD menu...

01-21 07:37 DEBUG  WindowsFrontend: __init__...

01-21 07:37 DEBUG  WindowsFrontend: on_init...

01-21 07:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en']

01-21 07:37 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en']

01-21 07:38 INFO   root: CD menu finished

01-21 07:38 INFO   root: Running the installer...

01-21 07:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en']

01-21 07:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl19.tmp\translations, languages=['en_US', 'en']

01-21 07:38 DEBUG  root: application.quit

01-21 07:38 DEBUG  WindowsFrontend: frontend.quit

01-21 07:38 DEBUG  WindowsFrontend: frontend.on_quit

01-21 07:38 DEBUG  root: application.on_quit

01-21 07:38 INFO   root: sys.exit

01-21 07:38 INFO   root: === wubi 9.10ubuntu1 rev160 ===

01-21 07:38 DEBUG  root: Logfile is c:\docume~1\furqan\locals~1\temp\wubi-9.10ubuntu1-rev160.log

01-21 07:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']

01-21 07:38 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\data

01-21 07:38 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\bin\7z.exe

01-21 07:38 DEBUG  CommonBackend: Fetching basic info...

01-21 07:38 DEBUG  CommonBackend: original_exe=F:\wubi.exe

01-21 07:38 DEBUG  CommonBackend: platform=win32

01-21 07:38 DEBUG  CommonBackend: osname=nt

01-21 07:38 DEBUG  CommonBackend: language=en_US

01-21 07:38 DEBUG  CommonBackend: encoding=cp1252

01-21 07:38 DEBUG  WindowsBackend: arch=i386

01-21 07:38 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\data\isolist.ini

01-21 07:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386

01-21 07:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64

01-21 07:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64

01-21 07:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386

01-21 07:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64

01-21 07:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386

01-21 07:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64

01-21 07:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386

01-21 07:38 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386

01-21 07:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386

01-21 07:38 DEBUG  WindowsBackend: Fetching host info...

01-21 07:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

01-21 07:38 DEBUG  WindowsBackend: windows version=xp

01-21 07:38 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP

01-21 07:38 DEBUG  WindowsBackend: windows_sp=Service Pack 2

01-21 07:38 DEBUG  WindowsBackend: windows_build=2600

01-21 07:38 DEBUG  WindowsBackend: gmt=5

01-21 07:38 DEBUG  WindowsBackend: country=US

01-21 07:38 DEBUG  WindowsBackend: timezone=America/New_York

01-21 07:38 DEBUG  WindowsBackend: windows_username=Furqan

01-21 07:38 DEBUG  WindowsBackend: user_full_name=Furqan

01-21 07:38 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Furqan

01-21 07:38 DEBUG  WindowsBackend: windows_language_code=1033

01-21 07:38 DEBUG  WindowsBackend: windows_language=English

01-21 07:38 DEBUG  WindowsBackend: processor_name=None

01-21 07:38 DEBUG  WindowsBackend: bootloader=xp

01-21 07:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 18415.3671875 mb free ntfs)

01-21 07:38 DEBUG  WindowsBackend: drive=Drive(C: hd 18415.3671875 mb free ntfs)

01-21 07:38 DEBUG  WindowsBackend: drive=Drive(D: hd 20416.203125 mb free ntfs)

01-21 07:38 DEBUG  WindowsBackend: drive=Drive(E: hd 35625.71875 mb free ntfs)

01-21 07:38 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)

01-21 07:38 DEBUG  WindowsBackend: uninstaller_path=None

01-21 07:38 DEBUG  WindowsBackend: previous_target_dir=None

01-21 07:38 DEBUG  WindowsBackend: previous_distro_name=None

01-21 07:38 DEBUG  WindowsBackend: keyboard_id=67699721

01-21 07:38 DEBUG  WindowsBackend: keyboard_layout=us

01-21 07:38 DEBUG  WindowsBackend: keyboard_variant=

01-21 07:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')

01-21 07:38 DEBUG  CommonBackend: locale=en_US.UTF-8

01-21 07:38 DEBUG  WindowsBackend: total_memory_mb=254.484375

01-21 07:38 DEBUG  CommonBackend: Searching ISOs on USB devices

01-21 07:38 DEBUG  CommonBackend: Searching for local CDs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu Netbook Remix CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu Netbook CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD

01-21 07:38 DEBUG  Distro:     does not contain C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD

01-21 07:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD

01-21 07:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs

01-21 07:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD

01-21 07:38 DEBUG  Distro:   parsing info from str=Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)

01-21 07:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}

01-21 07:38 DEBUG  Distro: wrong arch: i386 != amd64

01-21 07:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD

01-21 07:38 INFO   Distro: Found a valid CD for Ubuntu: F:\

01-21 07:38 INFO   root: Running the CD menu...

01-21 07:38 DEBUG  WindowsFrontend: __init__...

01-21 07:38 DEBUG  WindowsFrontend: on_init...

01-21 07:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']

01-21 07:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']

01-21 07:38 INFO   root: CD menu finished

01-21 07:38 INFO   root: Running the installer...

01-21 07:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']

01-21 07:38 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']

01-21 07:40 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=mohammed

01-21 07:40 INFO   root: Received settings

01-21 07:40 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']

01-21 07:40 DEBUG  TaskList: # Running tasklist...

01-21 07:40 DEBUG  TaskList: ## Running select_target_dir...

01-21 07:40 INFO   WindowsBackend: Installing into D:\ubuntu

01-21 07:40 DEBUG  TaskList: ## Finished select_target_dir

01-21 07:40 DEBUG  TaskList: ## Running create_dir_structure...

01-21 07:40 DEBUG  CommonBackend: Creating dir D:\ubuntu

01-21 07:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks

01-21 07:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\install

01-21 07:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot

01-21 07:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot

01-21 07:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub

01-21 07:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub

01-21 07:40 DEBUG  TaskList: ## Finished create_dir_structure

01-21 07:40 DEBUG  TaskList: ## Running uncompress_target_dir...

01-21 07:40 DEBUG  TaskList: ## Finished uncompress_target_dir

01-21 07:40 DEBUG  TaskList: ## Running create_uninstaller...

01-21 07:40 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe

01-21 07:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe

01-21 07:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu

01-21 07:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu

01-21 07:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico

01-21 07:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.10ubuntu1-rev160

01-21 07:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu

01-21 07:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)

01-21 07:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)

01-21 07:40 DEBUG  TaskList: ## Finished create_uninstaller

01-21 07:40 DEBUG  TaskList: ## Running copy_installation_files...

01-21 07:40 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation

01-21 07:40 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\winboot -> D:\ubuntu\winboot

01-21 07:40 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Furqan\LOCALS~1\Temp\pyl1A.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico

01-21 07:40 DEBUG  TaskList: ## Finished copy_installation_files

01-21 07:40 DEBUG  TaskList: ## Running get_iso...

01-21 07:40 DEBUG  TaskList: New task copy_file

01-21 07:40 DEBUG  TaskList: ### Running copy_file...

01-21 07:46 DEBUG  TaskList: ### Finished copy_file

01-21 07:46 ERROR  TaskList: [Errno 22] Invalid argument

Traceback (most recent call last):

  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__

  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file

IOError: [Errno 22] Invalid argument

01-21 07:46 DEBUG  TaskList: # Cancelling tasklist

01-21 07:46 ERROR  root: [Errno 22] Invalid argument

Traceback (most recent call last):

  File "\lib\wubi\application.py", line 56, in run

  File "\lib\wubi\application.py", line 126, in select_task

  File "\lib\wubi\application.py", line 194, in run_cd_menu

  File "\lib\wubi\application.py", line 118, in select_task

  File "\lib\wubi\application.py", line 156, in run_installer

  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__

  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file

IOError: [Errno 22] Invalid argument

01-21 07:46 DEBUG  TaskList: New task check_iso

01-21 07:46 DEBUG  CommonBackend: Searching for local ISO

01-21 07:46 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now

01-21 07:46 DEBUG  TaskList: New task get_metalink

01-21 07:46 ERROR  TaskList: Cannot download the metalink and therefore the ISO

Traceback (most recent call last):

  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__

  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso

  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso

Exception: Cannot download the metalink and therefore the ISO

01-21 07:46 DEBUG  TaskList: # Cancelling tasklist

01-21 07:46 DEBUG  TaskList: # Finished tasklist

---

### Post by earthpigg on 2010-01-22
> 
01-21 07:38 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.10', 'build': '20091028.5', 'codename': 'Karmic Koala', 'arch': 'i386'}

01-21 07:38 DEBUG Distro: wrong arch: i386 != amd64


that catches my eye.

does anyone know if 32 bit wubi/ubuntu run on ***64 bit windows***?

original poster: do you have 32 or 64 bit windows?

---

### Post by stinger30au on 2010-01-22
i have on my laptop a 64 bit version of windows 7

if i instal any 32 bit s/w on it it creates a special 32 bit program directory for it to save to...

so *in theory* the 32 bit version of ubuntu *should* install ok

having said that i have also run a 32 bit copy of ubuntu on my laptop and it ran fine before i ditched it and ran the 64 bit version. i just wanted to see if there was any difference. to be honest, i could not see any

---

### Post by furqanbhai on 2010-01-22
Thanks guys for all your replies.......... But still I want someone to help me out and fix it completely this time around.....

---

### Post by kansasnoob on 2010-01-22
Instead of burning a .iso just go here:

[http://wubi-installer.org/](http://wubi-installer.org/)

Click on download now.

But from this:

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

> 
Can I use an existing ISO/CD instead of letting Wubi download a new one?

Yes, **physical CDs will be detected automatically**, pre-downloaded ISOs should be placed in the same folder as Wubi.exe. Please note tha Wubi 8.10 requires the Desktop 8.10 CD/ISO. The DVD and Altrenate CD/ISO will not work. You can find the 8.10 ISO here. **If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is corrupted, it will automatically download a new ISO.** **[COLOR="Red"]It is recommended to let Wubi download the ISO for you.[/COLOR]**


So I'd recommend getting rid of all the old Ubuntu iso images on the box. Why you've been getting bad downloads I don't know :confused:

Since you'll be getting 9.10 you should also know this:

> Important Note to Wubi (Windows Ubuntu) Users:
Recent January 2010 updates are triggering a bug in the ntfs module, causing Wubi boot failures. The solution to this boot problem was posted by Agostino Russo and is found in this Lucid Lynx LaunchPad Bug Report #477169, Post 210. The module causing the errors has been fixed and replacing the "wubildr" file in Windows permanently solves this problem. See the bug report for details.

From:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

The bug link referred to:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

---

### Post by oldsoundguy on 2010-01-22
Your thumbnail indicates you are attempting to install Ubuntu INTO Windows using the iso disk.

That can't be done!  

Ubuntu is NOT a program, it is a complete operating system, meaning it CONTROLS your computer.

You can use this:
[http://wubi-installer.org/](http://wubi-installer.org/)
to install WITHIN WINDOWS, but it really is NOT the best way. (Do a Google search on the program to find out the pros and cons  .)

Much better to create a separate partition and to install it as a dual boot.

---

### Post by kansasnoob on 2010-01-22
> Much better to create a separate partition and to install it as a dual boot.

+1! With a but ........... but the OP is having trouble just installing Wubi, can you imagine the anxiety installing a true dual boot?

What comes after "for godsake" :P

I already know: holy crap I wiped my drive and I didn't want to!

---

