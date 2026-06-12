---
title: "Dual Boot Ubuntu 14.04.3 Can Corrupt NTSF File System"
date: 2015-09-28
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-09-28
Hello,

I just finished building a Windows 10 & Ubuntu 14.04.3 dual boot system. This has been my second attempt. I damaged the NTFS partition, when I tried to access it from the Ubuntu partition. This has been no problem for Windows 7; in fact I have been able to push and pull files from the NTFS partition. This has been an unexpected but useful feature. I would strongly advise against doing this with Windows 10, even though the file system is still NTFS. When I tried it on my previous build, I received an error message; but was able to read the NTFS partition. I also tried to relabel the NTFS partition to Windows 10 with GParted. The end result of these actions was to corrupt the NTFS file system and lock the partition. I then tried chkdsk /f to try to fix the NTFS file system; but this caused further damage and made Windows 10 completely unresponsive upon loading completely. I then had to erase both partitions and start over. I'm finally finished; but my what a heck of a time it was.

Does anyone have any alternative solutions for relabeling the NTFS partition; so I don't have to just read the drive name in Ubuntu? Also, if anyone knows a little more about reading the NTFS partition with Windows 10 from Ubuntu, this would be a great help!

Thanks, Hannibal

---

### Post by sudodus on 2015-09-28
I can't say exactly what caused your problems, but I have read advice years ago, to avoid writing to the Windows system partition from linux. ***A separate data partition with the NTFS file system is recommended for common data*** (or exchange of data) between linux and Windows.

One problem could be hibernation or the 'half-hibernation' that is called fast boot. Such methods assume that no other system writes or changes in the file system. Another problem could be the incomplete tools for NTFS in linux.

-o-

You can change the label in Windows (with Explorer or the Windows command line 'cmd'). This will be seen by linux.

---

### Post by Bucky Ball on 2015-09-28
> **sudodus said:**
> ... avoid writing to the Windows system partition from linux. ***A separate data partition with the NTFS file system is recommended for common data*** (or exchange of data) between linux and Windows.

^^^
This. Not a good idea to access the partition any version of Windows is installed on, particularly if you change the file in Ubuntu then save it back to the Win partition. 

The shared partition is the rule of thumb and regular way of going about this.

---

### Post by oldfred on 2015-09-28
While you still need fast start up off, you can set NTFS system partition to read only.
 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

And if writing into a NTFS data partition you need to include windows_names parameter as NTFS does not support some file name chars that Linux does.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
      
 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by coljohnhannibalsmith on 2015-09-28
> **sudodus said:**
> ***A separate data partition with the NTFS file system is recommended for common data***

Sounds like an excellent idea! How do I do this, when installing Windows?

Thanks, Hannibal

---

### Post by Mark Phelps on 2015-09-28
You need to understand that, like its predecessor Win8, Win10 automatically enables a new hibernation method known as Fast Startup.  With this enabled, ALL windows filesystems (that's ALL, not just the OS partition) remain mounted, even after Win10 is shut down.  That will prevent mounting a shared NTFS data partition in Linux.  And, if you Force it to mount, that will result in data corruption in that partition.

There are two ways to disable FastStartup; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.

---

### Post by sudodus on 2015-09-29
> **coljohnhannibalsmith said:**
> Sounds like an excellent idea! How do I do this, when installing Windows?

Thanks, Hannibal

That is the easiest option :-)

Afterwards, you can shrink the Windows partition (and leave drive space unallocated). Do this while running Windows.

After reboot into a live linux session (for example from an Ubuntu USB pendrive), you run ***gparted*** and create partitions:

an ext4 partition to become root partition for Ubuntu
an NTFS partition with the label data
a swap partition for Ubuntu

And remember to turn off fast startup according to the excellent description by *Mark Phelps*.

---

### Post by coljohnhannibalsmith on 2015-09-29
Sounds like excellent advice gentlemen. I will give it a try.

Thanks, Hannibal

---

