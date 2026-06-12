---
title: "Wubi: Trying to repair a dual boot installation..."
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Tigerbeat on 2011-03-21
[B][COLOR=Blue]I had a dual boot installation on Windows 7 (on different partitions). Unfortunately Windows 7 crashed but the Ubuntu partition was not affected by this.


Now I am starting over and I have installed Windows 7 and moved the old Ubuntu partition to a new partition... [/COLOR]
[/B]   


Now, **is there a way that I can hook up the old Ubuntu installation to Windows 7 and dual boot again?** Like repairing the installation on that partition?


[B][COLOR=Blue]
I thought if inserting the Ubuntu installation CD and install on the Ubuntu partition I'd get an option to do a new installation or repair the existing one.[/COLOR][/B]



Instead I get the following error message:
 
[B][COLOR=DarkRed]Exception: Cannot install into W:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing. [/COLOR][/B]
 

Thanks in advance.

---

### Post by Frogs Hair on 2011-03-21
Hi and Welcome 

If you were using a Wubi installation Ubuntu would have been installed inside of the  Windows partition and removed when Windows was removed . Is this a traditional dual boot or a Wubi installation ? Did you move The wubi installation to it's own partition before removing Windows ?

---

### Post by Tigerbeat on 2011-03-21
> **Frogs Hair said:**
> Hi and Welcome 

If you were using a Wubi installation Ubuntu would have been installed inside of the  Windows partition and removed when Windows was removed . Is this a traditional dual boot or a Wubi installation ? Did you move The wubi installation to it's own partition before removing Windows ?

Hi,


** Is this a traditional dual boot or a Wubi installation ? **
Wubi installation... 

**Did you move The wubi installation to it's own partition before removing Windows ?**
I am not sure if I understand this question. But here is what happened: My windows partition crashed and I lost everything it.

I hope this answers your question.


Thanks.

T

---

### Post by bcbc on 2011-03-21
You can recover the old Wubi. The virtual disk Wubi uses is the root.disk file (\ubuntu\disks\root.disk). Look inside that disks directory and make sure it's the only one - ignore swap.disk - and let me know if there are any more)

So, it's not straightforward to do this, because the boot file wubi uses is within the virtual disk, and it remembers the partition and UUID of where it was originally installed. And it sounds like these have likely changed.

What I would do is this:
rename W:\ubuntu to W:\ubuntuSAVE

Reinstall Wubi (same release as before, and make the virtual disk 3GB because you're going to throw it away later): 
1. install in windows, 
2. reboot and select Ubuntu to complete the actual install, 
3. after the ubuntu install it reboots, select Ubuntu again, but this time, when you see the grub menu, hit 'e'

Look for the lines:
*set root=(hdX,Y)*
and 
*linux /boot/xxxxx root=/dev/sdMY xxxx*

Note the values M, X, Y (e.g. (hd0,3) = /dev/sda3

Then boot windows, copy over the original root.disk from \ubuntuSAVE\disks over the one in \ubuntu\disks directory.

When you next boot Ubuntu, hit 'e' on the first entry, change it so it matches the values you found before: (hdX,Y) /dev/sdMY 
Also, delete the line "search --no-floppy xxxxx"
Then hit CTRL+x to boot
Then once booted, drop to a terminal (CTRL+ALT+t) and run "sudo update-grub".

That's pretty convoluted but necessary. If you're familiar with the partition notation you can just bypass the whole install step and go directly to the copy over and edit step.

If you prefer, you can also migrate the current Wubi do a normal dual boot, which is better if you'll be using it long-term.

---

### Post by Tigerbeat on 2011-03-22
> **bcbc said:**
> You can recover the old Wubi. The virtual disk Wubi uses is the root.disk file (\ubuntu\disks\root.disk). Look inside that disks directory and make sure it's the only one - ignore swap.disk - and let me know if there are any more)

So, it's not straightforward to do this, because the boot file wubi uses is within the virtual disk, and it remembers the partition and UUID of where it was originally installed. And it sounds like these have likely changed.

What I would do is this:
rename W:\ubuntu to W:\ubuntuSAVE

Reinstall Wubi (same release as before, and make the virtual disk 3GB because you're going to throw it away later): 
1. install in windows, 
2. reboot and select Ubuntu to complete the actual install, 
3. after the ubuntu install it reboots, select Ubuntu again, but this time, when you see the grub menu, hit 'e'

Look for the lines:
*set root=(hdX,Y)*
and 
*linux /boot/xxxxx root=/dev/sdMY xxxx*

Note the values M, X, Y (e.g. (hd0,3) = /dev/sda3

Then boot windows, copy over the original root.disk from \ubuntuSAVE\disks over the one in \ubuntu\disks directory.

When you next boot Ubuntu, hit 'e' on the first entry, change it so it matches the values you found before: (hdX,Y) /dev/sdMY 
Also, delete the line "search --no-floppy xxxxx"
Then hit CTRL+x to boot
Then once booted, drop to a terminal (CTRL+ALT+t) and run "sudo update-grub".

That's pretty convoluted but necessary. If you're familiar with the partition notation you can just bypass the whole install step and go directly to the copy over and edit step.

If you prefer, you can also migrate the current Wubi do a normal dual boot, which is better if you'll be using it long-term.



I am on it in a flash...


I'll let you know how it goes.


Thanks.

T

---

### Post by ashton93 on 2011-07-03
> **bcbc said:**
> You can recover the old Wubi. The virtual disk Wubi uses is the root.disk file (\ubuntu\disks\root.disk). Look inside that disks directory and make sure it's the only one - ignore swap.disk - and let me know if there are any more)
 
So, it's not straightforward to do this, because the boot file wubi uses is within the virtual disk, and it remembers the partition and UUID of where it was originally installed. And it sounds like these have likely changed.
 
What I would do is this:
rename W:\ubuntu to W:\ubuntuSAVE
 
Reinstall Wubi (same release as before, and make the virtual disk 3GB because you're going to throw it away later): 
1. install in windows, 
2. reboot and select Ubuntu to complete the actual install, 
3. after the ubuntu install it reboots, select Ubuntu again, but this time, when you see the grub menu, hit 'e'
 
Look for the lines:
*set root=(hdX,Y)*
and 
*linux /boot/xxxxx root=/dev/sdMY xxxx*
 
Note the values M, X, Y (e.g. (hd0,3) = /dev/sda3
 
Then boot windows, copy over the original root.disk from \ubuntuSAVE\disks over the one in \ubuntu\disks directory.
 
When you next boot Ubuntu, hit 'e' on the first entry, change it so it matches the values you found before: (hdX,Y) /dev/sdMY 
Also, delete the line "search --no-floppy xxxxx"
Then hit CTRL+x to boot
Then once booted, drop to a terminal (CTRL+ALT+t) and run "sudo update-grub".
 
That's pretty convoluted but necessary. If you're familiar with the partition notation you can just bypass the whole install step and go directly to the copy over and edit step.
 
If you prefer, you can also migrate the current Wubi do a normal dual boot, which is better if you'll be using it long-term.
 
 
 
 
Okay so i did the whole C:\ubuntuSAVE thing and to admit it was working until the error msg popped up saying permission denined. So what do i do??? :confused:

---

### Post by bcbc on 2011-07-03
> **ashton93 said:**
> Okay so i did the whole C:\ubuntuSAVE thing and to admit it was working until the error msg popped up saying permission denined. So what do i do??? :confused:

That's usually a problem on the Windows part of the install so you need to check the log file to see what is wrong. (It's in the %temp% directory). 

Also, it's generally a bad idea to use instructions that are specific to another user and their scenario - unless yours matches exactly (and sometimes it's hard to tell). It's better to create your own thread.

---

### Post by ashton93 on 2011-07-03
> **bcbc said:**
> That's usually a problem on the Windows part of the install so you need to check the log file to see what is wrong. (It's in the %temp% directory). 
 
Also, it's generally a bad idea to use instructions that are specific to another user and their scenario - unless yours matches exactly (and sometimes it's hard to tell). It's better to create your own thread.
 
This long list shows up
```

07-03 04:18 INFO   root: === wubi 11.04 rev211 ===
07-03 04:18 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 04:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 04:18 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\data
07-03 04:18 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\bin\7z.exe
07-03 04:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 04:18 DEBUG  CommonBackend: Fetching basic info...
07-03 04:18 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 04:18 DEBUG  CommonBackend: platform=win32
07-03 04:18 DEBUG  CommonBackend: osname=nt
07-03 04:18 DEBUG  CommonBackend: language=en_US
07-03 04:18 DEBUG  CommonBackend: encoding=cp1252
07-03 04:18 DEBUG  WindowsBackend: arch=amd64
07-03 04:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\data\isolist.ini
07-03 04:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 04:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 04:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 04:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 04:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 04:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 04:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 04:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 04:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 04:18 DEBUG  WindowsBackend: Fetching host info...
07-03 04:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 04:18 DEBUG  WindowsBackend: windows version=vista
07-03 04:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 04:18 DEBUG  WindowsBackend: windows_sp=None
07-03 04:18 DEBUG  WindowsBackend: windows_build=7600
07-03 04:18 DEBUG  WindowsBackend: gmt=-6
07-03 04:18 DEBUG  WindowsBackend: country=US
07-03 04:18 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 04:18 DEBUG  WindowsBackend: windows_username=Ashton
07-03 04:18 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 04:18 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 04:18 DEBUG  WindowsBackend: windows_language_code=1033
07-03 04:18 DEBUG  WindowsBackend: windows_language=English
07-03 04:18 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 04:18 DEBUG  WindowsBackend: bootloader=vista
07-03 04:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 228268.210938 mb free ntfs)
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(C: hd 228268.210938 mb free ntfs)
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 04:18 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 04:18 DEBUG  WindowsBackend: uninstaller_path=None
07-03 04:18 DEBUG  WindowsBackend: previous_target_dir=None
07-03 04:18 DEBUG  WindowsBackend: previous_distro_name=None
07-03 04:18 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 04:18 DEBUG  WindowsBackend: keyboard_layout=us
07-03 04:18 DEBUG  WindowsBackend: keyboard_variant=
07-03 04:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 04:18 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 04:18 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 04:18 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 04:18 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:18 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:18 DEBUG  CommonBackend: Searching for local CDs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Ubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Ubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Ubuntu Netbook CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Kubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Kubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Xubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Xubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Mythbuntu CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp is a valid Mythbuntu CD
07-03 04:18 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 04:18 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 04:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 04:18 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 04:18 INFO   root: Running the CD menu...
07-03 04:18 DEBUG  WindowsFrontend: __init__...
07-03 04:18 DEBUG  WindowsFrontend: on_init...
07-03 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\translations, languages=['en_US', 'en']
07-03 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\translations, languages=['en_US', 'en']
07-03 04:18 INFO   root: CD menu finished
07-03 04:18 INFO   root: Running the installer...
07-03 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\translations, languages=['en_US', 'en']
07-03 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\translations, languages=['en_US', 'en']
07-03 04:18 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 04:18 INFO   root: Received settings
07-03 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl47AB.tmp\translations, languages=['en_US', 'en']
07-03 04:18 DEBUG  TaskList: # Running tasklist...
07-03 04:18 DEBUG  TaskList: ## Running select_target_dir...
07-03 04:18 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:18 DEBUG  TaskList: # Cancelling tasklist
07-03 04:18 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:18 DEBUG  TaskList: # Finished tasklist
07-03 04:19 INFO   root: === wubi 11.04 rev211 ===
07-03 04:19 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 04:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 04:19 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\data
07-03 04:19 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\bin\7z.exe
07-03 04:19 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 04:19 DEBUG  CommonBackend: Fetching basic info...
07-03 04:19 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 04:19 DEBUG  CommonBackend: platform=win32
07-03 04:19 DEBUG  CommonBackend: osname=nt
07-03 04:19 DEBUG  CommonBackend: language=en_US
07-03 04:19 DEBUG  CommonBackend: encoding=cp1252
07-03 04:19 DEBUG  WindowsBackend: arch=amd64
07-03 04:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\data\isolist.ini
07-03 04:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 04:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 04:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 04:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 04:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 04:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 04:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 04:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 04:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 04:19 DEBUG  WindowsBackend: Fetching host info...
07-03 04:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 04:19 DEBUG  WindowsBackend: windows version=vista
07-03 04:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 04:19 DEBUG  WindowsBackend: windows_sp=None
07-03 04:19 DEBUG  WindowsBackend: windows_build=7600
07-03 04:19 DEBUG  WindowsBackend: gmt=-6
07-03 04:19 DEBUG  WindowsBackend: country=US
07-03 04:19 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 04:19 DEBUG  WindowsBackend: windows_username=Ashton
07-03 04:19 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 04:19 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 04:19 DEBUG  WindowsBackend: windows_language_code=1033
07-03 04:19 DEBUG  WindowsBackend: windows_language=English
07-03 04:19 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 04:19 DEBUG  WindowsBackend: bootloader=vista
07-03 04:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 228266.671875 mb free ntfs)
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(C: hd 228266.671875 mb free ntfs)
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 04:19 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 04:19 DEBUG  WindowsBackend: uninstaller_path=None
07-03 04:19 DEBUG  WindowsBackend: previous_target_dir=None
07-03 04:19 DEBUG  WindowsBackend: previous_distro_name=None
07-03 04:19 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 04:19 DEBUG  WindowsBackend: keyboard_layout=us
07-03 04:19 DEBUG  WindowsBackend: keyboard_variant=
07-03 04:19 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 04:19 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 04:19 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 04:19 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 04:19 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:19 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:19 DEBUG  CommonBackend: Searching for local CDs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Ubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Ubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Ubuntu Netbook CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Kubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Kubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Xubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Xubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Mythbuntu CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp is a valid Mythbuntu CD
07-03 04:19 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 04:19 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 04:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 04:19 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 04:19 INFO   root: Running the CD menu...
07-03 04:19 DEBUG  WindowsFrontend: __init__...
07-03 04:19 DEBUG  WindowsFrontend: on_init...
07-03 04:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\translations, languages=['en_US', 'en']
07-03 04:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\translations, languages=['en_US', 'en']
07-03 04:19 INFO   root: CD menu finished
07-03 04:19 INFO   root: Running the installer...
07-03 04:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\translations, languages=['en_US', 'en']
07-03 04:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\translations, languages=['en_US', 'en']
07-03 04:19 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 04:19 INFO   root: Received settings
07-03 04:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl5C73.tmp\translations, languages=['en_US', 'en']
07-03 04:19 DEBUG  TaskList: # Running tasklist...
07-03 04:19 DEBUG  TaskList: ## Running select_target_dir...
07-03 04:19 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:19 DEBUG  TaskList: # Cancelling tasklist
07-03 04:19 DEBUG  TaskList: # Finished tasklist
07-03 04:19 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:21 INFO   root: === wubi 11.04 rev211 ===
07-03 04:21 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 04:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 04:21 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\data
07-03 04:21 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\bin\7z.exe
07-03 04:21 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 04:21 DEBUG  CommonBackend: Fetching basic info...
07-03 04:21 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 04:21 DEBUG  CommonBackend: platform=win32
07-03 04:21 DEBUG  CommonBackend: osname=nt
07-03 04:21 DEBUG  CommonBackend: language=en_US
07-03 04:21 DEBUG  CommonBackend: encoding=cp1252
07-03 04:21 DEBUG  WindowsBackend: arch=amd64
07-03 04:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\data\isolist.ini
07-03 04:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 04:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 04:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 04:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 04:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 04:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 04:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 04:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 04:21 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 04:21 DEBUG  WindowsBackend: Fetching host info...
07-03 04:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 04:21 DEBUG  WindowsBackend: windows version=vista
07-03 04:21 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 04:21 DEBUG  WindowsBackend: windows_sp=None
07-03 04:21 DEBUG  WindowsBackend: windows_build=7600
07-03 04:21 DEBUG  WindowsBackend: gmt=-6
07-03 04:21 DEBUG  WindowsBackend: country=US
07-03 04:21 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 04:21 DEBUG  WindowsBackend: windows_username=Ashton
07-03 04:21 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 04:21 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 04:21 DEBUG  WindowsBackend: windows_language_code=1033
07-03 04:21 DEBUG  WindowsBackend: windows_language=English
07-03 04:21 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 04:21 DEBUG  WindowsBackend: bootloader=vista
07-03 04:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 228234.386719 mb free ntfs)
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(C: hd 228234.386719 mb free ntfs)
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 04:21 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 04:21 DEBUG  WindowsBackend: uninstaller_path=None
07-03 04:21 DEBUG  WindowsBackend: previous_target_dir=None
07-03 04:21 DEBUG  WindowsBackend: previous_distro_name=None
07-03 04:21 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 04:21 DEBUG  WindowsBackend: keyboard_layout=us
07-03 04:21 DEBUG  WindowsBackend: keyboard_variant=
07-03 04:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 04:21 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 04:21 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 04:21 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 04:21 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:21 DEBUG  CommonBackend: Searching for local CDs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Ubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Ubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Ubuntu Netbook CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Kubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Kubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Xubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Xubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Mythbuntu CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp is a valid Mythbuntu CD
07-03 04:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 04:21 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 04:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 04:21 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 04:21 INFO   root: Running the CD menu...
07-03 04:21 DEBUG  WindowsFrontend: __init__...
07-03 04:21 DEBUG  WindowsFrontend: on_init...
07-03 04:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\translations, languages=['en_US', 'en']
07-03 04:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\translations, languages=['en_US', 'en']
07-03 04:21 INFO   root: CD menu finished
07-03 04:21 INFO   root: Running the installer...
07-03 04:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\translations, languages=['en_US', 'en']
07-03 04:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\translations, languages=['en_US', 'en']
07-03 04:21 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 04:21 INFO   root: Received settings
07-03 04:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl622D.tmp\translations, languages=['en_US', 'en']
07-03 04:21 DEBUG  TaskList: # Running tasklist...
07-03 04:21 DEBUG  TaskList: ## Running select_target_dir...
07-03 04:21 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:21 DEBUG  TaskList: # Cancelling tasklist
07-03 04:21 DEBUG  TaskList: # Finished tasklist
07-03 04:21 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:27 INFO   root: === wubi 11.04 rev211 ===
07-03 04:27 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 04:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 04:27 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\data
07-03 04:27 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\bin\7z.exe
07-03 04:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 04:27 DEBUG  CommonBackend: Fetching basic info...
07-03 04:27 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 04:27 DEBUG  CommonBackend: platform=win32
07-03 04:27 DEBUG  CommonBackend: osname=nt
07-03 04:27 DEBUG  CommonBackend: language=en_US
07-03 04:27 DEBUG  CommonBackend: encoding=cp1252
07-03 04:27 DEBUG  WindowsBackend: arch=amd64
07-03 04:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\data\isolist.ini
07-03 04:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 04:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 04:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 04:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 04:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 04:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 04:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 04:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 04:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 04:27 DEBUG  WindowsBackend: Fetching host info...
07-03 04:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 04:27 DEBUG  WindowsBackend: windows version=vista
07-03 04:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 04:27 DEBUG  WindowsBackend: windows_sp=None
07-03 04:27 DEBUG  WindowsBackend: windows_build=7600
07-03 04:27 DEBUG  WindowsBackend: gmt=-6
07-03 04:27 DEBUG  WindowsBackend: country=US
07-03 04:27 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 04:27 DEBUG  WindowsBackend: windows_username=Ashton
07-03 04:27 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 04:27 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 04:27 DEBUG  WindowsBackend: windows_language_code=1033
07-03 04:27 DEBUG  WindowsBackend: windows_language=English
07-03 04:27 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 04:27 DEBUG  WindowsBackend: bootloader=vista
07-03 04:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 228231.738281 mb free ntfs)
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(C: hd 228231.738281 mb free ntfs)
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 04:27 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 04:27 DEBUG  WindowsBackend: uninstaller_path=None
07-03 04:27 DEBUG  WindowsBackend: previous_target_dir=None
07-03 04:27 DEBUG  WindowsBackend: previous_distro_name=None
07-03 04:27 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 04:27 DEBUG  WindowsBackend: keyboard_layout=us
07-03 04:27 DEBUG  WindowsBackend: keyboard_variant=
07-03 04:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 04:27 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 04:27 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 04:27 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 04:27 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:27 DEBUG  CommonBackend: Searching for local CDs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Ubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Ubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Ubuntu Netbook CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Kubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Kubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Xubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Xubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Mythbuntu CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp is a valid Mythbuntu CD
07-03 04:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 04:27 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 04:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 04:27 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 04:27 INFO   root: Running the CD menu...
07-03 04:27 DEBUG  WindowsFrontend: __init__...
07-03 04:27 DEBUG  WindowsFrontend: on_init...
07-03 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\translations, languages=['en_US', 'en']
07-03 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\translations, languages=['en_US', 'en']
07-03 04:27 INFO   root: CD menu finished
07-03 04:27 INFO   root: Running the installer...
07-03 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\translations, languages=['en_US', 'en']
07-03 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\translations, languages=['en_US', 'en']
07-03 04:28 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 04:28 INFO   root: Received settings
07-03 04:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl24A1.tmp\translations, languages=['en_US', 'en']
07-03 04:28 DEBUG  TaskList: # Running tasklist...
07-03 04:28 DEBUG  TaskList: ## Running select_target_dir...
07-03 04:28 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:28 DEBUG  TaskList: # Cancelling tasklist
07-03 04:28 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:28 DEBUG  TaskList: # Finished tasklist
07-03 04:28 INFO   root: === wubi 11.04 rev211 ===
07-03 04:28 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 04:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 04:28 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\data
07-03 04:28 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\bin\7z.exe
07-03 04:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 04:28 DEBUG  CommonBackend: Fetching basic info...
07-03 04:28 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 04:28 DEBUG  CommonBackend: platform=win32
07-03 04:28 DEBUG  CommonBackend: osname=nt
07-03 04:28 DEBUG  CommonBackend: language=en_US
07-03 04:28 DEBUG  CommonBackend: encoding=cp1252
07-03 04:28 DEBUG  WindowsBackend: arch=amd64
07-03 04:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\data\isolist.ini
07-03 04:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 04:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 04:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 04:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 04:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 04:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 04:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 04:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 04:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 04:28 DEBUG  WindowsBackend: Fetching host info...
07-03 04:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 04:28 DEBUG  WindowsBackend: windows version=vista
07-03 04:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 04:28 DEBUG  WindowsBackend: windows_sp=None
07-03 04:28 DEBUG  WindowsBackend: windows_build=7600
07-03 04:28 DEBUG  WindowsBackend: gmt=-6
07-03 04:28 DEBUG  WindowsBackend: country=US
07-03 04:28 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 04:28 DEBUG  WindowsBackend: windows_username=Ashton
07-03 04:28 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 04:28 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 04:28 DEBUG  WindowsBackend: windows_language_code=1033
07-03 04:28 DEBUG  WindowsBackend: windows_language=English
07-03 04:28 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 04:28 DEBUG  WindowsBackend: bootloader=vista
07-03 04:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 228228.964844 mb free ntfs)
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(C: hd 228228.964844 mb free ntfs)
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 04:28 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 04:28 DEBUG  WindowsBackend: uninstaller_path=None
07-03 04:28 DEBUG  WindowsBackend: previous_target_dir=None
07-03 04:28 DEBUG  WindowsBackend: previous_distro_name=None
07-03 04:28 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 04:28 DEBUG  WindowsBackend: keyboard_layout=us
07-03 04:28 DEBUG  WindowsBackend: keyboard_variant=
07-03 04:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 04:28 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 04:28 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 04:28 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 04:28 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 04:28 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 04:28 DEBUG  CommonBackend: Searching for local CDs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Ubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Ubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Ubuntu Netbook CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Kubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Kubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Xubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Xubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Mythbuntu CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp is a valid Mythbuntu CD
07-03 04:28 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 04:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 04:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 04:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 04:28 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 04:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 04:28 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 04:28 INFO   root: Running the CD menu...
07-03 04:28 DEBUG  WindowsFrontend: __init__...
07-03 04:28 DEBUG  WindowsFrontend: on_init...
07-03 04:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\translations, languages=['en_US', 'en']
07-03 04:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\translations, languages=['en_US', 'en']
07-03 04:28 INFO   root: CD menu finished
07-03 04:28 INFO   root: Running the installer...
07-03 04:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\translations, languages=['en_US', 'en']
07-03 04:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\translations, languages=['en_US', 'en']
07-03 04:29 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ace
07-03 04:29 INFO   root: Received settings
07-03 04:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl9B27.tmp\translations, languages=['en_US', 'en']
07-03 04:29 DEBUG  TaskList: # Running tasklist...
07-03 04:29 DEBUG  TaskList: ## Running select_target_dir...
07-03 04:29 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 04:29 DEBUG  TaskList: # Cancelling tasklist
07-03 04:29 DEBUG  TaskList: # Finished tasklist
07-03 04:29 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:31 INFO   root: === wubi 11.04 rev211 ===
07-03 05:31 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 05:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 05:31 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\data
07-03 05:31 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\bin\7z.exe
07-03 05:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 05:31 DEBUG  CommonBackend: Fetching basic info...
07-03 05:31 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 05:31 DEBUG  CommonBackend: platform=win32
07-03 05:31 DEBUG  CommonBackend: osname=nt
07-03 05:31 DEBUG  CommonBackend: language=en_US
07-03 05:31 DEBUG  CommonBackend: encoding=cp1252
07-03 05:31 DEBUG  WindowsBackend: arch=amd64
07-03 05:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\data\isolist.ini
07-03 05:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 05:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 05:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 05:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 05:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 05:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 05:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 05:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 05:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 05:31 DEBUG  WindowsBackend: Fetching host info...
07-03 05:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 05:31 DEBUG  WindowsBackend: windows version=vista
07-03 05:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 05:31 DEBUG  WindowsBackend: windows_sp=None
07-03 05:31 DEBUG  WindowsBackend: windows_build=7600
07-03 05:31 DEBUG  WindowsBackend: gmt=-6
07-03 05:31 DEBUG  WindowsBackend: country=US
07-03 05:31 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 05:31 DEBUG  WindowsBackend: windows_username=Ashton
07-03 05:31 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 05:31 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 05:31 DEBUG  WindowsBackend: windows_language_code=1033
07-03 05:31 DEBUG  WindowsBackend: windows_language=English
07-03 05:31 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 05:31 DEBUG  WindowsBackend: bootloader=vista
07-03 05:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227938.613281 mb free ntfs)
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(C: hd 227938.613281 mb free ntfs)
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 05:31 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 05:31 DEBUG  WindowsBackend: uninstaller_path=None
07-03 05:31 DEBUG  WindowsBackend: previous_target_dir=None
07-03 05:31 DEBUG  WindowsBackend: previous_distro_name=None
07-03 05:31 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 05:31 DEBUG  WindowsBackend: keyboard_layout=us
07-03 05:31 DEBUG  WindowsBackend: keyboard_variant=
07-03 05:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 05:31 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 05:31 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 05:31 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 05:31 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:31 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:31 DEBUG  CommonBackend: Searching for local CDs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Ubuntu Netbook CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 05:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-03 05:31 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 05:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 05:31 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-03 05:31 INFO   root: Running the CD menu...
07-03 05:31 DEBUG  WindowsFrontend: __init__...
07-03 05:31 DEBUG  WindowsFrontend: on_init...
07-03 05:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\translations, languages=['en_US', 'en']
07-03 05:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\translations, languages=['en_US', 'en']
07-03 05:32 INFO   root: CD menu finished
07-03 05:32 INFO   root: Running the installer...
07-03 05:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\translations, languages=['en_US', 'en']
07-03 05:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\translations, languages=['en_US', 'en']
07-03 05:32 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sebastain
07-03 05:32 INFO   root: Received settings
07-03 05:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylB924.tmp\translations, languages=['en_US', 'en']
07-03 05:32 DEBUG  TaskList: # Running tasklist...
07-03 05:32 DEBUG  TaskList: ## Running select_target_dir...
07-03 05:32 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:32 DEBUG  TaskList: # Cancelling tasklist
07-03 05:32 DEBUG  TaskList: # Finished tasklist
07-03 05:32 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:33 INFO   root: === wubi 11.04 rev211 ===
07-03 05:33 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 05:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 05:33 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\data
07-03 05:33 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\bin\7z.exe
07-03 05:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 05:33 DEBUG  CommonBackend: Fetching basic info...
07-03 05:33 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 05:33 DEBUG  CommonBackend: platform=win32
07-03 05:33 DEBUG  CommonBackend: osname=nt
07-03 05:33 DEBUG  CommonBackend: language=en_US
07-03 05:33 DEBUG  CommonBackend: encoding=cp1252
07-03 05:33 DEBUG  WindowsBackend: arch=amd64
07-03 05:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\data\isolist.ini
07-03 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 05:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 05:33 DEBUG  WindowsBackend: Fetching host info...
07-03 05:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 05:33 DEBUG  WindowsBackend: windows version=vista
07-03 05:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 05:33 DEBUG  WindowsBackend: windows_sp=None
07-03 05:33 DEBUG  WindowsBackend: windows_build=7600
07-03 05:33 DEBUG  WindowsBackend: gmt=-6
07-03 05:33 DEBUG  WindowsBackend: country=US
07-03 05:33 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 05:33 DEBUG  WindowsBackend: windows_username=Ashton
07-03 05:33 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 05:33 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 05:33 DEBUG  WindowsBackend: windows_language_code=1033
07-03 05:33 DEBUG  WindowsBackend: windows_language=English
07-03 05:33 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 05:33 DEBUG  WindowsBackend: bootloader=vista
07-03 05:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227936.179688 mb free ntfs)
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(C: hd 227936.179688 mb free ntfs)
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 05:33 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 05:34 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 05:34 DEBUG  WindowsBackend: uninstaller_path=None
07-03 05:34 DEBUG  WindowsBackend: previous_target_dir=None
07-03 05:34 DEBUG  WindowsBackend: previous_distro_name=None
07-03 05:34 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 05:34 DEBUG  WindowsBackend: keyboard_layout=us
07-03 05:34 DEBUG  WindowsBackend: keyboard_variant=
07-03 05:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 05:34 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 05:34 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 05:34 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 05:34 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:34 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:34 DEBUG  CommonBackend: Searching for local CDs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Ubuntu Netbook CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 05:34 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:34 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-03 05:34 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 05:34 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 05:34 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-03 05:34 INFO   root: Running the CD menu...
07-03 05:34 DEBUG  WindowsFrontend: __init__...
07-03 05:34 DEBUG  WindowsFrontend: on_init...
07-03 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\translations, languages=['en_US', 'en']
07-03 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\translations, languages=['en_US', 'en']
07-03 05:34 INFO   root: CD menu finished
07-03 05:34 INFO   root: Running the installer...
07-03 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\translations, languages=['en_US', 'en']
07-03 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\translations, languages=['en_US', 'en']
07-03 05:34 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sebastain
07-03 05:34 INFO   root: Received settings
07-03 05:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylA5A4.tmp\translations, languages=['en_US', 'en']
07-03 05:34 DEBUG  TaskList: # Running tasklist...
07-03 05:34 DEBUG  TaskList: ## Running select_target_dir...
07-03 05:34 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:34 DEBUG  TaskList: # Cancelling tasklist
07-03 05:34 DEBUG  TaskList: # Finished tasklist
07-03 05:34 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:56 INFO   root: === wubi 11.04 rev211 ===
07-03 05:56 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 05:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-03 05:56 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\data
07-03 05:56 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\bin\7z.exe
07-03 05:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 05:56 DEBUG  CommonBackend: Fetching basic info...
07-03 05:56 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-03 05:56 DEBUG  CommonBackend: platform=win32
07-03 05:56 DEBUG  CommonBackend: osname=nt
07-03 05:56 DEBUG  CommonBackend: language=en_US
07-03 05:56 DEBUG  CommonBackend: encoding=cp1252
07-03 05:56 DEBUG  WindowsBackend: arch=amd64
07-03 05:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\data\isolist.ini
07-03 05:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 05:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 05:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 05:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 05:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 05:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 05:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 05:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 05:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 05:56 DEBUG  WindowsBackend: Fetching host info...
07-03 05:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 05:56 DEBUG  WindowsBackend: windows version=vista
07-03 05:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 05:56 DEBUG  WindowsBackend: windows_sp=None
07-03 05:56 DEBUG  WindowsBackend: windows_build=7600
07-03 05:56 DEBUG  WindowsBackend: gmt=-6
07-03 05:56 DEBUG  WindowsBackend: country=US
07-03 05:56 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 05:56 DEBUG  WindowsBackend: windows_username=Ashton
07-03 05:56 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 05:56 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 05:56 DEBUG  WindowsBackend: windows_language_code=1033
07-03 05:56 DEBUG  WindowsBackend: windows_language=English
07-03 05:56 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 05:56 DEBUG  WindowsBackend: bootloader=vista
07-03 05:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227915.117188 mb free ntfs)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(C: hd 227915.113281 mb free ntfs)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 05:56 DEBUG  WindowsBackend: uninstaller_path=None
07-03 05:56 DEBUG  WindowsBackend: previous_target_dir=None
07-03 05:56 DEBUG  WindowsBackend: previous_distro_name=None
07-03 05:56 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 05:56 DEBUG  WindowsBackend: keyboard_layout=us
07-03 05:56 DEBUG  WindowsBackend: keyboard_variant=
07-03 05:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 05:56 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 05:56 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 05:56 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 05:56 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  CommonBackend: Searching for local CDs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 05:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 05:56 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-03 05:56 INFO   root: Running the CD menu...
07-03 05:56 DEBUG  WindowsFrontend: __init__...
07-03 05:56 DEBUG  WindowsFrontend: on_init...
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\translations, languages=['en_US', 'en']
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\translations, languages=['en_US', 'en']
07-03 05:56 INFO   root: CD menu finished
07-03 05:56 INFO   root: Running the installer...
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\translations, languages=['en_US', 'en']
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\translations, languages=['en_US', 'en']
07-03 05:56 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 05:56 INFO   root: Received settings
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl2011.tmp\translations, languages=['en_US', 'en']
07-03 05:56 DEBUG  TaskList: # Running tasklist...
07-03 05:56 DEBUG  TaskList: ## Running select_target_dir...
07-03 05:56 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:56 DEBUG  TaskList: # Cancelling tasklist
07-03 05:56 DEBUG  TaskList: # Finished tasklist
07-03 05:56 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:56 INFO   root: === wubi 11.04 rev211 ===
07-03 05:56 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 05:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 05:56 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\data
07-03 05:56 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\bin\7z.exe
07-03 05:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 05:56 DEBUG  CommonBackend: Fetching basic info...
07-03 05:56 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 05:56 DEBUG  CommonBackend: platform=win32
07-03 05:56 DEBUG  CommonBackend: osname=nt
07-03 05:56 DEBUG  CommonBackend: language=en_US
07-03 05:56 DEBUG  CommonBackend: encoding=cp1252
07-03 05:56 DEBUG  WindowsBackend: arch=amd64
07-03 05:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\data\isolist.ini
07-03 05:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 05:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 05:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 05:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 05:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 05:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 05:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 05:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 05:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 05:56 DEBUG  WindowsBackend: Fetching host info...
07-03 05:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 05:56 DEBUG  WindowsBackend: windows version=vista
07-03 05:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 05:56 DEBUG  WindowsBackend: windows_sp=None
07-03 05:56 DEBUG  WindowsBackend: windows_build=7600
07-03 05:56 DEBUG  WindowsBackend: gmt=-6
07-03 05:56 DEBUG  WindowsBackend: country=US
07-03 05:56 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 05:56 DEBUG  WindowsBackend: windows_username=Ashton
07-03 05:56 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 05:56 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 05:56 DEBUG  WindowsBackend: windows_language_code=1033
07-03 05:56 DEBUG  WindowsBackend: windows_language=English
07-03 05:56 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 05:56 DEBUG  WindowsBackend: bootloader=vista
07-03 05:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227915.011719 mb free ntfs)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(C: hd 227915.011719 mb free ntfs)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 05:56 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 05:56 DEBUG  WindowsBackend: uninstaller_path=None
07-03 05:56 DEBUG  WindowsBackend: previous_target_dir=None
07-03 05:56 DEBUG  WindowsBackend: previous_distro_name=None
07-03 05:56 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 05:56 DEBUG  WindowsBackend: keyboard_layout=us
07-03 05:56 DEBUG  WindowsBackend: keyboard_variant=
07-03 05:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 05:56 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 05:56 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 05:56 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 05:56 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 05:56 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 05:56 DEBUG  CommonBackend: Searching for local CDs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 05:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 05:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-03 05:56 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 05:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 05:56 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-03 05:56 INFO   root: Running the CD menu...
07-03 05:56 DEBUG  WindowsFrontend: __init__...
07-03 05:56 DEBUG  WindowsFrontend: on_init...
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\translations, languages=['en_US', 'en']
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\translations, languages=['en_US', 'en']
07-03 05:56 INFO   root: CD menu finished
07-03 05:56 INFO   root: Running the installer...
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\translations, languages=['en_US', 'en']
07-03 05:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\translations, languages=['en_US', 'en']
07-03 05:57 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 05:57 INFO   root: Received settings
07-03 05:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pylBB37.tmp\translations, languages=['en_US', 'en']
07-03 05:57 DEBUG  TaskList: # Running tasklist...
07-03 05:57 DEBUG  TaskList: ## Running select_target_dir...
07-03 05:57 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:57 DEBUG  TaskList: # Cancelling tasklist
07-03 05:57 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 05:57 DEBUG  TaskList: # Finished tasklist
07-03 06:13 INFO   root: === wubi 11.04 rev211 ===
07-03 06:13 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 06:13 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"']
07-03 06:13 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\data
07-03 06:13 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\bin\7z.exe
07-03 06:13 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 06:13 DEBUG  CommonBackend: Fetching basic info...
07-03 06:13 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-03 06:13 DEBUG  CommonBackend: platform=win32
07-03 06:13 DEBUG  CommonBackend: osname=nt
07-03 06:13 DEBUG  CommonBackend: language=en_US
07-03 06:13 DEBUG  CommonBackend: encoding=cp1252
07-03 06:13 DEBUG  WindowsBackend: arch=amd64
07-03 06:13 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\data\isolist.ini
07-03 06:13 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 06:13 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 06:13 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 06:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 06:13 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 06:13 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 06:13 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 06:13 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 06:13 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 06:13 DEBUG  WindowsBackend: Fetching host info...
07-03 06:13 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 06:13 DEBUG  WindowsBackend: windows version=vista
07-03 06:13 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 06:13 DEBUG  WindowsBackend: windows_sp=None
07-03 06:13 DEBUG  WindowsBackend: windows_build=7600
07-03 06:13 DEBUG  WindowsBackend: gmt=-6
07-03 06:13 DEBUG  WindowsBackend: country=US
07-03 06:13 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 06:13 DEBUG  WindowsBackend: windows_username=Ashton
07-03 06:13 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 06:13 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 06:13 DEBUG  WindowsBackend: windows_language_code=1033
07-03 06:13 DEBUG  WindowsBackend: windows_language=English
07-03 06:13 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 06:13 DEBUG  WindowsBackend: bootloader=vista
07-03 06:13 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227844.578125 mb free ntfs)
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(C: hd 227844.578125 mb free ntfs)
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(K: cd 0.0 mb free )
07-03 06:13 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 06:13 DEBUG  WindowsBackend: uninstaller_path=None
07-03 06:13 DEBUG  WindowsBackend: previous_target_dir=None
07-03 06:13 DEBUG  WindowsBackend: previous_distro_name=None
07-03 06:13 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 06:13 DEBUG  WindowsBackend: keyboard_layout=us
07-03 06:13 DEBUG  WindowsBackend: keyboard_variant=
07-03 06:13 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 06:13 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 06:13 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 06:13 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 06:13 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:13 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:13 DEBUG  CommonBackend: Searching for local CDs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Ubuntu Netbook CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 06:13 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:13 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-03 06:13 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 06:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 06:13 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-03 06:13 INFO   root: Running the CD menu...
07-03 06:13 DEBUG  WindowsFrontend: __init__...
07-03 06:13 DEBUG  WindowsFrontend: on_init...
07-03 06:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\translations, languages=['en_US', 'en']
07-03 06:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\translations, languages=['en_US', 'en']
07-03 06:13 INFO   root: CD menu finished
07-03 06:13 INFO   root: Running the installer...
07-03 06:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\translations, languages=['en_US', 'en']
07-03 06:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\translations, languages=['en_US', 'en']
07-03 06:13 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 06:13 INFO   root: Received settings
07-03 06:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6E21.tmp\translations, languages=['en_US', 'en']
07-03 06:13 DEBUG  TaskList: # Running tasklist...
07-03 06:13 DEBUG  TaskList: ## Running select_target_dir...
07-03 06:13 ERROR  TaskList: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 06:13 DEBUG  TaskList: # Cancelling tasklist
07-03 06:13 DEBUG  TaskList: # Finished tasklist
07-03 06:13 ERROR  root: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into C:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
07-03 06:15 INFO   root: === wubi 11.04 rev211 ===
07-03 06:15 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 06:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="I:\\wubi.exe"', '--cdmenu']
07-03 06:15 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\data
07-03 06:15 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\bin\7z.exe
07-03 06:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 06:15 DEBUG  CommonBackend: Fetching basic info...
07-03 06:15 DEBUG  CommonBackend: original_exe=I:\wubi.exe
07-03 06:15 DEBUG  CommonBackend: platform=win32
07-03 06:15 DEBUG  CommonBackend: osname=nt
07-03 06:15 DEBUG  CommonBackend: language=en_US
07-03 06:15 DEBUG  CommonBackend: encoding=cp1252
07-03 06:15 DEBUG  WindowsBackend: arch=amd64
07-03 06:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\data\isolist.ini
07-03 06:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 06:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 06:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 06:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 06:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 06:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 06:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 06:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 06:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 06:15 DEBUG  WindowsBackend: Fetching host info...
07-03 06:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 06:15 DEBUG  WindowsBackend: windows version=vista
07-03 06:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 06:15 DEBUG  WindowsBackend: windows_sp=None
07-03 06:15 DEBUG  WindowsBackend: windows_build=7600
07-03 06:15 DEBUG  WindowsBackend: gmt=-6
07-03 06:15 DEBUG  WindowsBackend: country=US
07-03 06:15 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 06:15 DEBUG  WindowsBackend: windows_username=Ashton
07-03 06:15 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 06:15 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 06:15 DEBUG  WindowsBackend: windows_language_code=1033
07-03 06:15 DEBUG  WindowsBackend: windows_language=English
07-03 06:15 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 06:15 DEBUG  WindowsBackend: bootloader=vista
07-03 06:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227840.59375 mb free ntfs)
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(C: hd 227840.59375 mb free ntfs)
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 06:15 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 06:15 DEBUG  WindowsBackend: uninstaller_path=None
07-03 06:15 DEBUG  WindowsBackend: previous_target_dir=None
07-03 06:15 DEBUG  WindowsBackend: previous_distro_name=None
07-03 06:15 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 06:15 DEBUG  WindowsBackend: keyboard_layout=us
07-03 06:15 DEBUG  WindowsBackend: keyboard_variant=
07-03 06:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 06:15 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 06:15 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 06:15 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 06:15 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:15 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:15 DEBUG  CommonBackend: Searching for local CDs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Ubuntu Netbook CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-03 06:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-03 06:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-03 06:15 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 06:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 06:15 INFO   Distro: Found a valid CD for Ubuntu: H:\
07-03 06:15 INFO   root: Running the CD menu...
07-03 06:15 DEBUG  WindowsFrontend: __init__...
07-03 06:15 DEBUG  WindowsFrontend: on_init...
07-03 06:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\translations, languages=['en_US', 'en']
07-03 06:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\translations, languages=['en_US', 'en']
07-03 06:15 INFO   root: CD menu finished
07-03 06:15 INFO   root: Running the installer...
07-03 06:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\translations, languages=['en_US', 'en']
07-03 06:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl65B8.tmp\translations, languages=['en_US', 'en']
07-03 06:15 INFO   WindowsFrontend: Operation cancelled
07-03 06:15 DEBUG  WindowsFrontend: frontend.quit
07-03 06:15 DEBUG  WindowsFrontend: frontend.on_quit
07-03 06:15 DEBUG  root: application.on_quit
07-03 06:15 INFO   root: sys.exit
07-03 06:21 INFO   root: === wubi 11.04 rev211 ===
07-03 06:21 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 06:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
07-03 06:21 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\data
07-03 06:21 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\bin\7z.exe
07-03 06:21 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 06:21 DEBUG  CommonBackend: Fetching basic info...
07-03 06:21 DEBUG  CommonBackend: original_exe=F:\wubi.exe
07-03 06:21 DEBUG  CommonBackend: platform=win32
07-03 06:21 DEBUG  CommonBackend: osname=nt
07-03 06:21 DEBUG  CommonBackend: language=en_US
07-03 06:21 DEBUG  CommonBackend: encoding=cp1252
07-03 06:21 DEBUG  WindowsBackend: arch=amd64
07-03 06:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\data\isolist.ini
07-03 06:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 06:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 06:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 06:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 06:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 06:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 06:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 06:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 06:21 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 06:21 DEBUG  WindowsBackend: Fetching host info...
07-03 06:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 06:21 DEBUG  WindowsBackend: windows version=vista
07-03 06:21 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 06:21 DEBUG  WindowsBackend: windows_sp=None
07-03 06:21 DEBUG  WindowsBackend: windows_build=7600
07-03 06:21 DEBUG  WindowsBackend: gmt=-6
07-03 06:21 DEBUG  WindowsBackend: country=US
07-03 06:21 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 06:21 DEBUG  WindowsBackend: windows_username=Ashton
07-03 06:21 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 06:21 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 06:21 DEBUG  WindowsBackend: windows_language_code=1033
07-03 06:21 DEBUG  WindowsBackend: windows_language=English
07-03 06:21 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 06:21 DEBUG  WindowsBackend: bootloader=vista
07-03 06:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227828.320313 mb free ntfs)
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(C: hd 227828.320313 mb free ntfs)
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 06:21 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 06:21 DEBUG  WindowsBackend: uninstaller_path=None
07-03 06:21 DEBUG  WindowsBackend: previous_target_dir=None
07-03 06:21 DEBUG  WindowsBackend: previous_distro_name=None
07-03 06:21 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 06:21 DEBUG  WindowsBackend: keyboard_layout=us
07-03 06:21 DEBUG  WindowsBackend: keyboard_variant=
07-03 06:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 06:21 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 06:21 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 06:21 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 06:21 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:21 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:21 DEBUG  CommonBackend: Searching for local CDs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Ubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Ubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Ubuntu Netbook CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Kubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Kubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Xubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Xubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Mythbuntu CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp is a valid Mythbuntu CD
07-03 06:21 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 06:21 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 06:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 06:21 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 06:21 INFO   root: Running the CD menu...
07-03 06:21 DEBUG  WindowsFrontend: __init__...
07-03 06:21 DEBUG  WindowsFrontend: on_init...
07-03 06:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\translations, languages=['en_US', 'en']
07-03 06:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\translations, languages=['en_US', 'en']
07-03 06:21 INFO   root: CD menu finished
07-03 06:21 INFO   root: Running the installer...
07-03 06:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\translations, languages=['en_US', 'en']
07-03 06:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\translations, languages=['en_US', 'en']
07-03 06:21 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 06:21 INFO   root: Received settings
07-03 06:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\translations, languages=['en_US', 'en']
07-03 06:21 DEBUG  TaskList: # Running tasklist...
07-03 06:21 DEBUG  TaskList: ## Running select_target_dir...
07-03 06:21 INFO   WindowsBackend: Installing into C:\ubuntu
07-03 06:21 DEBUG  TaskList: ## Finished select_target_dir
07-03 06:21 DEBUG  TaskList: ## Running create_dir_structure...
07-03 06:21 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-03 06:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-03 06:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-03 06:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-03 06:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-03 06:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-03 06:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-03 06:21 DEBUG  TaskList: ## Finished create_dir_structure
07-03 06:21 DEBUG  TaskList: ## Running uncompress_target_dir...
07-03 06:22 DEBUG  TaskList: ## Finished uncompress_target_dir
07-03 06:22 DEBUG  TaskList: ## Running create_uninstaller...
07-03 06:22 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-03 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-03 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-03 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-03 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-03 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 06:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 06:22 DEBUG  TaskList: ## Finished create_uninstaller
07-03 06:22 DEBUG  TaskList: ## Running copy_installation_files...
07-03 06:22 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-03 06:22 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\winboot -> C:\ubuntu\winboot
07-03 06:22 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl6C3D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-03 06:22 DEBUG  TaskList: ## Finished copy_installation_files
07-03 06:22 DEBUG  TaskList: ## Running get_iso...
07-03 06:22 DEBUG  TaskList: New task copy_file
07-03 06:22 DEBUG  TaskList: ### Running copy_file...
07-03 06:23 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-03 06:23 DEBUG  TaskList: # Cancelling tasklist
07-03 06:23 DEBUG  TaskList: New task check_iso
07-03 06:23 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-03 06:23 DEBUG  CommonBackend: Searching for local ISO
07-03 06:23 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-03 06:23 DEBUG  TaskList: New task get_metalink
07-03 06:23 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 06:23 DEBUG  TaskList: # Cancelling tasklist
07-03 06:23 DEBUG  TaskList: # Finished tasklist
07-03 06:27 INFO   root: === wubi 11.04 rev211 ===
07-03 06:27 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 06:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\wubi.exe"', '--cdmenu']
07-03 06:27 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\data
07-03 06:27 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\bin\7z.exe
07-03 06:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 06:27 DEBUG  CommonBackend: Fetching basic info...
07-03 06:27 DEBUG  CommonBackend: original_exe=H:\wubi.exe
07-03 06:27 DEBUG  CommonBackend: platform=win32
07-03 06:27 DEBUG  CommonBackend: osname=nt
07-03 06:27 DEBUG  CommonBackend: language=en_US
07-03 06:27 DEBUG  CommonBackend: encoding=cp1252
07-03 06:27 DEBUG  WindowsBackend: arch=amd64
07-03 06:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\data\isolist.ini
07-03 06:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 06:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 06:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 06:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 06:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 06:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 06:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 06:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 06:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 06:27 DEBUG  WindowsBackend: Fetching host info...
07-03 06:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 06:27 DEBUG  WindowsBackend: windows version=vista
07-03 06:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 06:27 DEBUG  WindowsBackend: windows_sp=None
07-03 06:27 DEBUG  WindowsBackend: windows_build=7600
07-03 06:27 DEBUG  WindowsBackend: gmt=-6
07-03 06:27 DEBUG  WindowsBackend: country=US
07-03 06:27 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 06:27 DEBUG  WindowsBackend: windows_username=Ashton
07-03 06:27 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 06:27 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 06:27 DEBUG  WindowsBackend: windows_language_code=1033
07-03 06:27 DEBUG  WindowsBackend: windows_language=English
07-03 06:27 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 06:27 DEBUG  WindowsBackend: bootloader=vista
07-03 06:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227357.617188 mb free ntfs)
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(C: hd 227357.617188 mb free ntfs)
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 06:27 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 06:27 DEBUG  WindowsBackend: uninstaller_path=None
07-03 06:27 DEBUG  WindowsBackend: previous_target_dir=None
07-03 06:27 DEBUG  WindowsBackend: previous_distro_name=None
07-03 06:27 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 06:27 DEBUG  WindowsBackend: keyboard_layout=us
07-03 06:27 DEBUG  WindowsBackend: keyboard_variant=
07-03 06:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 06:27 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 06:27 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 06:27 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 06:27 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:27 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:27 DEBUG  CommonBackend: Searching for local CDs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Ubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Ubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Ubuntu Netbook CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Kubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Kubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Xubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Xubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Mythbuntu CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp is a valid Mythbuntu CD
07-03 06:27 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 06:27 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 06:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 06:27 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 06:27 INFO   root: Running the CD menu...
07-03 06:27 DEBUG  WindowsFrontend: __init__...
07-03 06:27 DEBUG  WindowsFrontend: on_init...
07-03 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\translations, languages=['en_US', 'en']
07-03 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\translations, languages=['en_US', 'en']
07-03 06:27 INFO   root: CD menu finished
07-03 06:27 INFO   root: Running the installer...
07-03 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\translations, languages=['en_US', 'en']
07-03 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\translations, languages=['en_US', 'en']
07-03 06:27 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=3000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 06:27 INFO   root: Received settings
07-03 06:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\translations, languages=['en_US', 'en']
07-03 06:27 DEBUG  TaskList: # Running tasklist...
07-03 06:27 DEBUG  TaskList: ## Running select_target_dir...
07-03 06:27 INFO   WindowsBackend: Installing into C:\ubuntu
07-03 06:27 DEBUG  TaskList: ## Finished select_target_dir
07-03 06:27 DEBUG  TaskList: ## Running create_dir_structure...
07-03 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-03 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-03 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-03 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-03 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-03 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-03 06:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-03 06:27 DEBUG  TaskList: ## Finished create_dir_structure
07-03 06:27 DEBUG  TaskList: ## Running uncompress_target_dir...
07-03 06:27 DEBUG  TaskList: ## Finished uncompress_target_dir
07-03 06:27 DEBUG  TaskList: ## Running create_uninstaller...
07-03 06:27 DEBUG  WindowsBackend: Copying uninstaller H:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-03 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-03 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-03 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-03 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-03 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 06:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 06:27 DEBUG  TaskList: ## Finished create_uninstaller
07-03 06:27 DEBUG  TaskList: ## Running copy_installation_files...
07-03 06:27 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-03 06:27 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\winboot -> C:\ubuntu\winboot
07-03 06:27 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl404E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-03 06:27 DEBUG  TaskList: ## Finished copy_installation_files
07-03 06:27 DEBUG  TaskList: ## Running get_iso...
07-03 06:27 DEBUG  TaskList: New task copy_file
07-03 06:27 DEBUG  TaskList: ### Running copy_file...
07-03 06:29 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-03 06:29 DEBUG  TaskList: # Cancelling tasklist
07-03 06:29 DEBUG  TaskList: New task check_iso
07-03 06:29 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-03 06:29 DEBUG  CommonBackend: Searching for local ISO
07-03 06:29 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-03 06:29 DEBUG  TaskList: New task get_metalink
07-03 06:29 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 06:29 DEBUG  TaskList: # Cancelling tasklist
07-03 06:29 DEBUG  TaskList: # Finished tasklist
07-03 06:39 INFO   root: === wubi 11.04 rev211 ===
07-03 06:39 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 06:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 06:39 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\data
07-03 06:39 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\bin\7z.exe
07-03 06:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 06:39 DEBUG  CommonBackend: Fetching basic info...
07-03 06:39 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 06:39 DEBUG  CommonBackend: platform=win32
07-03 06:39 DEBUG  CommonBackend: osname=nt
07-03 06:39 DEBUG  CommonBackend: language=en_US
07-03 06:39 DEBUG  CommonBackend: encoding=cp1252
07-03 06:39 DEBUG  WindowsBackend: arch=amd64
07-03 06:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\data\isolist.ini
07-03 06:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 06:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 06:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 06:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 06:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 06:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 06:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 06:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 06:39 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 06:39 DEBUG  WindowsBackend: Fetching host info...
07-03 06:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 06:39 DEBUG  WindowsBackend: windows version=vista
07-03 06:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 06:39 DEBUG  WindowsBackend: windows_sp=None
07-03 06:39 DEBUG  WindowsBackend: windows_build=7600
07-03 06:39 DEBUG  WindowsBackend: gmt=-6
07-03 06:39 DEBUG  WindowsBackend: country=US
07-03 06:39 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 06:39 DEBUG  WindowsBackend: windows_username=Ashton
07-03 06:39 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 06:39 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 06:39 DEBUG  WindowsBackend: windows_language_code=1033
07-03 06:39 DEBUG  WindowsBackend: windows_language=English
07-03 06:39 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 06:39 DEBUG  WindowsBackend: bootloader=vista
07-03 06:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227309.652344 mb free ntfs)
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(C: hd 227309.652344 mb free ntfs)
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 06:39 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 06:39 DEBUG  WindowsBackend: uninstaller_path=None
07-03 06:39 DEBUG  WindowsBackend: previous_target_dir=None
07-03 06:39 DEBUG  WindowsBackend: previous_distro_name=None
07-03 06:39 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 06:39 DEBUG  WindowsBackend: keyboard_layout=us
07-03 06:39 DEBUG  WindowsBackend: keyboard_variant=
07-03 06:39 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 06:39 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 06:39 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 06:39 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 06:39 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:39 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:39 DEBUG  CommonBackend: Searching for local CDs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Ubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Ubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Ubuntu Netbook CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Kubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Kubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Xubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Xubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Mythbuntu CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp is a valid Mythbuntu CD
07-03 06:39 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 06:39 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 06:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 06:39 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 06:39 INFO   root: Running the CD menu...
07-03 06:39 DEBUG  WindowsFrontend: __init__...
07-03 06:39 DEBUG  WindowsFrontend: on_init...
07-03 06:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\translations, languages=['en_US', 'en']
07-03 06:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\translations, languages=['en_US', 'en']
07-03 06:40 INFO   root: CD menu finished
07-03 06:40 INFO   root: Running the installer...
07-03 06:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\translations, languages=['en_US', 'en']
07-03 06:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\translations, languages=['en_US', 'en']
07-03 06:40 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sebastian
07-03 06:40 INFO   root: Received settings
07-03 06:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\translations, languages=['en_US', 'en']
07-03 06:40 DEBUG  TaskList: # Running tasklist...
07-03 06:40 DEBUG  TaskList: ## Running select_target_dir...
07-03 06:40 INFO   WindowsBackend: Installing into C:\ubuntu
07-03 06:40 DEBUG  TaskList: ## Finished select_target_dir
07-03 06:40 DEBUG  TaskList: ## Running create_dir_structure...
07-03 06:40 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-03 06:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-03 06:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-03 06:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-03 06:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-03 06:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-03 06:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-03 06:40 DEBUG  TaskList: ## Finished create_dir_structure
07-03 06:40 DEBUG  TaskList: ## Running uncompress_target_dir...
07-03 06:40 DEBUG  TaskList: ## Finished uncompress_target_dir
07-03 06:40 DEBUG  TaskList: ## Running create_uninstaller...
07-03 06:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Ashton\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-03 06:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-03 06:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-03 06:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 06:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-03 06:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-03 06:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 06:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 06:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 06:40 DEBUG  TaskList: ## Finished create_uninstaller
07-03 06:40 DEBUG  TaskList: ## Running copy_installation_files...
07-03 06:40 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-03 06:40 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\winboot -> C:\ubuntu\winboot
07-03 06:40 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl699.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-03 06:40 DEBUG  TaskList: ## Finished copy_installation_files
07-03 06:40 DEBUG  TaskList: ## Running get_iso...
07-03 06:40 DEBUG  TaskList: New task copy_file
07-03 06:40 DEBUG  TaskList: ### Running copy_file...
07-03 06:42 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-03 06:42 DEBUG  TaskList: # Cancelling tasklist
07-03 06:42 DEBUG  TaskList: New task check_iso
07-03 06:42 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-03 06:42 DEBUG  CommonBackend: Searching for local ISO
07-03 06:42 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-03 06:42 DEBUG  TaskList: New task get_metalink
07-03 06:42 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 06:42 DEBUG  TaskList: # Cancelling tasklist
07-03 06:42 DEBUG  TaskList: # Finished tasklist
07-03 06:58 INFO   root: === wubi 11.04 rev211 ===
07-03 06:58 DEBUG  root: Logfile is c:\users\ashton\appdata\local\temp\wubi-11.04-rev211.log
07-03 06:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Ashton\\Downloads\\wubi.exe"']
07-03 06:58 DEBUG  CommonBackend: data_dir=C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\data
07-03 06:58 DEBUG  WindowsBackend: 7z=C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\bin\7z.exe
07-03 06:58 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-03 06:58 DEBUG  CommonBackend: Fetching basic info...
07-03 06:58 DEBUG  CommonBackend: original_exe=C:\Users\Ashton\Downloads\wubi.exe
07-03 06:58 DEBUG  CommonBackend: platform=win32
07-03 06:58 DEBUG  CommonBackend: osname=nt
07-03 06:58 DEBUG  CommonBackend: language=en_US
07-03 06:58 DEBUG  CommonBackend: encoding=cp1252
07-03 06:58 DEBUG  WindowsBackend: arch=amd64
07-03 06:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\data\isolist.ini
07-03 06:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-03 06:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-03 06:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-03 06:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-03 06:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-03 06:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-03 06:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-03 06:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-03 06:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-03 06:58 DEBUG  WindowsBackend: Fetching host info...
07-03 06:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-03 06:58 DEBUG  WindowsBackend: windows version=vista
07-03 06:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-03 06:58 DEBUG  WindowsBackend: windows_sp=None
07-03 06:58 DEBUG  WindowsBackend: windows_build=7600
07-03 06:58 DEBUG  WindowsBackend: gmt=-6
07-03 06:58 DEBUG  WindowsBackend: country=US
07-03 06:58 DEBUG  WindowsBackend: timezone=America/Chicago
07-03 06:58 DEBUG  WindowsBackend: windows_username=Ashton
07-03 06:58 DEBUG  WindowsBackend: user_full_name=Ashton
07-03 06:58 DEBUG  WindowsBackend: user_directory=C:\Users\Ashton
07-03 06:58 DEBUG  WindowsBackend: windows_language_code=1033
07-03 06:58 DEBUG  WindowsBackend: windows_language=English
07-03 06:58 DEBUG  WindowsBackend: processor_name=Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
07-03 06:58 DEBUG  WindowsBackend: bootloader=vista
07-03 06:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 227802.257813 mb free ntfs)
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(C: hd 227802.257813 mb free ntfs)
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(D: hd 2335.59765625 mb free ntfs)
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(E: hd 95.4150390625 mb free fat32)
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(G: removable 1889.04296875 mb free fat32)
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-03 06:58 DEBUG  WindowsBackend: drive=Drive(L: removable 2708.25 mb free fat32)
07-03 06:58 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-03 06:58 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-03 06:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-03 06:58 DEBUG  WindowsBackend: keyboard_id=67699721
07-03 06:58 DEBUG  WindowsBackend: keyboard_layout=us
07-03 06:58 DEBUG  WindowsBackend: keyboard_variant=
07-03 06:58 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-03 06:58 DEBUG  CommonBackend: locale=en_US.UTF-8
07-03 06:58 DEBUG  WindowsBackend: total_memory_mb=3002.921875
07-03 06:58 DEBUG  CommonBackend: Searching ISOs on USB devices
07-03 06:58 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  Distro:   checking Ubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  Distro:   checking Ubuntu Netbook ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  Distro:   checking Kubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  Distro:   checking Xubuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  Distro:   checking Mythbuntu ISO L:\ubuntu-11.04-desktop-i386.iso
07-03 06:58 DEBUG  Distro:     wrong size: 251633664 < 600000000
07-03 06:58 DEBUG  CommonBackend: Searching for local CDs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Ubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Ubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Ubuntu Netbook CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Kubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Kubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Xubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Xubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Mythbuntu CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp is a valid Mythbuntu CD
07-03 06:58 DEBUG  Distro:     does not contain C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-03 06:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-03 06:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-03 06:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-03 06:58 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
07-03 06:58 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
07-03 06:58 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-03 06:58 INFO   root: Running the CD menu...
07-03 06:58 DEBUG  WindowsFrontend: __init__...
07-03 06:58 DEBUG  WindowsFrontend: on_init...
07-03 06:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\translations, languages=['en_US', 'en']
07-03 06:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\translations, languages=['en_US', 'en']
07-03 06:58 INFO   root: CD menu finished
07-03 06:58 INFO   root: Running the installer...
07-03 06:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\translations, languages=['en_US', 'en']
07-03 06:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\translations, languages=['en_US', 'en']
07-03 06:59 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=ashton
07-03 06:59 INFO   root: Received settings
07-03 06:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\translations, languages=['en_US', 'en']
07-03 06:59 DEBUG  TaskList: # Running tasklist...
07-03 06:59 DEBUG  TaskList: ## Running select_target_dir...
07-03 06:59 INFO   WindowsBackend: Installing into C:\ubuntu
07-03 06:59 DEBUG  TaskList: ## Finished select_target_dir
07-03 06:59 DEBUG  TaskList: ## Running create_dir_structure...
07-03 06:59 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-03 06:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-03 06:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-03 06:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-03 06:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-03 06:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-03 06:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-03 06:59 DEBUG  TaskList: ## Finished create_dir_structure
07-03 06:59 DEBUG  TaskList: ## Running uncompress_target_dir...
07-03 06:59 DEBUG  TaskList: ## Finished uncompress_target_dir
07-03 06:59 DEBUG  TaskList: ## Running create_uninstaller...
07-03 06:59 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Ashton\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-03 06:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-03 06:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-03 06:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-03 06:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-03 06:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-03 06:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-03 06:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-03 06:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-03 06:59 DEBUG  TaskList: ## Finished create_uninstaller
07-03 06:59 DEBUG  TaskList: ## Running copy_installation_files...
07-03 06:59 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-03 06:59 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\winboot -> C:\ubuntu\winboot
07-03 06:59 DEBUG  WindowsBackend: Copying C:\Users\Ashton\AppData\Local\Temp\pyl7053.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-03 06:59 DEBUG  TaskList: ## Finished copy_installation_files
07-03 06:59 DEBUG  TaskList: ## Running get_iso...
07-03 06:59 DEBUG  TaskList: New task copy_file
07-03 06:59 DEBUG  TaskList: ### Running copy_file...
07-03 07:01 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-03 07:01 DEBUG  TaskList: # Cancelling tasklist
07-03 07:01 DEBUG  TaskList: New task check_iso
07-03 07:01 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 129, in select_task
  File "\lib\wubi\application.py", line 195, in run_cd_menu
  File "\lib\wubi\application.py", line 119, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
07-03 07:01 DEBUG  CommonBackend: Searching for local ISO
07-03 07:01 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-03 07:01 DEBUG  TaskList: New task get_metalink
07-03 07:01 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-03 07:01 DEBUG  TaskList: # Cancelling tasklist
07-03 07:01 DEBUG  TaskList: # Finished tasklist

```

---

### Post by ashton93 on 2011-07-03
> **bcbc said:**
> That's usually a problem on the Windows part of the install so you need to check the log file to see what is wrong. (It's in the %temp% directory). 
 
Also, it's generally a bad idea to use instructions that are specific to another user and their scenario - unless yours matches exactly (and sometimes it's hard to tell). It's better to create your own thread.
 
Also to let you kno our problem is the same!:(

---

### Post by bcbc on 2011-07-03
> **ashton93 said:**
> Also to let you kno our problem is the same!:(

The original poster had a working wubi but had to reinstall windows. In your case, you were having problems with Wubi... so I think that's quite different. Anyway - I'll continue to help you on the answers.launchpad.net/wubi site.

---

