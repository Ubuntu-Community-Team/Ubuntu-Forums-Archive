---
title: "Please Dont Hijack This Thread"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by knudsenjoe on 2008-07-02
Ok, so I got confused on my other thread, and now I'm lost as a cow at a square dance. I'm trying to install HH but I have fouled up what progress I was able to make. So now I just want to erase the whole disk and start over. So...

I 'preciate what advice I've gotten, but I think my best bet now is to totally wipe everything off so I know for sure I have a clean disk.

How can I erase the whole disk, from the very first part to the last. MBR/Grub the whole shebang?

---

### Post by Pumalite on 2008-07-02
DBan:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by tech0007 on 2008-07-02
Download either live or alternate iso. When you get to the partition part, pick 'Guided - entire disk'. That will wipe out everything. Check this link [http://www.howtoforge.org/the-perfect-desktop-kubuntu-8.04-lts](http://www.howtoforge.org/the-perfect-desktop-kubuntu-8.04-lts)

Although it shows kubuntu, steps are basically the same with ubuntu.

---

### Post by knudsenjoe on 2008-07-03
Tried both the above and still no luck. Should I just give up and get a new hard drive? I did try to install windoze just as a test, and the same thing happened. A check of the disk shows no errors.

---

### Post by Pumalite on 2008-07-03
If you can boot a Live CD; post:
sudo fdisk -lu

---

### Post by wpshooter on 2008-07-03
Get [www.killdisk.com](www.killdisk.com) and WIPE that hard drive clean and then make sure that the CD drive is the first bootable device in BIOS.

I would advise installing from the ALTERNATE CD version of Ubuntu.

And make sure that you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

Good luck.

---

### Post by knudsenjoe on 2008-07-03
Ok, so I wiped the disk again and installed Hardy. I have not updated it if that means anything.

sudo fdisk -lu is
Device Boot___Start_______End__________Blocks_________Id______System
/dev/hda1 *___63__________74862899___37431418+___83______Linux
/dev/hda2_____74862900__78156224___164662+______5______Extended
/dev/hda5_____74862963__78156224___1646631______82______Linux swap / Solaris

That * in dev/hda1 is not a typo on my part

'Preciate the help.

---

### Post by SkonesMickLoud on 2008-07-03
That * is the "bootable" flag, and it's supposed to be there.  If it weren't, Ubuntu wouldn't boot, and you'd be left with a blank screen giving you an error.

Updating simply updates out of date packages on your system and fixes bugs.

---

### Post by knudsenjoe on 2008-07-04
oops, spilled my beer

---

### Post by knudsenjoe on 2008-07-04
last bump attempt

---

### Post by Pumalite on 2008-07-04
According to your fdisk -lu, you should be booting Ubuntu. What specifically do you need?.

---

### Post by knudsenjoe on 2008-07-04
'Preciate the help. Normally, I boot Ubuntu without any disc in the drive, and all is good to go. I had a dual boot while I tried Hardy, and I liked it so much I decided to run XP off. In doing so I somehow killed the MBR. Now the only way I can boot is to use Super Grub. I can't figure out how to restore grub back into the MBR (SG says it does, but it don't)

I'm thinking is it a matter of dynamic/logical disk or whatever? Is the MBR fried and I need a new HD? I just can't tell. 

Any help is appreciated.

---

### Post by Pumalite on 2008-07-04
Have you tried reinstalling Grub?:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by knudsenjoe on 2008-07-04
Yeah, I tried that too, and I'm still lost as a cow at a square dance.

---

### Post by Pumalite on 2008-07-04
Where do you encounter the problem?

---

### Post by knudsenjoe on 2008-07-05
When I boot up without supergrub, it gets to a point where there is just the cursor flashing in the upper left, then it attempts to boot a realtek boot, and fails on that. The install cd is good, it works on other drives/systems, but not this particular HD. Grub does just fine except this disk.

Just in case, here's the realtek output...

```

Intel UNDI, PXE-2.1 (build 084)
Copyright (C) 1997-2000 Intel Corporation

For Realtek RTL8139(X)/8130/810X PCI Fast Ethernet Controller v2.16 (041224)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.

```

Obviously that's the ethernet adapter, it doesn't show up when I boot using supergrub, but it does work once I'm into Hardy.

---

