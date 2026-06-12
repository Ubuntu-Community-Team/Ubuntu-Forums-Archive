---
title: "SATA, Ntfs, resizing during install..."
date: 2006-07-08
forum: Installation &amp; Upgrades
---

### Post by bnastic on 2006-07-08
Hi all,

After hearing all the good things about Ubuntu I decided to give it a try (I'm running several Win and MacOSX boxes at the moment, so Linux had to join the fun sooner or later). 

Unfortunately, istall process refuses to work on my PC in dual-boot mode.

Details:
- Ubuntu 6.06 (LiveCD)
- PC (P4HT, i865) with 2 drives: IDE(80 GB) and SATA (system drive for WinXP, 80GB Maxtor, one NTFS partition, and target drive for Ubuntu).

1. First installation failed as Ubuntu wrongly reported (or I misunderstood) the drives, so Ubuntu ended up resizing the IDE drive. Luckily, no data have been lost in the process. I deleted new partitions on IDE drive (along with Ubuntu on it, I had no option to boot into Ubuntu, as grub was not on mbr for some reason), and went on to install it on SATA (where it should be, along with XP).

2. Second instalation hangs on partitioning. 
Drive model/name, size, partition type... all recognized, but trying to resize it from Ubuntu (to make some 30GB for it) failed with a message "*cannot allocate enough drive space*", or something similar. Tried with different partition sizes with no luck. There is more than enough space on the drive, and drive has no errors on it. 

I searched forums for similar message, but couldn't find anything, only the general confusion about whether Ubuntu can actualy resize NTFS partitions or not. Going on to manualy arranging partitions still won't allow me to resize the partition on SATA drive. 

Anyone seen the similar message, or it's the same problem lots of people seem to have with dual-boot? Is "rescueCD" the only thing to save the day, or I'm missing something?


TIA


--
Some issues that were probably reported elsewhere:

1. USB keyboard/mouse don't work during the initial screen! One always has to wait for 30 seconds and go into LiveCD mode, as no other option is actualy reachable! 
Keyboard starts working after a couple of "loading..." lines pass by. This is very annoying, as USB keyboard works even in BIOS.

2. Something is not quite right with time-zones. Last time I checked London was in GMT zone, but Ubuntu insists on GMT+1! If I force the correct time it manages somehow to even confuse the WinXP afterwards!

3. SATA drive is reported as SCSI(?) on my PC... is this normal?

---

### Post by confused57 on 2006-07-08
Since you haven't gotten a reply yet, thought I'd attempt to help.

You might need to defragment your Windows partition on your SATA drive, if you plan on installing a dualboot on the one drive.

Also, if you want to try installing Ubuntu on the IDE drive and dualbooting, see if this link gives you any options:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you install Ubuntu, with Windows on the SATA drive, be sure to select UTC "no"...Windows is set to local time and UTC "on" will incorrectly set your Windows time.

An excellent dualbooting guide:
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)
or
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by bnastic on 2006-07-09
Thanks, I'll try defragging first.

Interestingly enough, Ubuntu can resize NTFS partition which is not system and on IDE drive, while failing to do so on system partition on SATA.

---

### Post by bnastic on 2006-07-09
Well, writing this from Ubuntu, I'm getting closer but not quite there yet :)

I had to download the Alternate .iso, only that version was able to resize partitions properly! 
I actualy tried using PartitionManager from WinXP, but it couldn't resize the partition either, for the same reason (I guess) LiveCD failed - the primary partition was locked by Windows (something that PartitionManager reported). Alternate version, as it boots from clean, doesn't have that problem.

If I could only figure out why GRUB cannot boot any of the OSes installed... but running Ubuntu CD and selecting "start from the first hard-drive" works fine, although Windows is as good as dead now... endless fun this Ubuntu instalation is... :)

---

### Post by confused57 on 2006-07-09
First we need to see what your partition table(s) are:

```
sudo fdisk -l
```
The -l is a small "L"

and

```
cat /etc/fstab
```

Hopefully, this information will help...did you select to install grub to the mbr during the install process?

---

### Post by bnastic on 2006-07-10
It's all up and running now, editing GRUB files by hand was the only way.
As an advice to people who want to dual-boot it and have more than one drive - read drive names carefully! Or you might end up having grub on both discs and need to boot up Ubuntu from CD (among other crazy things I had to go thru)

The annoying fact is that one encounters THREE different naming conventions for hard-drives! Initial install, GRUB, and "rescue" option from CD all have different names for hard-drives! To make things even more confusing these are just generic names, and have no resemblance with the actual hardware name. You need to look at your BIOS settings and try to figure out which one is the first drive (I got this one wrong...twice, as I have 3 primary IDE drives).


On a side note: USB keyboard still doesn't work whilst in GRUB menu! I have to keep yet another PS2 keyboard just to navigate Grub menu. Once "Loading drivers" phase is reached the USB is back online, but not before that. Any idea how to solve this? USB keyboard works fine in BIOS, though.

---

