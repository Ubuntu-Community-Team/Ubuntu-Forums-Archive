---
title: "Adding another Linux distro to GRUB"
date: 2005-02-09
forum: Installation &amp; Upgrades
---

### Post by timelord726 on 2005-02-09
Hey everyone.

When I installed Ubuntu, GRUB only recognized Windows XP as my only other operating system.  This wasn't really the case -- I was also running Fedora Core 3.  At the time, though, I really didn't care that much.  I still don't particularly miss it, but I would like to boot back into it once or twice if only to copy some stuff off of it to get into my Ubuntu installation.  (Coincidentally Ubuntu refuses to recognize/mount my standard ext3 Fedora partitions.)

Any help would be appreciated, either with adding Fedora Core 3 to my GRUB boot menu or with mounting the drives in Ubuntu!

---

### Post by Wolven on 2005-02-09
To boot another Linux distro you need to add something like this in your **/boot/grub/menu.lst**:
```

title     Fedora Core 3
root      (hdX,X)
kernel    name_of_the_fedora_kernel root=/dev/hdXX

```
To GRUB the HDD and partitions are read like this: hda1 = (hd0,0) | hda2 = (hd0,1) | hdb1 = (hd1,0) | hdb2 = (hd1,1) and so on under the **root** entry.
Under the **kernel** entry the HDD and partitions are read "normal"   root=/dev/hdb3 or where ever your FC3 / dir is.
Take a look at the examples in the menu.lst

This quote is from the Gentoo handbook:
> 
**Understanding GRUB's terminology**

The most critical part of understanding GRUB is getting comfortable with how GRUB refers to hard drives and partitions. Your Linux partition /dev/hda1 will most likely be called (hd0,0) under GRUB. Notice the parenthesis around the hd0,0 - they are required.

Hard drives count from zero rather than "a" and partitions start at zero rather than one. Be aware too that with the hd devices, only hard drives are counted, not atapi-ide devices such as cdrom players and burners. Also, the same construct is used with scsi drives. (Normally they get higher numbers than ide drives except when the bios is configured to boot from scsi devices.) When you ask the BIOS to boot from a different hard disk (for instance your primary slave), that harddisk is seen as hd0. 

-----

To automaticly mount extra HDDs and/or partitions under Ubuntu you need to add it/them to your **/etc/fstab**. Here is mine:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>       <dump>  <pass>
proc            /proc           proc            defaults        0       0
/dev/hda3       /               reiserfs        defaults        0       1
/dev/hda1       /boot           ext3            defaults        0       2
/dev/hda4       /home           reiserfs        defaults        0       2
/dev/hda2       none            swap            sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660     ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto            rw,user,noauto  0       0
## The lines below has been manually added by me
/dev/hdb1       /mnt/hdb        reiserfs        defaults        0       0
/dev/hdd1       /mnt/hdd        reiserfs        defaults        0       0

```

Hope that wasn't too cryptic.  :-)

---

