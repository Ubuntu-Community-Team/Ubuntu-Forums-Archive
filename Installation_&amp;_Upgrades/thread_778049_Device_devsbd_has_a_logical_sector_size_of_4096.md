---
title: "Device /dev/sbd has a logical sector size of 4096"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by SHiNiNG_SaBeR on 2008-05-01
Hi.  I'm relitively new to the ubuntu scene (Have only installed it once on a real PC, twice on virtual pcs), and I get this error when I'm trying to install it on my computer:
```
Device /dev/sbd has a logical sector size of 4096.  Not all parts of GNU Parted Support this at the moment, and the working code is HIGHLY EXPERIMENTAL.
```
I was thinking it might have to do something with the size set when I formatted my XP distribution (the little thing besides space, that had a bunch of numbers that were in multiples of 4), but I can't reinstall XP at the moment, since I don't have a PC to back up all of my data from this one on.  I was wondering, if thats the problem, is there some way to edit the logical size without reformatting?
My specs:
Intel Core 2 Duo at 2.4 GHz
2 GB PC4200 RAM
ATi Radeon X1950 Pro
160 GB HDD (Partitions : 107.42 GB NTFS containing Windows XP (x32 Home), 2 GB Linux-Swap, 39.63 GB EXT3 (For Ubuntu))
I'm installing Ubuntu 8.04 x32
Any help would be appreciated.:)

---

### Post by Patb on 2008-05-02
Saber, if you can boot from the live CD, what is the output of 
```
sudo fdisk -l
```
Cheers, Pat.

---

### Post by SHiNiNG_SaBeR on 2008-05-02
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
11 heads, 1 sectors/track, 28416528 cylinders
Units = cylinders of 11 * 512 = 5632 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1    20480000   112639999+   7  HPFS/NTFS
/dev/sda2        20480001    20861300     2097150   82  Linux swap / Solaris
/dev/sda3        20861301    28416528    41553754   83  Linux

```
EDIT : I feel bad, because today I booted off of my Ubuntu CD (I reburnt it), and it worked fantastically.  Thanks for trying to help, I appreciate it.

---

### Post by Dunke on 2008-05-02
I told you yesterday making a new one would probably fix your problem. I'm happy you solved it :)

---

### Post by Patb on 2008-05-02
> **SHiNiNG_SaBeR said:**
> EDIT : I feel bad, because today I booted off of my Ubuntu CD (I reburnt it), and it worked fantastically.  Thanks for trying to help, I appreciate it.
You're welcome and don't worry, you were right to post.  The "/dev/sdb" in your original post looked odd.  Cheers, Pat.

---

### Post by crazyheinz on 2008-11-14
i have the same problem with a debian cd. 
the error is the same, only it's dev/scsi/host4/bus0/target0/lun0/disc 
I always get this message when it's time to partition the disk. Always at 41 procent i get the message.

---

### Post by sankar_s on 2009-04-06
I am trying to install Ubuntu for the first time and seeing the same issue (Device /dev/sbd has a logical sector size of 4096.  Not all parts of GNU Parted Support this). 

I am not clear about how the logical sector size issue is resolved. Though it gives this warning, I am able to install and get it to work. However, I would like to understand how this issue was addressed earlier.

---

