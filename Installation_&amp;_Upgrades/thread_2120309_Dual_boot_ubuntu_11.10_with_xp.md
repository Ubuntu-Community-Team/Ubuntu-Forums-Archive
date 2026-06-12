---
title: "Dual boot ubuntu 11.10 with xp"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by SR_ELPIRATA on 2013-02-26
Hello all:

I had a working ubuntu 10.10 drive, but needed to install xp and thought about also putting the new ubuntu on it and dual boot. So, I normally what do is prepare a drive (take data out that is) and then install xp and next install ubuntu.

Problem Im having is that when I try to either do the install (from a flash drive) or do the try and install from desktop shortcut, I get to a point in which is asking me where to put the bootloader, and on the box, the upper section shows nothing, and the bottom section shows the a pulldown menu with only /dev/sda as option (which is the only drive of course).

First time I tried, I had the windows partition and another NTFS partition. I wiped that one, and made the second partition to be ext4 (with / as label) for ubuntu and a 2gb partition for swap (as I usually had done many times before). But it keeps giving me this error, is not able to install the bootloader and I cant figure out why.

Any ideas?

ELP

---

### Post by TheFu on 2013-02-26
GPT or MBR disk partitioning?  XP doesn't support GPT partitions.
Is the HDD over 2TB in size?

If the machine is too new, XP might have hardware compatibility issues.  Did it have XP on it previously?

After getting XP installed - it must be on a primary partition, you can run Boot-Repair to find all the Windows and Linux boot partitions, then setup a boot menu in the MBR.

Lacking all of this, if the machine has a Core2Duo or better CPU and 2GB of RAM or more, you could load up a virtual machine and load XP inside there. That way you could run both OSes at the same time and overcome any XP hardware issues, since the actual hardware will never be seen by any VM.  OTOH, if that P4 is what you ahve - forget running any VMs.

---

### Post by SR_ELPIRATA on 2013-02-27
Well, at least when I did the ext4 was with gparted, but the windows was done with the xp installer, and I did this way before doing the ext4.

No, is a 250GB drive. Its a rather old computer, P4 with DDR. It was 'designed for xp'. XP is on a primary partition (C drive using 60gigs), then I was using all the rest for ext4 and at the very end a extended part with 2gigs and set as linux swap (logical drive).

What it baffles me is that I've done it before like this, and has worked. Do the initial partition for windows from within xp installer, then with gparted I made the next ext4 and swap.

I've done virtualbox before and works great, but is not for games, hence the need to dualboot.

It could be that when I did the partition for windows I had done with gparted, so I'm going to delete the ex4 partition and move data back, so I can use the other 250gig drive to retry all this. I guess I could use fdisk to make the initial 60gig partition and then just ghost/copy this partition to that one and see if ubuntu install works from there.

THANKS for the suggestions!

---

### Post by dino99 on 2013-02-27
from the livecd/liveusb, open a terminal and run:

```
sudo grub-install /dev/sda
```
```
sudo update-grub
```

---

### Post by SR_ELPIRATA on 2013-02-27
That would be before actually executing the install on the livecd/liveusb?

---

### Post by oldfred on 2013-02-27
Gparted often does not show partitions on drives that were gpt before, that were RAID before or were dynamic partitions before. Each requires meta data to be removed from drive.

Also if Windows is hibernated or NTFS needs chkdsk gparted will not mount NTFS partition.

---

