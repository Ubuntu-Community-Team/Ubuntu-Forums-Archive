---
title: "Can someone please help with fstab"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by parallelogram on 2007-10-02
I have a maxtor 500GB Here is how my fstab looks and seagate 500gb connected via sata . I boot from the maxtor. Maxtor is sda and seagate is sdb. Here is how fstab looks

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=46472221-5c9e-474d-9548-153bbf386b12 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/sda4 :
UUID=13885356-c5ae-46fb-9339-3bb6f8416d77 /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# Entry for /dev/sda1 :
UUID=C69415C79415BB3F /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda5 :
UUID=0A148C61148C521D /media/sda5 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=cc03df5a-247d-40b5-a16e-c8d5852d18c9 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb6 /media/sdb6 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdb7 /media/sdb7 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda6 /media/sda6 ntfs-3g defaults,locale=en_US.UTF-8 0 0

First of all - sda1, sda5 and sda6 are on my primary hard disk and they are all NTFS. Any idea why they are written differently in fstab. I ran ntfs-config and got the sda6 entry. But sda5 and sda1 were there before and they are referenced by UUID

I have an ext3 and fat32 partitions on my seagate. What do I need to write in fstab to mount them also

thanks

---

### Post by rsambuca on 2007-10-02
Could you post the output of 

sudo fdisk -l

---

### Post by parallelogram on 2007-10-02
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62918541    7  HPFS/NTFS
/dev/sda2            7834       50467   342457605    f  W95 Ext'd (LBA)
/dev/sda3           50468       59585    73240335   83  Linux
/dev/sda4           59586       60801     9767520   83  Linux
/dev/sda5            7834       20581   102398278+   7  HPFS/NTFS
/dev/sda6           20582       39703   153597433+   7  HPFS/NTFS
/dev/sda7           50187       50467     2257101   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3824    30716248+   b  W95 FAT32
/dev/sdb2            3825       60801   457667752+   5  Extended
/dev/sdb5            3825       19122   122881153+  83  Linux
/dev/sdb6           19123       38244   153597433+   7  HPFS/NTFS
/dev/sdb7           38245       60801   181189071    7  HPFS/NTFS

---

### Post by rsambuca on 2007-10-02
It looks like the ones you want to have automounted at boot time are sdb1 and sdb5.  Does that look correct to you?  If so, there are a couple of things that you need to do.

1.  Create folders on your Ubuntu filesystem to which you can mount these partitions.

2.  Edit your fstab to have the partitions mounted at boot time.

Instructions:

1.  ```
sudo mkdir /media/sdb1
sudo mkdir /media/sdb5
```You can obviously name them what ever you want.  In this example the first folder will be called /media/sdb1, etc.

2.  For the FAT32 partition (Why do you have this, anyways???)Edit your fstab using the gedit text editor:
```
gksudo gedit /etc/fstab
```
Add this to the end of you fstab:
```
# Entry for /dev/sdb1 :
/dev/sdb1 /media/sdb1 vfat defaults,utf8,umask=007,gid=46 0 1

```

---

### Post by parallelogram on 2007-10-02
Thanks!

To answer your question about why I have FAT32 - I really don't know. I just thought since I have enough storage I'll leave a small amount of space for the partition which most rescue CDs/Programs might like. So FAT32. Other than that I have no use and it is just blank

---

