---
title: "Big boot problems"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by snakeminidez on 2008-05-30
I tried to install PClinuxOS on mt Toshiba Satellite, however after manually editing the partitions and pressing the "next" button on the install process the screen just closes and nothing happens, so I (stupidly) decided to shut down the computer with the live CD still in, and when I restarted the computer there's no GRUB menu at all. So I attempted to just install PClinuxOS again however the installer said that there was no room on the harddrive. However after putting in a LinuxMint Live CD, I am still able to view all of my Vista folders, pic, videos, and all that good stuff. So how do I partition the dick again, but without deleting Windows, and still having the ability to install another linux distro.

---

### Post by ugm6hr on 2008-05-30
Have you backed up Vista?  If not - I would recommend you do that before any further partitioning, since it can jeopardise your data.

With the LinuxMint CD booted, type the following and post the output:
```
sudo fdisk -l
```

It may well be that you have already partitioned the disk.

PS: I am not very familiar with either Mint or PCLOS - this is the Ubuntu forum!

---

### Post by snakeminidez on 2008-05-30
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c4d8ab6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4523    36323328    7  HPFS/NTFS
/dev/sda2            4524       14593    80887275    5  Extended
ubuntu@ubuntu:~$ 
 

And yeah I know this is the Ubuntu forum, but I usually get the most help from here

---

### Post by ugm6hr on 2008-05-30
> Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Not sure what this means.

But the fdisk output looks like sda2 is an extended partition with no logical partitions within it.

Presumably a partitioner (e.g. gparted or cfdisk) could erase that and create a new partition table.

However, I would suggest you ensure things are backed up before going any further.

---

### Post by snakeminidez on 2008-05-30
OK, just to be clear, I should open gparted and format all the unallocated space, which for some reason says 111.79 GiB, and then just make a partition that was teh same sixe as the original windows partition

---

### Post by ugm6hr on 2008-05-30
> **snakeminidez said:**
> OK, just to be clear, I should open gparted and format all the unallocated space, which for some reason says 111.79 GiB, and then just make a partition that was teh same sixe as the original windows partition

No.

It looks like the Windows partition (sda1) is 40GB at the start of the disk.  Leave that alone.

Just delete sda2.

Then where you go from there is dependent on how you want to install Linux.  I don't know enough about the installers you want to use to tell you how to proceed.  It may be more sensible to leave the 80GB space unallocated for a reattempt at installation.

PS: Please backup before doing anything else.

---

### Post by snakeminidez on 2008-05-30
This is going to sound real sketch, but for some reason those partitions do not show up in gparted. Gparted shows two /dev/sda 111.75GiB and /dev/scd0 172.57MiB, and both of those are unallocated, yet, once again, I can still view and edit the folders in Vista.

---

### Post by galileon on 2008-05-30
> **snakeminidez said:**
> So how do I partition the dick again

bad idea :p

---

### Post by ugm6hr on 2008-05-30
> **snakeminidez said:**
> This is going to sound real sketch, but for some reason those partitions do not show up in gparted. Gparted shows two /dev/sda 111.75GiB and /dev/scd0 172.57MiB, and both of those are unallocated, yet, once again, I can still view and edit the folders in Vista.

I have encountered this kind of thing before.  It is something to do with the partition table not matching the actual partitions.

There is a way to fix it, but I ended up just reformatting the whole drive.

---

### Post by snakeminidez on 2008-05-30
> **galileon said:**
> bad idea :p

lol, and I guess I'll just reformat it then, there wasn't that much on windows to begin with

---

### Post by ugm6hr on 2008-05-30
> **snakeminidez said:**
> lol, and I guess I'll just reformat it then, there wasn't that much on windows to begin with

Consider partitioning before installing Windows too.

---

