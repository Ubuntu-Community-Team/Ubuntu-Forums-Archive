---
title: "bootable disk.. isn't"
date: 2006-03-28
forum: Installation &amp; Upgrades
---

### Post by danimal on 2006-03-28
Hi,

I have a PC running Windows XP on which I want to put Ubuntu.  I would be fine with a dual boot or strictly Unbuntu.  I have an Ubuntu disk, but it won't automatically boot.  I put in the CD and reboot.  The Autoplay window pops up (so I think it's trying to automagically run it - meaning the bios is set to auto boot from a CD), but then it doesn't do anything.  I tried using the Windows Explorer to manually install Ubuntu, but I don't have any programs that can run the files.  I notice there are 3 files on the "root" of the CD: ubuntu (zero length), readme.diskdefines and md5sum.txt (checksum).  As I look deeper into the CD, there are gzip files (.gz), but my PC doesn't have a gzip reader either.

Any suggestions ?
Thanks,
Danimal

---

### Post by zovres on 2006-03-28
Ok what exactly do you do when you reboot? if the autoplay window pops up this means that you are in windows, there is no link between the autoplay window in windows and the bios. the last thing you want is to be in windows to install Ubuntu. So the CD needs to be launched before windows loads.

---

### Post by linear on 2006-03-28
Did you burn the CD yourself? Make sure you have a valid iso, and that you burned it as an image: [BurningIsoHowto]("https://wiki.ubuntu.com/BurningIsoHowto")

---

### Post by dimava on 2006-03-29
Actually I'm having the same problem, when I restart my computer, it does'nt pick up on the boot sector of the cd.

I burned the CD (Version 5.10) myself, and later used ISOBuster to verify that there is infact a boot sector. I just tried another boot disk (Windows XP Setup) just to see if my setting were correct, and that was able to load just fine. 

I guess I could just extract the bootsector from the windows disk and inject it into this iso.

---

### Post by WoodyMahan on 2006-03-29
I had similar problems when I downloaded the ISO and burned a CD.  The process of copying 600+ MB of data lends itself to issues of the ISO getting corrupted.  I went to the Ship It screen and ordered a pack of 5 CD's.  It took about a month to get them, but when I did, everything worked perfectly.  I would download another ISO and order the CD's to be shipped (it's free, no shipping charges or anything).

---

### Post by danimal on 2006-03-29
The disk I have is an Ubuntu install disk (4.10 Intel x86 Edition), so I didn't burn it.

Maybe my PC isn't setup to autoboot from a CD.  How do I check/change that ?

Thanks,
Dan

---

### Post by WoodyMahan on 2006-03-29
This is in the BIOS.  On Dell when you turn the computer on you can hit F2 and go to a setup screen.  Look for the option to change the Boot Configuration and set the CD-ROM to the top of the priority list.  Then when the machin boots, it will try to boot off of the CD first, then it will move to Floppy, Then to the hard drive.

---

### Post by dimava on 2006-03-29
Actually nevermind mind my post, i tried it once more today and it worked, same iso file, same cd. Weird stuff

---

### Post by mauvegrail on 2006-04-02
Initially I had the same problem. I then checked the BIOS setup for my machine and found that the boot order was Floppy first, Hard disk second and CDrom third.

I changed it to CDrom first, got shot of the Floppy (I don'thave one on the machine) and tried again.


All was ok, and it booted from the CD.


I still don't have UBUNTU working though!!!

Hope this helps.

---

