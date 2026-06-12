---
title: "GRUB load error? Please help!"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by TomJ93 on 2010-01-25
I installed Ubuntu 9.10 on a partition of anexternal hard drive. The installer required me to reboot when finished, so I followed the instructions, removing the cd from the drive and pressing enter. I interrupted the reboot at the BIOS menu and changed the settings to boot from the external disk. When I continue, nothing happens. The only thing on the screen is the flashing white cursor, and typing is impossible. I have tried various settings in BIOS regarding boot order, and only one gives any result. When the boot order is set so that the local disk is first, (Normally boots Windows 7) AND the external drive is disconnected, the screen says:
 
GRUB loading.
error: no such disk
grub rescue> (Flashing cursor)
 
With the same settings and the external drive connected, the screen says:
 
GRUB loading.
 
(Flashing cursor)
 
Also, I cannot boot Windows 7 from the local disk. I think this is because the computer is looking for ubuntu on the disk before Windows, even though th local disk is not the location of ubuntu. 
 
During setup, I manually specified the partitions for installation. I used one partition on the external drive for the root dorectory, and one for the share, leaving two free partitions for other uses. I did not specify any partitions on the local disk to be used for anything at all. 
 
Please help, my laptop is currently a paperweight!

---

### Post by panterus on 2010-01-25
i had this trouble at first with my initial install on an external, i had to set the bios to boot from the internal drive first to give the external time to warm up then select ubuntu to boot and it worked fine that way

---

### Post by TomJ93 on 2010-01-25
How long does that take? my external has a built in hardware feature that makes it spin down after 5 minutes of idling. It has done this several times, so I'm assuming it isn't being used at all. Should it be needed again, it can spin up in about 4 seconds. Is this the problem, or do you mean I'd have to wait much longer? 
Also, from what you say, this problem went away after the initial install on the external? If waiting fails, I need access to my original OS again. Is there a way to do that?

---

### Post by Leppie on 2010-01-25
booting off a livecd, try the following:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
this will restore the mbr of your internal drive so when the external drive is not connected it will boot straight into windows.

now install grub to the mbr of your external drive:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sdb
```
this assumes that sdb is your external drive and ubuntu is installed in the first partition on your external drive.
if this is not working, please post the results of the following commands:
```
sudo fdisk -l
sudo blkid
```

---

### Post by altjx on 2010-01-25
i know im probably not helping much, but i had this problem less than 12 hours ago. however, booting from the CD and selecting "boot from hard disk" solved my problem. not sure wtf went wrong or how to even avoid this again

---

### Post by TomJ93 on 2010-01-25
I fixed it! I used a recovery disk and booted from it, and used methods from somewhere on the forum (I forget what I searched for to find it). The point is, it's fixed. Thanks for all the help!

---

