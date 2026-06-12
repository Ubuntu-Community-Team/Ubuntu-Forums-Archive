---
title: "automount drives but fstab modification disappeared after next reboot"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by horming on 2008-11-14
I want to auto-mount my following disk from [COLOR="DarkGreen"]fdisk -l dump[/COLOR]:

[COLOR="DarkGreen"]Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09340933

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS**

Disk /dev/sdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36c552c7

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1   *           1        5005    40202631    7  HPFS/NTFS**

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22652265

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdc1   *           1       10012    80416768    7  HPFS/NTFS**
/dev/sdc2           10013       10136      996030   82  Linux swap / Solaris
/dev/sdc3           10137       20023    79417327+  83  Linux[/COLOR]

I had tried using storage device manager but after the application modified the [COLOR="DarkGreen"]/etc/fstab[/COLOR],
all modification will disappeared after the next reboot.

I created the [COLOR="Blue"]/media/data[/COLOR], [COLOR="Blue"]/media/iso-images[/COLOR], [COLOR="Blue"]/media/vista[/COLOR] from [COLOR="Blue"]/dev/sda1[/COLOR], [COLOR="Blue"]/dev/sdb1[/COLOR], and [COLOR="Blue"]/dev/sdc1[/COLOR].

Here is my [COLOR="DarkGreen"]ls -l /dev/disk/by-uuid[/COLOR] dump

[COLOR="DarkGreen"] ls -l /dev/disk/by-uuid
total 0
**lrwxrwxrwx 1 root root 10 2008-11-15 20:22 020CF9D10CF9BFA9 -> ../../sdc1**
lrwxrwxrwx 1 root root 10 2008-11-15 20:22 807eb274-30ed-4099-88d4-788a52684d7c -> ../../sdc2
**lrwxrwxrwx 1 root root 10 2008-11-15 20:22 9278881F78880467 -> ../../sdb1**
**lrwxrwxrwx 1 root root 10 2008-11-15 20:22 C8B8CC69B8CC5818 -> ../../sda1**
lrwxrwxrwx 1 root root 10 2008-11-15 20:22 ef5332dd-dbd2-468b-a3bb-1d2ee67d8be4 -> ../../sdc3[/COLOR]

Thanks & Help

---

### Post by taurus on 2008-11-14
What's the error message when you try to mount this ntfs partition, /dev/sda1?

```
sudo mount -t ntfs-3g /dev/sda1 /media/data
```

---

### Post by horming on 2008-11-15
There is no error doing this command.

---

### Post by horming on 2008-11-15
I finally found out the "MountManager" program will "restore" the modified "fstab" content after application exit.

Now I can automount by specifying fstab =)

Thanks,

---

