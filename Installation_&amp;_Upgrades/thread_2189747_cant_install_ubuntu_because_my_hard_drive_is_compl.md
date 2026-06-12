---
title: "cant install ubuntu because my hard drive is completely full for some reason"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by sharks706 on 2013-11-23
So I have a windows 8 laptop which got infected by a virus and is completely uunable to be operated.  
I want to install ubuntu alongside windows 8, and then run an antivirus on the windows partition
But when i tried installing, the installer crashed, and then i discovered it was because I have no space left on my hard drive
Apparently, sda5, which holds Windows 8, has 949.4 GB on it.  what the heck!!  I only have like 100 mb of free space left.
This is not right because previous to my attempts of installing ubuntu to cure the computre, i had tried everything else.  Which included wiping all my files.  There shouldn't be that much data on the hard drive.  there shouldnt be any data.  what is causing this?  (the virus??)

TL;DR: For absolutely no reason, sda5 has 949.4 GB on it, causing my hard drive to be 99% full, and there isn't enough space to install ubuntu.  Why is this and what do i do? 

(I hope this is the right section)

Thank you

---

### Post by ptrakk on 2013-11-23
run a live version and use the command 'baobab' to help clear up the windows 8 partition. will also tell you what is causing the program. please post updates 'cause a virus that takes up that much space might be something to hear about.

---

### Post by sharks706 on 2013-11-23
thanks!  i got the disk usage analyzer but how do i clear up the partition?  and I scanned both Home and the file system but it seems that nothing is taking up much space.. sorry I'm really confused.  what am i even scanning when i scan home and the file system

---

### Post by Mark Phelps on 2013-11-24
If you have access to another PC,  there are virus vendors that provide free downloadable ISO images -- that you can burn to CD and then boot your infected PC from them to do virus scans.  Kaspersky (among others) offers such a free download.

---

### Post by sharks706 on 2013-11-24
i put kaspersky on a usb, but it wouldnt show up in the boot menu when I tried booting on the infected laptop
However I tested the kaspersky usb on another functioning computer and it worked

I also burned kaspersky to a cd but that didnt show up in the boot menu of the bad laptop either

i think im almost ready to just replace windows with ubuntu

---

### Post by cybergalvez on 2013-11-24
can your laptop boot anything from a USB? you might have to make a change in the bios to make it boot from the USB

---

### Post by sharks706 on 2013-11-24
Yeah it can boot from the ubuntu usb just fine

---

### Post by oldfred on 2013-11-25
Did you leave Windows with fast boot or always on hibernation working. When hibernated gparted or installer will not mount NTFS partition so you can change its size. Always best to fix Windows and shrink it from inside Windows.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

