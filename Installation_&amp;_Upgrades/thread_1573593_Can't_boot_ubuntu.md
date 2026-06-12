---
title: "Can't boot ubuntu"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by weiloon1234 on 2010-09-12
i has downloaded ubuntu10.04.1-desktop and i run UNetbootin copy the iso into USB .

and i boot from USB,format my C: drive(windows 7) and format C: to ext4 (mount : / ).

i restart my computer when the installation is complete .but get error "Missing operating system"

now my ubuntu is install at C:

maybe is hdd(0,0) #1,how i can boot my ubuntu and set it automatic boot by default??

erm...sry i don't know what is grub and i don't know how to run grub

---

### Post by Bucky Ball on 2010-09-12
Enter the BIOS and make sure you are booting from the hard drive and NOT the USB stick (which shouldn't be in the slot). If you are booting from the hard drive already are you sure you've actually installed Ubuntu?

When you boot is it going to a list with Ubuntu and Windows as selections or is giving the error message instead? If the latter, you either haven't installed or are booting from the absent USB dongle. You should be able to run 10.04 directly from the dongle. Get in there and check on Gparted (Partition Editor) that the hard drive is set up as you're imagining. Are you attempting to install Ubuntu Netbook Remix incidentally? This is best for netbooks.

My method? Install Windows, leave the rest of the drive blank. You could/can add an NTFS data storage partition which both OSs are capable of reading (Ubuntu will read NTFS, FAT; Windows WON'T read EXT4. Install Ubuntu on remaining space. I use 'Manual partitioning' and create a separate /home partition. Good luck.

---

### Post by weiloon1234 on 2010-09-12
i has ejected the usb drive b4 i on the computers

i think i have no windows OS in my computer now, because i has format the C: drive, and i'm sure my ubuntu is installed!

because now i'm booting from my usb drive and i saw a partition call ubuntu(i name it just now) and inside the partition got lots of file like home/ boot/ dev/ etc...

---

### Post by Bucky Ball on 2010-09-13
Yep, sounds like Ubuntu is in there IF you are looking at the hard drive and NOT the directories on the USB stick. If you formatted C drive Windows will not be there. I would start again and follow my instructions above. I am presuming you have no optical drive?

Things are MUCH easier if you install Windows first. It likes to be on the first partition of the first hard drive and if it is not you need to trick it into thinking it is (map the drive). Do-able but why bother when you just want to start using your new OSs???

---

### Post by weiloon1234 on 2010-09-13
i got 2 hdd in my computer
and 1 dvd rom

---

### Post by Bucky Ball on 2010-09-13
Well why are you using a USB stick?

---

### Post by wilee-nilee on 2010-09-13
> **Bucky Ball said:**
> Well why are you using a USB stick? Please press the 'Report Abuse' button on post #5 above you. These types are not welcome.

Been reported, I would have him run the bootscript in my signature, to get the lowdown.

---

