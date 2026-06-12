---
title: "Problem with /etc/fstab, mounting partition, Grub's looks"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by vdorta on 2005-08-06
I installed Ubuntu in dual boot with a previously installed Mepis. Ubuntu's Grub wiped Mepis' booting data off, but I copied it from the Mepis partition and now both can be booted OK. However, I did something wrong either when mounting the Mepis partition or when I added the Mepis data to /fstab. Ubuntu now says that " line 6 of /etc/fstab is wrong", and now I can't find the Mepis information anymore because hda1 shows as a folder in /mnt but without any data.

I would also like to have the Mepis partition automatically mounted when X starts.

fdisk -l gives this:

/dev/hda1               1         637     5116671   83  Linux (Mepis)
/dev/hda2   *         638        1193     4466070   83  Linux (Ubuntu)
/dev/hda3            1194        1222      232942+   5  Extended
/dev/hda5            1194        1222      232911   82  Linux swap / Solaris

and this is my fstab file:

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda: 262 MB, 262144000 bytes (pen drive)

and the Grub/device.map file:

(hd0)	/dev/hda
(hd1)	/dev/sda

Finally, Can I use Mepis' Grub (much better looking, imho) and copy the Ubuntu data into it?

Thanks.

---

### Post by kosmic on 2005-08-06
in grub to start with mepis you need to have this :

hd0,0 -> /dev/hda1 (hd0,0) is partition hda1 where Mepis is

and to start ubuntu with should have this :

hd0.1 -> /dev/hda2 (hd0,1) is partition hda2 where ubuntu is :)

and yes you can copy the configuration file of grub from Mepis to ubuntu :)

---

