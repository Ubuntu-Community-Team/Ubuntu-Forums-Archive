---
title: "Changing from Dual Boot"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by GreenandBluification on 2011-01-31
I've recently installed Ubuntu 10.10 Maverick Meerkat as a secondary OS and updating it messed up Windows 7's boot sector. I was just wondering if there's a way for me to get rid of Windows 7 and give Ubuntu my full HDD without reinstalling.

---

### Post by tommcd on 2011-01-31
> **GreenandBluification said:**
> I've recently installed Ubuntu 10.10 Maverick Meerkat as a secondary OS and updating it messed up Windows 7's boot sector.
This should not happen. If you were able to boot Windows7 after you first installed Ubuntu then you should still be able to boot Windows7 after any updates. Does the grub2 menu still give you an option for booting Windows7 when you boot the computer? If not, then try opening a terminal and running:
```
sudo update-grub
```
Then reboot and see if you can boot Windows7.
> **GreenandBluification said:**
> 
I was just wondering if there's a way for me to get rid of Windows 7 and give Ubuntu my full HDD without reinstalling.
You have several options for what you want to do with the hard drive space that is currently occupied by Windows7.
You could simply boot from the Ubuntu live CD and use Gparted to reformat the Windows partition to an ext4 partition. Or use the live CD to delete the Windows partition and grow your Ubuntu root or home partition into the newly created free space.
You could also use a *Parted Magic* live CD for this:[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)
From your Ubuntu install post the output of:
```
sudo fdisk -l
```
This will tell us what partitions you have. This will determine what options you have if you wish to change the size of your linux partitions to incorporate the space that is currently used by the Windows7 partition. 
Otherwise you could just format your Windows partition into a linux partition. Then create a mount point for it and add it to your */etc/fstab* file so it mounts when you boot your system.

Write back if you need more help.

---

### Post by kansasnoob on 2011-01-31
> **GreenandBluification said:**
> I've recently installed Ubuntu 10.10 Maverick Meerkat as a secondary OS and updating it messed up Windows 7's boot sector. I was just wondering if there's a way for me to get rid of Windows 7 and give Ubuntu my full HDD without reinstalling.

Was this a Wubi install?

In order to troubleshoot your problem we should see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

