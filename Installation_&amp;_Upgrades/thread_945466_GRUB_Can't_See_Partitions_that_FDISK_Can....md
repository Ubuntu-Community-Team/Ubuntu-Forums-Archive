---
title: "GRUB Can't See Partitions that FDISK Can..."
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by jecottrell on 2008-10-12
I've been working on setting up a system with a bunch of hard disks. My latest attempt at an install is working but when I:

```
GRUB> root (hd0,0)
```

I get a no such partition error. Same thing if I use geometry to see what hd0 looks like to GRUB.

However, if I FDISK -l all the partitions get listed and everything looks normal.

For the record, I'm trying to RAID1 hd0 and hd1 following an online how-to.

Here's the history of what I've done so far:

Six IDE hard drives. One on each MOBO controller. Two IDE PCI expansion cards w/ one hd on each controller on each card.

Original install had a problem with the menu.lst and device.map files not agreeing. I edited them and the system would then boot normally.

An FDISK -l looked good but, there was no "boot asterisk" by sda1. I figured out how to mark it as a boot in FDISK and did that and now it shows the asterisk by sda1.

BTW, MOBO drives show up as sd not hd, that is where the original  booting problems started. (Yes, they are on IDE controllers not SCSI.)



So, the question is.... where does GRUB get its partition information? And why can't it see the partitions that FDISK can? And how do I fix it?


Thanks,

John

---

### Post by caljohnsmith on 2008-10-12
When you boot Grub on start up, it has to use BIOS to access your drives, so it is more limited than when you access your drives through the kernel in Ubuntu with the "fdisk" command. If you want to know how Grub "sees" your drives on start up, press "c" when you get the Grub menu, and then type the following without hitting return:
```
grub> geometry (hd
```
Then hit TAB for tab-completion, and it should show all your drives starting with (hd0). My guess might be that Grub sees your drives as separate instead of in a RAID configuration. To see the partitions and drive size of a particular drive, do:
```
grub> geometry (hdX)
```
Where (hdX) is (hd0), (hd1), etc. Anyway, that probably won't solve your problem, but it should give you some valuable clues as to how Grub sees your drives. :)

---

### Post by jecottrell on 2008-10-12
I had done that. It sees the drives, but not the partitions. It's got to get the partition info from somewhere.

I've given up on the RAID of the system disk. I'll have to find some other way to back up the system....

---

### Post by upchucky on 2008-10-12
get supergrub advanced, and if u can,  get knoppix too it has two great partitioning programs that will find the info u need to fix the drives.

they both are indespensable for fixing partitions and master boot records.

grub stage 1 at the bios level passes drive geometry on to the grub menu.lst file for booting. if the geometry is not setup in grub it will hang with a busybox cursor waiting for u to tell it what to do.

supergrub advanced  and knoppix will give u the parameters that u need to edit into the grub menu.lst file so it can see the partitions

knoppix will let u partition and verify the partitions, plus u can also edit the files on an unbootable system whether it is linux or windows.

many times supergrub will magically fix it in one shot, but if it does not then post the drive geometry when u find it and it will be easier to help u.

---

