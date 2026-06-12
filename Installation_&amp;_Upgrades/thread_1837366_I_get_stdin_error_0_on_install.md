---
title: "I get stdin error 0 on install"
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by Doggerdoo on 2011-09-01
I have tried many times to install ubuntu, i chose F6 and deleted "Quiet" & "Splash". At the end it either hangs at stdin error 0 or switching to colour fram buffer device 160x64

:confused: :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by mörgæs on 2011-09-02
Which version of Ubuntu and which hardware are you using?

---

### Post by Doggerdoo on 2011-09-02
I am trying to install ubuntu 10.04.3 LTS LiveCD, i have a Intel Pentium 4 1.60 GHz CPU. 1 GB RAM and a removable Samsung CD/DVD Drive.

---

### Post by mörgæs on 2011-09-02
Have you tried the alternate ISO?

---

### Post by Doggerdoo on 2011-09-04
> **mörgæs said:**
> Have you tried the alternate ISO?

yes, and it works but no grub and blinking cursor on everyboot then black screen.

---

### Post by mörgæs on 2011-09-04
It sounds like you need to add boot options. There are some links here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

It would also be a good test to try a newer Ubuntu for comparison.

---

### Post by shawnat88 on 2012-01-03
I was getting "stdin error 0" also. It would take a long time before I could try or install ubuntu from the live usb. My problem turned out to be related to the hard drive; most likely because a previous installation of 11.10 was interrupted. I was finally able to fix it using parted magic and the following steps:

1.) Download Parted Magic and create a live cd/usb from it (link below)
2.) Boot into Parted Magic (From RAM)
2.) Go to: System tools > Erase Disk
3.) Erase the disk (write zeros)
3.) Open Gparted and format drive as ntfs
4.) Restart and install Linux 

Parted Magic can be found Here: 
[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

Backup any files before doing this(obviously). I tried a bunch of other stuff before this, like running badblocks and reformatting the disk numerous times, but none of that stuff did the trick.Not sure how this worked out, but it did.

Very late, but hope this helps.

---

