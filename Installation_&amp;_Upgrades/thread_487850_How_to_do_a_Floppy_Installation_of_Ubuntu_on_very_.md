---
title: "How to do a Floppy Installation of Ubuntu on very old Notebook With Boot Limitations?"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by guyver on 2007-06-29
Okay, my GF has a very old notebook with a broken integrated CD drive and no ability to do a boot from a USB storage device.  I have two options I'd like to pursue.  First option is floppy boot towards a network installation.  Second option is a floppy boot towards using an external CD drive installation.

Is there some place I can obtain a floppy disk image in order to download and install Ubuntu?  Her notebook is partitioned in half.  One half is WinXP and the other half is Win 2K.  I intend to wipe both partitions and make this a dedicated linux notebook.  

How can I go about this?

---

### Post by guyver on 2007-06-29
I forgot to mention, I am a total rookie in the Linux world so any spoon feeding would be greatly appreciated.

---

### Post by ugm6hr on 2007-06-29
This might be helpful:
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by guyver on 2007-06-29
I want to say I tried this before without much success... it looks familiar, but it has been a while.  I will try again.  I was thinking Debian may be a better choice for her since Ubuntu makes no boot floppies of their own which I think would fix this problem very easily.

My problem is that I am pretty much a windows guy, trying to make the shift to Linux, but some of the solutions can at times not be easy to a novice like myself.  I'll try again tonight.

---

### Post by lluisanunez on 2007-06-29
You may try Wubi-installer. It installs Ubuntu from Windows, running as an .exe, no need of a CD drive 
[http://wubi-installer.org/]("http://wubi-installer.org/")

There is also a Debian version: [debian.exe]("http://goodbye-microsoft.com/") (300Kb)

---

### Post by ugm6hr on 2007-06-29
> **guyver said:**
> I want to say I tried this before without much success... it looks familiar, but it has been a while.  I will try again.  I was thinking Debian may be a better choice for her since Ubuntu makes no boot floppies of their own which I think would fix this problem very easily.

My problem is that I am pretty much a windows guy, trying to make the shift to Linux, but some of the solutions can at times not be easy to a novice like myself.  I'll try again tonight.

It is possible to install Ubuntu from a USB device too.  It is pretty easy to get the Ubuntu mini.iso onto a 64MB USB flash (or the whole Ubuntu onto 1GB) using the method here:
[http://ubuntuforums.org/showthread.php?t=453922](http://ubuntuforums.org/showthread.php?t=453922)

Of course, my previous link to Smart Boot Manager would have to give a USB boot option....

---

### Post by logos34 on 2007-06-29
Since windows is installed on this thing, my candidate for the easiest ubuntu install is to do it straight from the hard disk--no floppy or cd required.  Starts up a network install. Wipe the NT half and install root and swap there.  Afterwards format xp partition as ext3 /home.

'Windows NT/2000/XP (using Grub)'
[COLOR="Blue"]https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%29[/COLOR]

---

