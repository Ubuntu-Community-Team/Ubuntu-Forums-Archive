---
title: "No boot option"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by TimEnid on 2010-07-12
I have windows 7 installed to one hd, and installed Ubuntu to another internal. The install went well, and when it was done, it said it had to restart. But upon restarting, i wasnt give the option to boot ubuntu. It just keeps loading windows. I went back to my bios and chose to boot from both hd's, but nothing is happening. With the hd with ubuntu on it, it wont load up. Any help? I didnt get any error messages during the install.

---

### Post by lindsay7 on 2010-07-12
Lets see that you system looks like.

type the following into the terminal  sudo fdisk -l   (that is the lower case letter L) and post the results here.

---

### Post by TimEnid on 2010-07-12
> **lindsay7 said:**
> Lets see that you system looks like.

type the following into the terminal  sudo fdisk -l   (that is the lower case letter L) and post the results here.

sorry, but i cant type anything in the terminal, because ubuntu wont load up. i just installed it a little while ago. only thing i am able to load is windows 7.

---

### Post by lindsay7 on 2010-07-12
Try this,

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

tell us what happens

---

### Post by TimEnid on 2010-07-12
> **lindsay7 said:**
> Try this,

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

tell us what happens

thanks. i will try this out.

---

### Post by TimEnid on 2010-07-12
that didnt work. i tried installing the grub to both the ubuntu hd and the w7 hd. nothing. after it restarts, my monitor is not detected and i have to restart it all over again

---

### Post by lindsay7 on 2010-07-12
start up with the ubuntu install disk and post the results of

sudo fdisk -l

---

### Post by TimEnid on 2010-07-13
> **lindsay7 said:**
> start up with the ubuntu install disk and post the results of

sudo fdisk -l

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd8f3c04b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x19ad14d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488383488    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009f891

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       58336   468581376   83  Linux
/dev/sdc2           58336       60802    19803137    5  Extended
/dev/sdc5           58336       60802    19803136   82  Linux swap / Solaris

Disk /dev/sde: 16.4 GB, 16372989952 bytes
255 heads, 63 sectors/track, 1990 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00819419

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        1991    15985152    7  HPFS/NTFS

Disk /dev/sdf: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1           7       56196   de  Dell Utility
/dev/sdf2   *           8        4430    35527747+  42  SFS
/dev/sdf3            4431        4863     3477501   42  SFS
```

---

### Post by Darkness Des on 2010-07-13
I have no idea where you're going with this, but if you want to add Ubuntu as an option to the Windows 7 Bootloader, go to the link below and download the latest build. You have to sign up for this.
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)
When making a new boot entry, make sure you select GRUB2 and it will auto detect where it is on your hard drive and add Ubuntu to your boot menu. I then select adding a shorter timeout on GRUB so that it goes straight to Ubuntu instead of adding another wait.

---

### Post by TimEnid on 2010-07-13
> **Darkness Des said:**
> I have no idea where you're going with this, but if you want to add Ubuntu as an option to the Windows 7 Bootloader, go to the link below and download the latest build. You have to sign up for this.
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)
When making a new boot entry, make sure you select GRUB2 and it will auto detect where it is on your hard drive and add Ubuntu to your boot menu. I then select adding a shorter timeout on GRUB so that it goes straight to Ubuntu instead of adding another wait.

This worked. thanks a lot. How do you add the shorter timeout?

---

