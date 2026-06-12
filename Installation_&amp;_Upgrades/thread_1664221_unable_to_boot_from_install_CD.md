---
title: "unable to boot from install CD"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by inkameep on 2011-01-10
I'm trying to do a clean install of Ubuntu 10.10 on a desktop computer currently running Windows 7. But when I try to boot from the Ubuntu 10.10 installation CD, I can't even get to the screen where you select "Try" or "Install." All I get is the ubuntu logo with the dots lighting up underneath. The CD/DVD drive thrashes around for 10 or 15 minutes. Then the dots stop lighting up and everything grinds to a halt. I pop out the CD and the system boots into Windows 7.
 
I've burned several CDs, thinking it might be a bad CD, but that doesn't seem to be the case.

---

### Post by wilee-nilee on 2011-01-10
Try holding down the shift key when you power on you will get a earlier menu with the same and more options. 

If you intend to install Ubuntu as a dual boot make sure you don't already have 4 primary partitions, that is the limit on one HD. Also use the windows 7 disk manager to resize its partitions, and don't choose the install alongside. You will want to build the partitions and use a custom install to be safe. Build the partitions with gparted in Ubuntu with a extended partition first the ext4 partition and the swap inside.

---

### Post by jonbonjovi on 2011-01-10
Try press "esc" as soon as Ubuntu CD starts, you should see the command line output and maybe figure out what goes wrong.

---

### Post by wilee-nilee on 2011-01-10
> **jonbonjovi said:**
> Try press "esc" as soon as Ubuntu CD starts, you should see the command line output and maybe figure out what goes wrong.

In Maverick it is shift, the esc was before Lucid I believe.

---

### Post by wjz on 2011-01-10
I downloaded the 693iso of ubuntu 10.10 and burned it several times to a 700mb disposable cd. I went through 8 cd's with the same problem. The dvd drive would make a whining noise as if it couldn't find the start. And 1 of the discs would go as far as the ubuntu logo with the dots and no further. Try using a dvd disc with more storage, In my case imgburn, infrarecorder and the ubuntu burner were having issues closing the cd.

---

### Post by inkameep on 2011-01-10
I held down the shift key while booting and sure enough I got a menu. 
 
When I selected "test disc for errors," the system found no defects.
 
When I selected "test memory," I got the following:
 
EDD: Error 8000 reading sector 10084
Invalid or corrupt kernel image.
boot:
EDD: Error 8000 reading sector 2084
 
At this point the system froze.
 
When I tried to reboot, the system would not start from the CD at all. There was activity on the CD/DVD drive for about 30 seconds. Holding down the "shift" key did nothing. Then the system seemed to give up on the CD and it booted Win7 from the HDD. I tried this 3 times.
 
Then I burned an installation disk for ubuntu 10.04.1 and tried to boot off that. Same result (x3).
 
So now I have a system that installs Win7 easily in 15 minutes but will not get to first base with either ubuntu 10.10 or ubuntu 10.04.1.

---

### Post by wilee-nilee on 2011-01-10
How fast was the cd burned at?

If the computer will boot a thumb try unetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You might also check the ISO's MD5SUM.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by inkameep on 2011-01-10
It was burned on a 24x Sony DVDRW drive. I don't know how to control the burn speed, but the burn was verified and the ubuntu installer seemed to give it a clean bill of health. But I will try your suggestions.

---

### Post by wilee-nilee on 2011-01-10
> **inkameep said:**
> It was burned on a 24x Sony DVDRW drive. I don't know how to control the burn speed, but the burn was verified and the ubuntu installer seemed to give it a clean bill of health. But I will try your suggestions.

Thats pretty fast if that is what it is burning at, yeah try the thumb.

---

### Post by inkameep on 2011-01-12
The problem turned out to be a defective CD/DVD drive. (The install CDs themselves were good because I burned them on a different computer.) I began to suspect the CD/DVD drive might be bad because it occasionally seemed to be thrashing and struggling while reading. Once I replaced the CD/DVD drive, the system was able to boot ubuntu 10.10 from the CD. Thanks to everyone for their assistance.

---

### Post by manee1982 on 2012-06-23
thank you very much Mr/ [inkameep]("http://ubuntuforums.org/member.php?u=1215775") and you guys for opening this topic,  your posts helpful.

really i am getting tired thinking about what was my problem. i try to install ubuntu over and over from my old cd-rom, and i didn't discovered where
is a problem antil i read this posts.

 really thanks again
 

Manee.O.H

---

