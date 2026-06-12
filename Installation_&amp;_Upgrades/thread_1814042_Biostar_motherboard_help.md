---
title: "Biostar motherboard help"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by rillwaney on 2011-07-28
Hello all, I am new a brand new member and this is my first post. I just purchased a new setup consisting of the following, Biostar motherboard TH67+, Intel i5 2400, 4Gb Adata mem. I am trying to install 11.04 on this however I it is not going very smooth, things start off looking ok then I am greeted with this

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

I am new to Ubuntu and to Linux all around, was hoping that with this new build out I would be able to put 11.04 on it instead of having to use Windows so I could learn and practice Linux. Any help would be greatly appreciated.

---

### Post by Hakunka-Matata on 2011-07-28
Welcome to Ubuntu and the Forum;

Tell us a bit more:

[LIST]
[*]Are you installing through windows (wubi) or booting the machine into Ubuntu?
[*]what are you using to boot with?  liveCD?, USB?
[*]
[/LIST]

---

### Post by rillwaney on 2011-07-28
Live CD. Forgot to include the system is using an ASUS dvd-rw drive. BIOS boot order is set to the 1. hard drive (WD black 500GB 6gbs) 2. ASUS dvd-rw drive.

---

### Post by Hakunka-Matata on 2011-07-28
I'm a bit confused, if you are attempting to install Ubuntu via a liveCD, then you need to boot the computer into the liveCD.  You know, first boot device = CD drive, with the liveCD inserted.

If you haven't backed up your windows installation, and you don't have recover discs, that would be the very first thing to do.  

You can roll the dice a bit by attempting to boot into the liveCD, and then choosing "Try ubuntu witihout installing to hard disc", that will establish whether or not your 'latest greatest' motherboard is compatible, it's not listed in the Ubuntu Hardware Compatibility List, but that's not to say it won't work.

---

### Post by rillwaney on 2011-07-28
Well thank you for your help on this matter, it looks like I made a bad purchase and this board is not going to allow Ubuntu :( guess I will just end up having to run windows on it.

---

### Post by Hakunka-Matata on 2011-07-28
I wouldn't get discouraged quite so fast, did you find something saying it wouldn't work?  There are lots of reasons you may be having these initial issues, 

Tell us more about how you are trying to install Ubuntu.  What happens when you start up?, how far does the install progress before you run into trouble, 

You may have a bad CD, or a bad downloaded .iso file to start with, A Bios setting that needs to be changed......

Tell us more

---

### Post by ingeva on 2011-07-28
> **rillwaney said:**
> Hello all, I am new a brand new member and this is my first post. I just purchased a new setup consisting of the following, Biostar motherboard TH67+, Intel i5 2400, 4Gb Adata mem. I am trying to install 11.04 on this however I it is not going very smooth, things start off looking ok then I am greeted with this
I believe that you want to keep Windows, at least as a last resort.

First, I think you should use Windows disk mananager to reduce the Windows partition size, and leave the rest of the disk as unused (without partitions).

A hard disk can be divided into four primary partitions, but one (or more?) of them can be defined as extended partitions, which again can be divided into an unknown number of logical partitions. For Linux, you need at least two partition, Linux and Swap. I would recommend a third partition (at least); your home and/or personal storage partition. For this you would probably need at least 10GB of free disk space.

I believe that Ubuntu can be installed in most computers on the market today. What you want to ensure is that you alway have an alternative. So before you start, make sure you have the SuperGrub disk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) so you can always boot whatever system you have on your hard disk.

Don't give up. I really don't believe that you can't run Ubuntu on your computer.

---

### Post by wandalalakers on 2011-07-29
Try using the alternative version.
[http://www.ubuntu.com/start-download](http://www.ubuntu.com/start-download)

---

### Post by Hakunka-Matata on 2011-07-29
You may also be experiencing SATA 6gb/s - SATAII vs. SATAIII interface problems.  

A thread that might help to understand the potential problem:  [http://ubuntuforums.org/showthread.php?t=1513174](http://ubuntuforums.org/showthread.php?t=1513174)

Also, does your machine have a Windows installation installed?, if so which flavor windows?

---

