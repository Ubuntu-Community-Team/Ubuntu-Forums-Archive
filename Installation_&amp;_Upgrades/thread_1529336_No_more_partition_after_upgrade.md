---
title: "No more partition after upgrade"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by gavrochelegnou on 2010-07-12
Hello, 
I just upgraded an ubuntu-server from 8.10 to 9.04 via "do-release-upgrade"
And after reboot, no partition from one of my hard drives can't be mounted :
Drive is /dev/sdc

And when i try to mount it :
```
root@mob:~# mount /BACKUPS
mount: special device /dev/sdc1 does not exist

```
Or : 
```
root@mob:~# swapon /dev/sdc2
swapon: /dev/sdc2: stat failed: No such file or directory

```
But fdisk returns this :

```
Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18966   152344363+  83  Linux
/dev/sdc2           18967       19457     3943957+  82  Linux swap / Solaris

```

Any idea of what could be wrong ? 
Is it normal that disk identifier is 0x00000000 ?
Thanks a lot.

---

### Post by Sanjeevtrip on 2010-07-12
Check 
```

dmesg

```

and /var/log/messages if any error message appears
what does your /etc/fstab have?

---

### Post by gavrochelegnou on 2010-07-12
The only relevant lines in dmesg seems to be :

```

[    2.148442] scsi 3:0:0:0: Direct-Access     ATA      ST3160827AS      3.42 PQ: 0 ANSI: 5
[    2.148514] sd 3:0:0:0: [sdc] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.148527] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    2.148548] sd 3:0:0:0: [sdc] Write Protect is off
[    2.148550] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.148568] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.148653]  sdc: sdc1 sdc2
[    2.175326] sd 3:0:0:0: [sdc] Attached SCSI disk
```

nothing relevant in /var/log/messages

And the according lines in fstab is :

```
/dev/sdc1      /BACKUPS        ext3    relatime,errors=remount-ro      0       1
```

But i've just seen that my other hard drive is declared via UUID and not /dev/xyz.
I will try to do the same with this one.

---

### Post by dino99 on 2010-07-12
find your uuids with blkid into a console, compare with fstab and modify if its needed, then update grub

---

### Post by gavrochelegnou on 2010-07-12
Thanks for your replies.
I found the UUID by looking into /dev/disk/by-uuid/ and changed it accordingly in /etc/fstab and now everything works fine.

Is it normal that partitions appears no more as sdc1, sdc2, ... or should i worry ?

My system currently boots fine, can i keep it like :
root=/dev/md0 
or should i change it to :
root=UUID=wxyz-wxyz-wxyz...

thanks a lot !

---

### Post by gavrochelegnou on 2010-07-12
Actually my two partitions doesn't show up as /dev/sdc1 /dev/sdc2
but as : 
/dev/mapper/hpt45x_bacdbejdai1
and
/dev/mapper/hpt45x_bacdbejdai2

is it just driver relevant ? or a global change ?
(my two other raid partitions on different disks still show up as /dev/sda1)

---

