---
title: "No uuid after upgrade to Gutsy"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by Ysbeer on 2008-03-06
Hi there,

I just upgraded my Breezy box to Gutsy. I noted that all device entries in /etc/fstab got changed to uuid's. All partitions for /dev/sda mounted fine and appear to have uuid's. My /dev/sdb disk don't have a corresponding uuid and subsequently don't mount. 

When I do a vol_id --uuid /dev/sdb1 it returns no information.

Can I create a uuid for the disk ? 

Any help will be much appreciated.

Regards,

---

### Post by Rui Pais on 2008-03-06
Hi. 
Whats the output of 
```
blkid
```?

---

### Post by Ysbeer on 2008-03-06
I hate following up my own posts but here goes. I googled a bit and found a reference to a "blkid" utility. I ran it and it showed the UUID for my /dev/sdb1 . I simply created the symbolic link that was missing in /dev/disk/by-uuid using the UUID output from blkid. Once done the filesystem mounted fine.

---

### Post by Rui Pais on 2008-03-06
> **Ysbeer said:**
> I hate following up my own posts but here goes. I googled a bit and found a reference to a "blkid" utility. I ran it and it showed the UUID for my /dev/sdb1 . I simply created the symbolic link that was missing in /dev/disk/by-uuid using the UUID output from blkid. Once done the filesystem mounted fine.

I told you that 4 minutes after you asked ;)

---

### Post by Ysbeer on 2008-03-07
Unfortunately my problems didn't stop there. After the first reboot the symbolik links for the two partitions I added dissaperead and I am back to square one.

Below is more detail. I have two SATA 56 Gb disks in a Fujitsu Siemens Blade server. Parted shows the following partition information:


root@ns1:/dev# parted /dev/sda print

Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  5001MB  5001MB  primary   ext3
 2      5001MB  7501MB  2500MB  primary   linux-swap
 3      7501MB  60.0GB  52.5GB  extended
 5      7501MB  17.5GB  10.0GB  logical   ext3
 6      17.5GB  27.5GB  10.0GB  logical   ext3
 7      27.5GB  37.5GB  10.0GB  logical   ext3
 8      37.5GB  45.5GB  8003MB  logical   ext3
 9      45.5GB  60.0GB  14.5GB  logical   ext3

root@ns1:/dev# parted /dev/sdb print

Disk /dev/sdb: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  60.0GB  60.0GB  primary  ext3

On the first disk only 6 of the 7 partitions get mounted. /dev/sda9 don't get mounted and the singe partition on /dev/dsb don't get mounted. There aren't any UUID's created for them in /dev/disk/by-uuid/

root@ns1:/dev/disk/by-uuid# ls -alF
total 0
drwxr-xr-x 2 root root 160 2008-03-07 13:07 ./
drwxr-xr-x 5 root root 100 2008-03-07 13:07 ../
lrwxrwxrwx 1 root root  10 2008-03-07 13:07 110a70f3-a754-4771-94cd-c97d80265437 -> ../../sda8
lrwxrwxrwx 1 root root  10 2008-03-07 13:07 2c8906a3-6074-4528-b39d-3d6cc0bc48af -> ../../sda7
lrwxrwxrwx 1 root root  10 2008-03-07 13:07 463dc866-212f-40c4-ab05-f61cd8118176 -> ../../sda5
lrwxrwxrwx 1 root root  10 2008-03-07 13:07 aaaac4ec-a5a0-49b0-b9ed-fa17098529f3 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-03-07 13:07 c4c5dea5-f69c-44de-bd4f-5e114768d678 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-03-07 13:07 f8d83d1d-7226-43f7-9bec-3b945c773e49 -> ../../sda6

blkid shows the following:

root@ns1:/dev# blkid
/dev/sda1: UUID="c4c5dea5-f69c-44de-bd4f-5e114768d678" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda2: TYPE="swap" UUID="aaaac4ec-a5a0-49b0-b9ed-fa17098529f3"
/dev/sda5: UUID="463dc866-212f-40c4-ab05-f61cd8118176" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda6: UUID="f8d83d1d-7226-43f7-9bec-3b945c773e49" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda7: UUID="2c8906a3-6074-4528-b39d-3d6cc0bc48af" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda8: UUID="110a70f3-a754-4771-94cd-c97d80265437" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda9: UUID="e54d35ca-95bf-4c0b-8f01-aaa322001424" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdb1: UUID="900ecc0d-0604-45fb-94af-68a2bda2bb67" SEC_TYPE="ext2" TYPE="ext3"

When I manually create the symolic links (info from blkid) I can mount the devices. After the first reboot the symbolic links from the two partitions that weren't created after the upgrade dissapear and I am back to square one. 

Has anyone encountered this problem ? How did you solve it ? Or is it better to simply use the actual device files in /dev/dsk and not the UUID ? It does make for a pretty confusing /etc/fstab file ?

Regards,

---

### Post by Ysbeer on 2008-03-11
Guess no-one has encountered this problem then ?

---

