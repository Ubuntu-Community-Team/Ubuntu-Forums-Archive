---
title: "dual boot install w/ XP - install does not seem to recognize grub"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by bakedup on 2007-05-13
Setup - quad core Intel EMT64, 4GB ram, nVidia motherboard and graphics, XP Professional, 2 disks, one 250GB "system disk" (three partitions, one for XP32 (ntfs), three for Linux64 (ex, the other idle) the other 500G for data (ntfs).  Boot partition is (hd0).  Using 10GB for / and 1GB for swap on manual partition setup.  The system partition plus one more partition are formatted as ext3.  The partition where XP lives is formatted as ntsf.

I installed both the Ubuntu and Kubuntu 7.06 distributions onto the partition reserved for linux on the primary system disk.  Upon completion of the install, the system does not come up with a GRUB screen but rather boots directly to XP.  When running the install again, the partition setup that was previously done has not persisted.

I would like to either set it up as dual boot from MBR or boot Linux from a CD (sourcing the installed linux OS on the disk).

Any ideas why I am not seeing the GRUB screen when I boot up?

---

### Post by bulldog on 2007-05-13
You need to find out which hdd is (hd0) because GRUB is installed on this hdd by default [can be changed]
If you have Sata and IDE hdd's most probably GRUB is on the IDE hdd.
Try to boot from the other hdd and look around if GRUB persists there.

In most case it's recommended to install ubuntu on the first boot device and install GRUB there as well.
Windows on the second hdd and remap your windows entry in the menu.lst.
In that case you can boot both from GRUB,but in case of trouble you can boot windows from it's own boot
loader by changing the boot device in your BIOS.
Sample of how to edit your windows entry in menu.lst,
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	(hd1,0)+1

```

---

### Post by bakedup on 2007-05-13
both disks are SATA.  I will poke around later however.  Thanks for the advice.

Is there a way to boot from a CD and source the install on the linux partition?  Or does it have to go through the boot loader on disk?  I remember my first linux dual boot install worked that way except it was a floppy then.

---

### Post by bulldog on 2007-05-13
Use the live cd and choose the option 'boot from hard disk' or something like that,it should be in the first menu.

---

