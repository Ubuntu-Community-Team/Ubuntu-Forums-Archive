---
title: "cant see my partitions"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by qaisar on 2013-02-07
Hi, I have got samsung laptop with 700 gb hard drive storage. My laptop came with windows 7 by default so i made a another partition and installed windows 8 trial on my 2nd partition. Then i had 2 windows installed at same time. Yesterday I have decided to replace windows 8 trial with ubuntu 12.10. While i was installing ubuntu it gave me option to replace windows 8 with ubuntu or install alongside. I chose replace option. So i was able to install ubuntu successfully.

It use to give me option to choose windows 7 or windows 8, now the problem is i am not getting the windows 7 option, i really need that partition becaz i have save stored everything in there. Please help...

---

### Post by darkod on 2013-02-07
Boot with the cd in live mode, open terminal and post the output of:
```
sudo parted -l (that's small L)
```

---

### Post by qaisar on 2013-02-08
> **darkod said:**
> Boot with the cd in live mode, open terminal and post the output of:
```
sudo parted -l (that's small L)
```

thanks for replying... here is the output of sudo parted -l

faizan@faizan-300E4C-300E5C-300E7C:~$ sudo parted -l
Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  744GB  744GB   primary   ext4            boot
 2      744GB   750GB  6212MB  extended
 5      744GB   750GB  6212MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by schragge on 2013-02-08
It seems like you wiped out all your Windows partitions when installing Ubuntu :(.

---

### Post by darkod on 2013-02-08
Yeah, it seems you wiped it. If you want to try recovering the partition, STOP booting the computer from the hdd right now. Use it with the ubuntu cd in live mode. That way it doesn't write to the disk.

In ubuntu live mode you can download and run testdisk, which can scan the hdd for all previous partitions and try to recover the ones you want.
You have a tutorial here:
[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

As first step, download and run the program, and do the Deeper Search. Post the screenshot here and we can try to figure out which partitions to try recover. Be careful, the output of testdisk might look confusing but it's very good with recovering partitions.

---

### Post by furything on 2013-02-08
> You have a tutorial here:
[www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")
I have seen this listed on tomshardware.com but not yet tried it.

Is this the tool of your choice?

---

### Post by darkod on 2013-02-08
> **furything said:**
> I have seen this listed on tomshardware.com but not yet tried it.

Is this the tool of your choice?

Yes, that would be my choice. First to scan what can be found, and after making sure you select the right partition, try to recover it (write a new partition table).

A small problem is that testdisk often shows many old partitions, including some that were deleted on purpose. So you have to be careful and recover the correct one. It offers to try and read files on a partition with P when you have the highlight bar on it.
That way you can see on which partition files can actually be read.

---

