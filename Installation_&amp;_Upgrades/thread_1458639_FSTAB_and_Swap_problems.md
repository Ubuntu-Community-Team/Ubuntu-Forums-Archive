---
title: "FSTAB and Swap problems"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by mavenofmirth on 2010-04-20
Hi,
So I recently installed Kubuntu, and everything was running smoothly. Specifically, my swap space was configured correctly and working.
Then I decided I wanted to have a couple of my hard drives auto mount on startup, so I used mountmanager to try and set it up (rather foolishly, I did not back-up my FSTAB file beforehand, assuming the software would do it automatically). Since then swap no longer mounts, and the hds didn't automount either.
Here's 'free -m' just to show you:
```
             total       used       free     shared    buffers     cached
Mem:          1507       1466         41          0        119        753
-/+ buffers/cache:        593        914
Swap:          854          0        854

```
My current FSTAB
```
# device name mount point fs-type options dump-freq pass-num

#Floppy
/dev/fd0 /media/floppy0 vfat noauto 0 0

#Linux
UUID=30068e60-1512-449c-84d9-02e76cb8cdd3 none swap sw 0 0
UUID=437d0cc7-1e67-4095-af85-1074c7979621 / ext4 defaults 0 1
#UUID=30068e60-1512-449c-84d9-02e76cb8cdd3 none swap sw 0 0
#/dev/sdb6 none swap sw 0 0

#SATA HD
#UUID=3670A30770A2CD45 /media/disk-1 ntfs-3g auto,users,rw 0 0
#/dev/sdc1 /media/disk-1 ntfs defaults,nls=utf8,umask=007,uid=1000 0 0
#/dev/sdc1 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

#HD2
#UUID=90C09D5DC09D4A7C /media/HD2 ntfs-3g auto,users,rw 0 0 
#/dev/sdb5 /media/HD2 ntfs defaults,nls=utf8,umask=007,uid=1000 0 0
#/dev/sdb5 /media/HD2 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

```
The commented out lines are what I've tried (manually configuring, and copying from mtab after mounting in Dolphin). When trying either of the 2 manual entries for HD2, I can hear the hard drive going crazy, as is the disk usage led, but it's not mounted, and would no longer mount in Dolphin.

sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076813

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9243    74244366    7  HPFS/NTFS
/dev/sda2            9244        9728     3895762+   f  W95 Ext'd (LBA)
/dev/sda5            9244        9728     3895731    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x790b6e59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2441    19607301   83  Linux
/dev/sdb2   *        2442       14945   100438380    f  W95 Ext'd (LBA)
/dev/sdb5            2551       14945    99562806    7  HPFS/NTFS
/dev/sdb6            2442        2550      875479+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7dfc7df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36482   293041633+   7  HPFS/NTFS

```
sudo blkid
```
/dev/sda1: UUID="0238F2D238F2C3A7" TYPE="ntfs" 
/dev/sda5: UUID="8430A88430A87EB4" TYPE="ntfs" 
/dev/sdb1: UUID="437d0cc7-1e67-4095-af85-1074c7979621" TYPE="ext4" 
/dev/sdb5: UUID="90C09D5DC09D4A7C" LABEL="HD2" TYPE="ntfs" 
/dev/sdb6: UUID="30068e60-1512-449c-84d9-02e76cb8cdd3" TYPE="swap" 
/dev/sdc1: UUID="3670A30770A2CD45" TYPE="ntfs" 
```

Ideally I'd like to get swap back and have /dev/sdc1 & /dev/sdb5 automount on startup.
Any help would be greatly appreciated.
Thanks :)

**EDIT:**
Har, I'm so blind. Clearly my swap space is working correctly. It wasn't working yesterday I didn't either bother to read the free -m output.
But I still need to figure out how to automount those partitions.
So again, any help is appreciated.

---

### Post by sisco311 on 2010-04-20
First you have to create the mount point(s):
```
sudo mkdir /media/**name**
```

An entry for an NTFS partition looks like this:
```
UUID=**uuid-of-the-partition**    /media/**name**    ntfs    defaults,gid=plugdev,dmask=0002,fmask=0113    0    0
```

This will mount the partition with read/write permissions for users from the plugdev group (the first user is already in this group) & read permissions for others.

You can run:
```
sudo mount -a
```to mount the partitions mentioned in fstab.

To add a user to the plugdev group, run:
```
sudo gpasswd -a **username** plugdev
```

[thread=283131]How to fstab[/thread]
[uhelp]community/Fstab[/uhelp]

---

### Post by mavenofmirth on 2010-04-20
Thank you so much :) That worked!
Care to point out what it was that I was doing wrong?

---

### Post by sisco311 on 2010-04-20
> **mavenofmirth said:**
> Thank you so much :) That worked!
Care to point out what it was that I was doing wrong?

You are welcome!

```
#UUID=90C09D5DC09D4A7C /media/HD2 ntfs-3g auto,users,rw 0 0 
#/dev/sdb5 /media/HD2 ntfs defaults,nls=utf8,umask=007,uid=1000 0 0

```

The above entries should work too, I have no idea what went wrong.

---

