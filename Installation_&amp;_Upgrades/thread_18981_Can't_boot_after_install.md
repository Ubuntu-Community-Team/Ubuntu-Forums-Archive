---
title: "Can't boot after install"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by SolarBear on 2005-03-09
Hi ! Sorry if the title is vague, but I'm kinda clueless about what's wrong here.

I've just installed Ubuntu on /dev/hda5. Here's my grub.conf :

```
default 0
timeout 10
splashimage=/boot/grub/splash.xpm.gz

title=Gentoo Linux 2.6.9-r4
root (hd1,0)
kernel /kernel-2.6.9-gentoo-r4 root=/dev/hdb4

title=Windows XP
rootnoverify (hd0,0)
makeactive
chainloader +1

title=Ubuntu Linux 4.10
root (hd0,4)
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda5
```

Nothing fancy, heh, but still, I get the following message :

VFS: Cannot open root device "hda5" or (0,0)
Please append a correct "root=" boot option

What's going on ? I've read head [here](http://forums.gentoo.org/viewtopic.php?t=122656&highlight=grub+error+collection) that it could be a kernel problem... but I'd tend to think Ubuntu would support ReiserFS out of the box.

So ? any ideas ?

---

### Post by krusbjorn on 2005-03-10
on my machine, hda5 by default is the swap partition. 
did you partition your disk correctly when installing Ubuntu?

---

### Post by SolarBear on 2005-03-10
[QUOTE=krusbjorn]on my machine, hda5 by default is the swap partition. 
did you partition your disk correctly when installing Ubuntu?[/QUOTE]
 Have a look for yourself.

```
root@candyland solarbear # fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
16 heads, 63 sectors/track, 79656 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       59240    29856771    7  HPFS/NTFS
/dev/hda2           59240       79656    10289601+   f  W95 Ext'd (LBA)
/dev/hda5   *       59240       79656    10289601   83  Linux

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1           7       56196   83  Linux
/dev/hdb2            7180        9729    20482875    f  W95 Ext'd (LBA)
/dev/hdb3               8         132     1004062+  82  Linux swap / Solaris
/dev/hdb4             133        7179    56605027+  83  Linux
/dev/hdb5            7180        9729    20482843+   b  W95 FAT32

Partition table entries are not in disk order
```

I'm using a swap partition from another disk but I fail to see what could be wrong with that. But as usual, I must be wrong. ;)

---

### Post by GrapeApe on 2005-03-10
Not sure if this will help, but it appears you are missing

initrd   /boot/initrd.img-2.6.8.1-3-386 

after the kernel command for ubuntu.

I was getting the same error when I was trying to make a boot cd for ubuntu.  Couldn't find the root device.  As soon as I added the init option it worked.

Your ubuntu should be something like ....

title=Ubuntu Linux 4.10
root (hd0,4)
kernel /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda5
initrd /boot/initrd.img-2.6.8.1-3-386

---

### Post by SolarBear on 2005-03-11
You know what ? That worked ! Thanks a bunch !

---

### Post by GrapeApe on 2005-03-11
I'm glad it worked for you.

---

