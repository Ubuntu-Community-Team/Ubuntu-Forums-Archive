---
title: "Partitions on hdb not mounted"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by panorack on 2008-05-26
I have two IDE drives in my box and have just done a complete install of 8.04 on the same partition of hda I used for 7.10 (after reformatting). On hdb there are three FAT32 partitions and two EXT3 but 8.04 has not found any of them, although it has mounted a SWAP partition on this same drive. There has to be a simple answer but I am at a loss.

(I have gone through the process of editing the fstab file and mkdir to set up the directories in /mnt but when trying to mount these partitions I get an error message that they do not exist. Gparted is showing them as not mounted and I can access the FAT partitions from Windows XP so they are not damaged in any way.)

Can anyone help please.:confused:

Thanks in anticipation,

panorack

---

### Post by didac on 2008-05-26
Could you post the results of:

```
sudo fdisk -l
```

---

### Post by panorack on 2008-05-26
Hi Didac,

Result of 'sudo fdisk -l' as follows:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ed63f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15943   128062116    7  HPFS/NTFS
/dev/sda2           15944       21260    42708771   83  Linux
/dev/sda3           21261       23820    20563200    f  W95 Ext'd (LBA)
/dev/sda4           23821       30401    52861882+  83  Linux
/dev/sda5           21261       23820    20563168+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c593bab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb2               1           1        8001    1  FAT12
/dev/sdb5               2        6376    51207156    b  W95 FAT32
/dev/sdb6            6377       14025    61440561    b  W95 FAT32
/dev/sdb7           14026       15300    10241406    b  W95 FAT32
/dev/sdb8           15301       22216    55544737    7  HPFS/NTFS
/dev/sdb9           22216       22427     1702858+  82  Linux swap / Solaris
/dev/sdb10          22428       25038    20972826   83  Linux
/dev/sdb11          25039       30401    43078266   83  Linux

Partition table entries are not in disk order

Hope this is helpful,

Panorack

---

### Post by didac on 2008-05-26
edit your fstab:

```
sudo /etc/fstab
```

and add the following lines:

```

/dev/sdb5  /media/sdb5  vfat  defaults,utf8,umask=007,gid=46  0  0
/dev/sdb6  /media/sdb6  vfat  defaults,utf8,umask=007,gid=46  0  0
/dev/sdb7  /media/sdb7  vfat  defaults,utf8,umask=007,gid=46  0  0
/dev/sdb8  /media/sdb8  ntfs  defaults,umask=007,gid=46  0  0

```

Save and type

```

sudo makedir /media/sdb5
sudo makedir /media/sdb6
sudo makedir /media/sdb7
sudo makedir /media/sdb8
sudo mount -a

```

They should be mounted now.

---

### Post by panorack on 2008-05-26
Hi didac,

followed your instructions and got the same result as my first attempt. I get the following message:

mount: special device /dev/hdb5 does not exist

.. repeated for each of the other partitions. Checked /media and the directories are there, as are the additions to fstab.


Hope this tells you something useful!

Thanks,

panorack

---

### Post by didac on 2008-05-26
You have to put sdb5 and not hdb5. Instead of 'h' use an 's'

I know you don't have scsi disks, and that h is for normal hard disks, but Ubuntu uses sdb5.

---

### Post by panorack on 2008-05-26
Hi didac,

Thanks for that. Just a little slip but it made all the difference. Everything is showing and working fine. 

Not quite sure how to show this thread is answered satisfactorily, but have sent a thanks and add my own thanks.

Panorack

---

