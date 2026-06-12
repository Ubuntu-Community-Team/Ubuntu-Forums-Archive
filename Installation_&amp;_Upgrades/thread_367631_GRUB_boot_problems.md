---
title: "GRUB boot problems"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by atomicfire on 2007-02-22
Grub loads and just displays "GRUB" in the top left corner...and nothing happens. Does not respond to keyboard, and starts beeping at me if I keep hitting keys.

Hard disk configuration:

(hd0,0) - 120gb IDE hard disk on Channel 1, Master on PCI IDE controller, NTFS data drive
(hd1,0) - 120gb IDE hard disk on Channel 2, Master on PCI IDE controller, NTFS data drive
(hd2,0) - 36gb SCSI u160 drive on PCI SCSI controller - NTFS Boot drive for Windows XP
(hd3,0) - 36gb SCSI u160 drive on PCI SCSI controller, Ubuntu 6.10 boot drive

Normally it boots off of (hd2,0) and goes into windows. I installed 6.10, and i'm guesing it installed the bootloader to (hd2,0) but now just freezes on boot.

I tried to manually reinstall GRUB with the Ubuntu disc:

grub
configfile (hd3,0)/boot/grub/menu.lst
setup (hd2) (hd3,0)
quit

This told me that everythign went smoothly, but I still have the problem :(

-AtomicFire

---

### Post by tgalati4 on 2007-02-22
Here's a reach--perhaps you will have to use a grub floppy, which contains a mini linux operating system that allows grub to run.  Then transfer your menu.lst to the floppy and try it.  The SCSI controller may be messing up the drive assignments.

Grub normally loads its mini kernel from the disk designated as root (hd3,0) in this case.  But since it can't find hd3 (for whatever reason) grub never gets loaded and you are left in limbo.  

At least with a grub floppy you will get a working grub system that you can edit on-the-fly and change boot options in real time.

It's a pain, but you do have system that is outside of a normal disk setup.

Search the forum for grub floppy, there are some good tutorials on how to set it up.

Basically load the floppy to load grub then pick your operating system.
Remove the floppy and your system will boot into Windows by default.
Cheesy but it might get the job done.

---

### Post by sheepshearer on 2007-02-22
check /boot/grub/device.map

not all drives may be where you expect them:

```
# cat /boot/grub/device.map 
(hd0)   /dev/hda
(hd1)   /dev/hdc
```

my first IDE slave /dev/hdb is grub hd2 as a result

---

