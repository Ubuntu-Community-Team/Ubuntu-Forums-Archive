---
title: "boot issue (problem)"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by anafshalom on 2013-05-03
Background:
I've recently installed Ubuntu 12.10 on a Toshiba laptop 64-bit machine which has been running Windows Vista for about 5 years.  It worked fine.  I installed on an aditional partition as well.  I attempted to change the appearance of the GRUB menu so that I could easily identify the two versions and so that it would automatically boot the last system used--I also gave the menu a background picture and changed the fount.  i made these changes with *Grub Customizer 3.04 *.  somehow I messed things up and the computer would not boot at all.  I booted to live CD and fixed things up, so now it boots and the GRUB menu looks fine. But:

I do not get the initial BOIS screen when I reboot which also has options like F2 for setup, etc

I would like to get the screen, though I know it's not critical

Thank you,  Reuven

---

### Post by fantab on 2013-05-04
Are you booting only Ubuntu or are you dual booting Windows and Ubuntu? If dual booting, are able to select and boot Windows?
What do you mean, when you say, " I installed on an additional partition as well"? Do you have two copies of Ubuntu?

---

### Post by anafshalom on 2013-05-04
I have Ububtu installed on two diferent partitions, and also have Windows Vista.
Here is  gparted screen dumo
[ATTACH=CONFIG]242170[/ATTACH]

---

### Post by anafshalom on 2013-05-04
And yes i can boot to Windows.

---

### Post by grahammechanical on 2013-05-04
The BIOS flash screen appears before the Grub menu. It is independent of anything you have done to fix Grub. My BIOS setup has an option to disable the BIOS flash screen (Full Screen Logo). Could it be that at some point you have disabled the BIOS screen? And now you need to enter the BIOS setup to re-enable it.

I have also noticed that I do not always get the BIOS screen. 

Regards.

---

### Post by anafshalom on 2013-05-04
Fixing GRUB does not change it, but di messing up grub causing the computer to give ma a totally blank screen when booting break it?

---

