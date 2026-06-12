---
title: "Dual Boot Partition Problem"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by Roundel on 2008-09-30
Heres the story:

I'm running Hardy Heron and am experimenting with dual booting XP.  I got everything installed and working perfectly, and then decided to add room to my XP(NTFS) partition.  I used GParted from the live disk to remove space from my linux partition (first on the drive) and then add that space to the beginning of my XP partition (I later read you're not supposed to add space to the front of the partition ](*,) oops) .  Now I can start windows from grub and it shows the windows loading bar and progresses to the blue screen with the windows logo where the user names should be.  The user names never show up, but my mouse does.  I have I/O control but no options.

Question:  

Did I brick windows?  I there anything I can try to fix it short of a full reinstall?  I'm afraid any efforts I make to fix it with the XP cd might kill linux.

Thanks!

---

### Post by caljohnsmith on 2008-09-30
Do you have a Windows XP Install CD? If you do, boot from that, press "r" at the first main menu to get the recovery console, and then run:
```
fixboot
chkdsk /r
```
Then boot Windows again, and let me know what happens. It's quite likely you will have to run testdisk in Linux and use that to help repair XP, but first try the above and see how far you get.

---

### Post by Roundel on 2008-09-30
Thank you for the help!

I tried your suggestion but it didn't work - the chkdsk took forever and did report that it found and fixed "errors" but didn't say what they were and the end result when I boot XP is exactly the same blue screen.

What would the next step be (or maybe next steps if there's more than one thing I can try)?

---

### Post by caljohnsmith on 2008-09-30
OK, we can try using "testdisk" on your Windows XP partition to fix the boot sector, so first boot into Ubuntu, enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens.

Also, please post the following:
```
sudo fdisk -l
```

---

### Post by Roundel on 2008-09-30
Thanks for the quick response!

I did all of the above but still no luck.  I'm thinking that since it does boot at least part way into XP and I can see my external HDs, wireless, and mouse and graphics card engage, it must be some problem with the loading process right before it gets to the welcome screen?

---

### Post by legartner on 2008-09-30
Just a suggestion, but if you google "DSRFIX" it should take you to Don Goodall's site. There he explains how to fix your problem.
I've screwed up my Dell computer more than once playing around and the "DSRFIX" has worked everytime for me.

Sorry, I may have assumed you are working on a Dell!

---

### Post by lemming465 on 2008-09-30
The start of an NTFS partition has special contents describing the partition itself, location of the Master File Table, and so on.  If you just tack extra space on at the beginning I"m guessing windows gets very confused trying to interpret whatever gobbledegook is occupying the blocks that it's expecting to be full of NTFS metadata.

A possible recovery: edit the partition table again and strip off the extra space.  If you can get it back to exactly where it used to start, it may be OK after a chkdsk.  You may be able to move it using a commercial tool such as partition magic; the GNU tools can resize NTFS but I don't think they can move it.

Otherwise you are looking a complete reinstall of XP, sorry.

---

### Post by meierfra. on 2008-10-04
I tried out your scenario (add space to the beginning of the XP partition) and run into the exact some problem as you. After three days days of fruitless attempts, I'm finally able to boot into XP again.  Moving the beginning of the the partition causes XP to reassign the drive letter. If the newly assigned drive letter is different from  the original drive letter, XP  cannot boot. 

I used "regedit"  to change the drive letter back to the original. If you haven't solved your  problem yet, let me know and I can give you detailed instruction.


Are you able to mount XP from Ubuntu ? (I was able to,  so I knew the whole time that my  XP partition was not seriously damaged)

---

### Post by caljohnsmith on 2008-10-04
Meierfra, so if you use gparted to expand the beginning of a Windows XP partition, is gparted savvy enough to move the Windows XP (starting at the boot sector) to the beginning of that new space, or does gparted just put a whole bunch of free space at the beginning of the XP partition? Sounds like it is the former but I just want to confirm. 

Also, do you mind posting your method of getting it to work successfully? Instead of posting it here, I'm thinking it would definitely be worth creating a "HowTo" thread with your method, especially the details of which registry entries you have to change the drive letter. It would be great to have your method documented so everyone in the future can benefit. :)

---

### Post by meierfra. on 2008-10-04
> so if you use gparted to expand the beginning of a Windows XP partition, is gparted savvy enough to move the Windows XP (starting at the boot sector) to the beginning of that new space
Yes. Although in my case gparted computed the length of the filesystem wrong. But  testdisk's "rebuild BS" fixed that problem.

> creating a "HowTo" thread with your method, 

I might, but I   would like  to solve Roundel's  problem  before I dare to post a general howto.

Goodells' [webpage]("http://www.goodells.net/multiboot/partsigs.htm") contains lots of information on the drive letter problem.

---

