---
title: "Partition system cannot resize Windows XP system"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by Chiyiros on 2007-09-20
Similar threads showed nothing that seemed relevant, so I'm posting this in the hopes for a bit more help.

Problem Outline:

When attempting to have Ubuntu's installer (Live CD) resize the Windows XP partition (currently the only partition aside from what I believe is the swap partition), I get the following error message at 0% Resizing:

"An error occured while writing the changes to the storage devices.

The resize operation was aborted."

An observation that may be of assistance: The first time I started the Ubuntu install from the Live CD, it did not present the automatic resizing option of the partition, instead only offering a full reformat or the manual option. I looked online to try and get the commands needed to reformat the drive (returning to Windows to do so), and returned with a general concept - only to find that the first option of an automatic resize was available. However, attempting the resize with the automatic system or the manual system's edit setup did not work - I did not try using the command line setup, fearing that attempting to brute force this wouldn't be my wisest of moves.

Notes:

I'd rather not delete Windows XP yet (I want visual confirmation that some of my old/obscure/oddball programs will work before I commit to removing it), so formatting the drive before installing Ubuntu is to be avoided if at all possible.

System Specs:

Toshiba A105-S4164
OS: Windows XP Media Center Edition (argh)
Core Solo 1.86 GHz
1 GB RAM (DDR2 SDRAM)
80 GB hard drive
Intel GMA 950

---

### Post by meindian523 on 2007-09-20
Please post ```
fdisk -l
```(small L) from Live CD.....

---

### Post by psusi on 2007-09-20
Run a chkdsk /f from windows, then reboot and let it fix the filesystem.

---

### Post by Diavo on 2007-09-20
I'm having a similar problem as Chiyiros (without his "observation" part).  I go to resize WinXP's NTFS partition (the only partition on my HDD) during the Ubuntu Fiesty install and it returns the error that it cannot write the changes to the disk. =(
I tried running GParted from the Live CD, same error. =(
I downloaded a System Restore ISO (linux based), burned it and booted from it and ran GParted from it and again, same error. =(

But I'll try what's suggested ^above^ and report back in a day or so, thanks!

It's a shame because running Ubuntu from the Live CD, everything [hardware-wise] was recognized & works, even my Wacom tablet. =)    And even from the CD Ubuntu runs and executes things faster than XP.  And I'm SO ready to join the Linux world, but I'm not ready to do away with Windows *just* yet...

Just FYI:
Toshiba Satellite (forget which model, but almost 3 years old)
Celeron M, 1.5 Ghz
1.5 Gb RAM (upgraded from the stock 256Mb)
60 Gb HDD
WinXP Home
+250 Gb external HDD (Fat32), for backups and extra space

--Diavo

---

### Post by logos34 on 2007-09-20
try temporarily disabling hibernation and the virtual memory/paging files in windows.  Then defrag several times.

[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by Diavo on 2007-09-20
Great link, thanks.   (Quick reply too!)
=)

---

### Post by Chiyiros on 2007-09-20
As for my problem, I'm afraid it's been rendered quite irrelevant; after going to load Windows up and check on answers this morning, I found that it doesn't load, period. (Doesn't even get to the standard Windows logo screen...)

So. Here I go with full-out Linux, then, since I don't even have a Windows back-up CD with me (It's four thousand miles away back in Michigan, I'm in Beijing. Yeah.)

So I suppose this can be considered solved?

---

### Post by Diavo on 2007-09-21
Hey, my problem was solved following the "Moving the Unmovable" tutorial on unchecking the Hibernate option in WinXP and setting the swap/paging file to zero, then degragging.  Ubuntu installed without a hitch after that! =)

---

### Post by Skidpad on 2007-09-21
> **Diavo said:**
> Hey, my problem was solved following the "Moving the Unmovable" tutorial on unchecking the Hibernate option in WinXP and setting the swap/paging file to zero, then degragging.  Ubuntu installed without a hitch after that! =)
I had the same problem when I installed 6.10 last Jan, and solved it the same way (with wonderful help here of course!).  I believe this type of laptop installation problem is more common than most people realize - hence the link in my sig.

Glad you got it going, and welcome aboard!

---

### Post by Diavo on 2007-09-25
> **Skidpad said:**
> Glad you got it going, and welcome aboard!
Thanks!  I'm starting to play around with it and plan to really get into it... over time of course. =)

---

