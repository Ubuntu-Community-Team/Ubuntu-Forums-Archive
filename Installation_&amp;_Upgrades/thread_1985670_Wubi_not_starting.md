---
title: "Wubi not starting"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by vazduxosbra4kania on 2012-05-23
Please check video i made for the stupidity that i have as a problem. I really hope that its just some stupid mistake i am making.....After 15 restarts each time its the same i turned off anti virus and all kind of firewalls i still dont know wtf is wrong with this computer. I tried 64 or 32 bit systems i tried i386 and NOTHING....is it possible that my windows 7(64bit) is the reason cause before i had win7(32bit) and had no problem....May be the old ubuntu hasn't been uninstalled successfully???

            ---> [http://youtu.be/ONQu0aTV88E](http://youtu.be/ONQu0aTV88E) <---

---

### Post by jadtech on 2012-05-23
ok I know ubuntu wubi hasn't been install , I have several thooughts here first  is there any ubuntu folders on C drive that you can see  ??? go to remove programs is there anything  related to ubuntu  that you can choose to uninstall .. 

next run disk clean up, clear your browser cache , delete the down loaded wubi installer from  your down loaded programs .. 

make sure you have a good internet connection  and try the online wubi installer again , if it fails  DOwn load the ISO burn it to DVD  once its burnt and finished open the cd/dvd player and close it back up  a notice to install ubuntu inside windows should pop up you can do the wubi install right from the live cd without having to boot from CD it auto runs and installs wubi  from windows.. .. 

it kis possible  the online wubi install is not working for a few reason one of them being that the server it is trying to down load from is to busy or is down :)

keep in mind  doing wubi install from disk you can have version 12.04 doing the online installer you can only have 11.04 or 11.10 they are no longer  supporting the online wubi online installer beyond version 11 ...

---

### Post by bcbc on 2012-05-23
Check the %TEMP% directory. Look for wubi-12.04-rev266.log. Post the contents back here.

If there is nothing there, check whether you have python installed on your computer.

---

### Post by vazduxosbra4kania on 2012-05-23
> **jadtech said:**
> ok I know ubuntu wubi hasn't been install , I have several thooughts here first  is there any ubuntu folders on C drive that you can see  ??? go to remove programs is there anything  related to ubuntu  that you can choose to uninstall .. 

next run disk clean up, clear your browser cache , delete the down loaded wubi installer from  your down loaded programs .. 

make sure you have a good internet connection  and try the online wubi installer again , if it fails  DOwn load the ISO burn it to DVD  once its burnt and finished open the cd/dvd player and close it back up  a notice to install ubuntu inside windows should pop up you can do the wubi install right from the live cd without having to boot from CD it auto runs and installs wubi  from windows.. .. 

it kis possible  the online wubi install is not working for a few reason one of them being that the server it is trying to down load from is to busy or is down :)

keep in mind  doing wubi install from disk you can have version 12.04 doing the online installer you can only have 11.04 or 11.10 they are no longer  supporting the online wubi online installer beyond version 11 ...

Thank you for the suggestions but none of them worked. I tried everything step by step...

---

### Post by vazduxosbra4kania on 2012-05-23
> **bcbc said:**
> Check the %TEMP% directory. Look for wubi-12.04-rev266.log. Post the contents back here.

If there is nothing there, check whether you have python installed on your computer.

I do not have python. And the content of my log file is GIANT. I cant post all of it (i think). Is there something special to extract from there, or to look for?:)

---

### Post by bcbc on 2012-05-23
> **vazduxosbra4kania said:**
> I do not have python. And the content of my log file is GIANT. I cant post all of it (i think). Is there something special to extract from there, or to look for?:)

Here's what to do: delete or rename the log file.
Run it again. That will create a new, smaller log file. Post that.

Or pastebin it. Or you can read it and look for the error. It's hard for me to speculate what it might be.

---

### Post by vazduxosbra4kania on 2012-05-23
> **bcbc said:**
> Here's what to do: delete or rename the log file.
Run it again. That will create a new, smaller log file. Post that.

Or pastebin it. Or you can read it and look for the error. It's hard for me to speculate what it might be.


OK so apperantly this log file is divided in install sequences. i see the following message repeating in every sequence i guess this is the error we are looking for( the underlined part at the bottom)
05-23 16:04 INFO   root: === wubi 12.04 rev266 ===
05-23 16:04 DEBUG  root: Logfile is c:\users\turlakov\appdata\local\temp\wubi-12.04-rev266.log
05-23 16:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Turlakov\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\BQHEF2EF\\wubi.exe"']
05-23 16:04 DEBUG  CommonBackend: data_dir=C:\Users\Turlakov\AppData\Local\Temp\pylFBD3.tmp\data
05-23 16:04 DEBUG  WindowsBackend: 7z=C:\Users\Turlakov\AppData\Local\Temp\pylFBD3.tmp\bin\7z.exe
05-23 16:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 16:04 DEBUG  CommonBackend: Fetching basic info...
05-23 16:04 DEBUG  CommonBackend: original_exe=C:\Users\Turlakov\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\BQHEF2EF\wubi.exe
05-23 16:04 DEBUG  CommonBackend: platform=win32
05-23 16:04 DEBUG  CommonBackend: osname=nt
05-23 16:04 DEBUG  CommonBackend: language=en_US
05-23 16:04 DEBUG  CommonBackend: encoding=cp1252
05-23 16:04 DEBUG  WindowsBackend: arch=amd64
05-23 16:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\Turlakov\AppData\Local\Temp\pylFBD3.tmp\data\isolist.ini
05-23 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-23 16:04 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-23 16:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-23 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 16:04 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-23 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 16:04 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-23 16:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 16:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 16:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 16:04 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-23 16:04 DEBUG  WindowsBackend: Fetching host info...
05-23 16:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 16:04 DEBUG  WindowsBackend: windows version=vista
05-23 16:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-23 16:04 DEBUG  WindowsBackend: windows_sp=None
05-23 16:04 DEBUG  WindowsBackend: windows_build=7600
05-23 16:04 DEBUG  WindowsBackend: gmt=2
05-23 16:04 DEBUG  WindowsBackend: country=US
05-23 16:04 DEBUG  WindowsBackend: timezone=America/New_York
05-23 16:04 DEBUG  WindowsBackend: windows_username=Turlakov
05-23 16:04 DEBUG  WindowsBackend: user_full_name=Turlakov
05-23 16:04 DEBUG  WindowsBackend: user_directory=C:\Users\Turlakov
05-23 16:04 DEBUG  WindowsBackend: windows_language_code=1033
05-23 16:04 DEBUG  WindowsBackend: windows_language=English
05-23 16:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU         530  @ 2.93GHz
05-23 16:04 DEBUG  WindowsBackend: bootloader=vista
05-23 16:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87661.5742188 mb free ntfs)
05-23 16:04 DEBUG  WindowsBackend: drive=Drive(C: hd 87661.5742188 mb free ntfs)
05-23 16:04 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-23 16:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free udf)
05-23 16:04 DEBUG  WindowsBackend: drive=Drive(G: hd 40819.1210938 mb free ntfs)
05-23 16:04 DEBUG  WindowsBackend: uninstaller_path=None
05-23 16:04 DEBUG  WindowsBackend: previous_target_dir=None
05-23 16:04 DEBUG  WindowsBackend: previous_distro_name=None
05-23 16:04 DEBUG  WindowsBackend: keyboard_id=67699721
05-23 16:04 DEBUG  WindowsBackend: keyboard_layout=us
05-23 16:04 DEBUG  WindowsBackend: keyboard_variant=
05-23 16:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-23 16:04 DEBUG  CommonBackend: locale=en_US.UTF-8
05-23 16:04 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-23 16:04 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 16:04 DEBUG  Distro:   checking Ubuntu ISO G:\Diablo 3.iso
_05-23 16:04 ERROR  root: list index out of range_
[U]Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\backends\common\backend.py", line 190, in fetch_basic_info
  File "\lib\wubi\backends\common\backend.py", line 803, in find_any_iso
  File "\lib\wubi\backends\common\distro.py", line 112, in is_valid_iso
  File "\lib\wubi\backends\win32\backend.py", line 542, in get_iso_file_names
IndexError: list index out of range[/U]

---

### Post by jadtech on 2012-05-23
hmmm 

you wouldn't happen to have a diablo 3 cd in your cd/dvd drive would you ??? 

> 
05-23 16:04 DEBUG Distro: checking Ubuntu ISO G:\Diablo 3.iso
05-23 16:04 ERROR root: list index out of range
Traceback (most recent call last):
 

that appears to possiblly be the trouble  it is looking for an .ISO and the diablo 3 its finding  is not right .
I could be wrong I have been before  every thing went good till that point .. 

if that cd in in the drive remove it   and start over with the wubi install

---

### Post by jadtech on 2012-05-23
I can't count the number of time I have said to these kids when you are done playing  pick things up some day some one is goingto get hurt or something is going to get broke and you will spend hours regreting and swearing over it  .. 

hope that works for you

---

### Post by bcbc on 2012-05-23
Yes, it seems you have found a bug. If you can move the ISO out of the root of the G: drive (move it into a subfolder) and try again.

Please file a bug report too: [https://bugs.launchpad.net/wubi/+filebug](https://bugs.launchpad.net/wubi/+filebug) and attach that log file to it. (You'll need a launchpad account for this)
Thanks

---

### Post by vazduxosbra4kania on 2012-05-24
Ok thank both of you. I submitted a bug report. The reason was actually the diablo 3. Removed it and installer started. Right now i have some other issues and cant install ubuntu. I shall try resolve by myself. If i didnt make it i will right here again. Thank you one more time for the support....:P

---

### Post by vazduxosbra4kania on 2012-05-24
> **bcbc said:**
> Yes, it seems you have found a bug. If you can move the ISO out of the root of the G: drive (move it into a subfolder) and try again.

Please file a bug report too: [https://bugs.launchpad.net/wubi/+filebug](https://bugs.launchpad.net/wubi/+filebug) and attach that log file to it. (You'll need a launchpad account for this)
Thanks

Ubuntu up and running :)))) FINALLY!

---

### Post by bcbc on 2012-05-24
> **vazduxosbra4kania said:**
> Ubuntu up and running :)))) FINALLY!

Great! Good job.

Review the [Wubi Guide]("https://wiki.ubuntu.com/WubiGuide") if you have questions about Wubi or ask. Pay attention to the warning about hard shutdowns right near the top of that page.

---

