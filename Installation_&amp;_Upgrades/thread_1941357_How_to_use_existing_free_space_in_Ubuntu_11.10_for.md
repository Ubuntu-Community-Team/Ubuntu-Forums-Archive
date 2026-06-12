---
title: "How to use existing free space in Ubuntu 11.10 for dual booting without data loss?"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by shankhaagt on 2012-03-15
Hi,

I have a 120 GB SATA Hard disk and the entire hard disk has only Ubuntu 11.10 installed ,mount point is /. Below are the details of current partition:

sudo blkid
/dev/sda1:  UUID="dcb382b9-c8aa-441e-8a16-8e2f81d3ec4a"     TYPE="ext4" 
/dev/sda5: UUID="4e2c2ec4-4b03-48a9-ac2f-6f6cc5b09393" TYPE="swap"

sudo fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   232366079   116182016   83  Linux
/dev/sda2       232368126   234440703     1036289    5  Extended
/dev/sda5       232368128   234440703     1036288   82 Linux swap 



Filesystem            Size  Used Avail Use%   Mounted on
/dev/sda1             110G   59G   46G  57%    /
udev                  1.5G  8.0K  1.5G   1%    /dev
tmpfs                 604M  1.2M  603M   1%    /run
none                  5.0M  8.0K  5.0M   1%    /run/lock
none                  1.5G  428K  1.5G   1%    /run/shm

Ouput of discus command :

anirban@Zion:~$ discus
Mount           Total         Used         Avail      Prcnt      Graph
/              109.06 GB     58.43 GB     50.63 GB    53.6%   [*****-----]
/sys                0 KB         0 KB         0 KB     0.0%   [----------]
+onnections         0 KB         0 KB         0 KB     0.0%   [----------]
+rnel/debug         0 KB         0 KB         0 KB     0.0%   [----------]
+l/security         0 KB         0 KB         0 KB     0.0%   [----------]
/dev             1.46 GB         8 KB      1.46 GB     0.0%   [----------]
/run            603.4 MB       1.1 MB     602.2 MB     0.2%   [----------]
/run/lock         5.0 MB         8 KB       5.0 MB     0.2%   [----------]
/run/shm         1.47 GB       428 KB      1.47 GB     0.0%   [----------]
+infmt_misc         0 KB         0 KB         0 KB     0.0%   [----------]
+block-fuse         0 KB         0 KB         0 KB     0.0%   [----------]

Now I want to use the remaining 46 GB available space in /dev/sda1 to install Fedora 16 without losing any existing data.I

Please advise how to proceed
Please let me know if any additional details are needed.

---

### Post by darkod on 2012-03-15
1. You need to make a full backup of your data. Shrinking partitions always carries some risk of data loss.
2. Then you need to boot the computer with the ubuntu cd in live mode (not from the hdd), open Gparted and shrink /dev/sda1 for as much space as you want. Be aware that you can't shrink all of the 46GB free because ubuntu will not work if the root partition is 100% full. You can't leave it without any free space.
3. When you have unallocated space left after the shrink, install fedora onto it. I would select not to install a bootloader during the fedora install and after that during the first ubuntu boot just run update-grub and it will detect it and create an entry in the boot menu. That will leave grub2 from ubuntu on the MBR.

Make sure fedora doesn't install with LVM or something, I am not sure how it installs these days. That's your job to investigate and know what are you doing. :)

---

### Post by shankhaagt on 2012-03-15
Thanks darkod , i wouldnt have bother to leave any free space but for you...would have messed up...and that LVM too..shall try and update the post:)

---

