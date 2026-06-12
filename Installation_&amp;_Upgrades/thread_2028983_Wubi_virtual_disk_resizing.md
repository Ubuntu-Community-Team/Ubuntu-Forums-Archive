---
title: "Wubi virtual disk resizing"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by Ajay8055 on 2012-07-19
Guys i am total noob in linux ....
i embraced ubuntu just a week back......
i am using ubuntu 12.04 wubi installer i ran out of space so i used the wiki guide to increase the size of the virtual disk...it worked with no errors but the home folder of mine is 30gigs instead of 60gigs...i booted to windows 7 and checked my installation folder....i had home.disk(the new appeared disk) root.disk and swap.disk.....
i want to have more space so how can add the virtual drives to my home directory...

check this image please 

[http://postimg.com/image/76000/photo-75877.jpg](http://postimg.com/image/76000/photo-75877.jpg)

---

### Post by sudodus on 2012-07-19
I suggest that you migrate your wubi install to partition instead of resizing it. Wubi is good for testing, but if you want to use Ubuntu as (one of) your main system(s), I recommend dual boot with regular partitions. See this link

[[COLOR="Red"]_https://help.ubuntu.com/community/MigrateWubi_[/COLOR]]("https://help.ubuntu.com/community/MigrateWubi")

One reason to 'only' resize wubi is that you already have four primary partitions, and don't want or dare to edit your partitions. In that case see this link

[[COLOR="red"]_https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk_[/COLOR]]("https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk")

---

### Post by Ajay8055 on 2012-07-19
thanks for the reply sir...thats why i sticked to wubi the wubi is on my 5th partition...


[HTML]How do I resize the virtual disks?

Refer to the following guide: https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk

Note that LVPM only works to resize older releases of Ubuntu (those using grub-legacy).

As an alternative, you can use the following script to move /home to a dedicated virtual disk.

Download wubi-add-virtual-disk, open a terminal and run:


sudo sh wubi-add-virtual-disk /home 15000
Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.

You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab.

Note that contrary to previous information, this script is not suitable for moving /usr.

Experienced users may be able to do this manually, at own risk, following a process similar to that outlined in the file. (Do not rename /usr until the very last moment, as rsync is installed there.)[/HTML]
i used this guide from wiki...i just need access of the extra virtual disk created.....

---

### Post by ajgreeny on 2012-07-19
> **Ajay8055 said:**
> Guys i am total noob in linux ....
i embraced ubuntu just a week back......
i am using ubuntu 12.04 wubi installer i ran out of space so i used the wiki guide to increase the size of the virtual disk...it worked with no errors but the home folder of mine is 30gigs instead of 60gigs...i booted to windows 7 and checked my installation folder....i had home.disk(the new appeared disk) root.disk and swap.disk.....
i want to have more space so how can add the virtual drives to my home directory...

check this image please 

[http://postimg.com/image/76000/photo-75877.jpg](http://postimg.com/image/76000/photo-75877.jpg)
30GB is the maximum size that the wubi virtual disk can be, I think, so if you do need more space you will certainly need to migrate it to a proper dual boot partition, as recommended by sudodus.

I am not sure how to deal with a wubi install but for a start can you show the output of ```
sudo fdisk -l
``` in terminal, and if possible boot to a live ubuntu CD, run gparted and show a scerrnshot of the gparted window.  That will tell us exactly what partitions you already have.

EDIT:
I've just seen your reply to sudodus.  What exactly do you mean by "wubi is on my 5th partition"?  It sounds as if you must already have logical partitions on your disk which should make things easier to deal with, but see my gparted request above.

---

### Post by Ajay8055 on 2012-07-19
[HTML][Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfde8fde8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   102398309    51199123+   7  HPFS/NTFS/exFAT
/dev/sda2   *   511991613   716788169   102398278+   7  HPFS/NTFS/exFAT
/dev/sda3       716788170   976768064   129989947+   7  HPFS/NTFS/exFAT
/dev/sda4       102398310   511991549   204796620    f  W95 Ext'd (LBA)
/dev/sda5       102398373   307194929   102398278+   7  HPFS/NTFS/exFAT
/dev/sda6       307194993   511991549   102398278+   7  HPFS/NTFS/exFAT

Partition table entries are not in disk order
/HTML]


sudodos solution worked but the resize is limited to 32gb which for time being is enough... 

[HTML]**How do I create a virtual disk in Windows?**

 You  can use qemu-img for that. Another dirty (but working) trick is to copy  any other file of the desired size to C:\wubi\disks and rename it  "root.disk", "home.disk", "swap.disk" or "extra.disk". That's the Wubi  equivalent of buying (and installing) a new hard disk. [/HTML]

i read this in wubi wiki how to get it working?

---

