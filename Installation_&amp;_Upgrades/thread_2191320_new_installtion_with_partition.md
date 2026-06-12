---
title: "new installtion with partition"
date: 2013-12-02
forum: Installation &amp; Upgrades
---

### Post by vs-punn on 2013-12-02
I bought a new laptop with 500GB Hard disk.I want to create two partition on the HDD with the following:
50GB for Ubuntu
rest for backup and storing all the data (sharable with WIndows or other users).

When doing a new installation, I selected something else on the step and then divided the HDD in two partitions. 
50GB was alloted as ext3 partition with mount to / .
rest 450 GB I tried to set a FAT32 windows aprtition. i could not find NTFS option.

I installed the os and after that when I started ubuntu, I could not find the other partition. I checked under DISKS and there it was showing unallocated free space
, which I tried to format. But it is not happening.

What should I do.

---

### Post by Bucky Ball on 2013-12-02
You are missing one important thing: a 2Gb /swap partition at the end of the drive. Also, NTFS is there. I would strongly advise against using a FAT32 partition.

---

### Post by fantab on 2013-12-02
It is a good idea to keep your 'system files' and DATA separated. 
25Gb for Ubuntu systemfiles or '/' is plenty
100Gb for Linux DATA or /home
2-4Gb Swap
All the remaining GB for NTFS #Do NOT use FAT32.

Also ext3 is old, use ext4 filesystem.

Use Gparted from ubuntu live DVD/USB, create your partitions first and then when installing use "something else" option to select partitions for install.

---

### Post by vs-punn on 2013-12-02
There is no option for NTFS. 
The following options are being shown:
Ext4 journaling,
ext3 journaling,
ext2 file system,
reiserFS ,
btrsfs journaling,
JFS,
XFS,
Fat16,
FAT32,
swap area,
Physical volume for encryption,
do not use

---

### Post by Bucky Ball on 2013-12-02
That's weird. Maybe just leave it as free space and create it with Gparted once installed.

(Just checked and it's there in Gparted. Why its weird is because I thought Gparted was used for the partitioning during the install also.) :-k

---

### Post by vs-punn on 2013-12-02
The laptop is ACER Aspire E-1, which came with preloaded Linplus (command mode).

I tried installing 64bit , but it did not go through, whereas the spec. say Windows 8 64bit can be installed.

---

### Post by Bucky Ball on 2013-12-02
For clarity:

> **vs-punn said:**
> 
I installed the os and after that when I started ubuntu, I could not find the other partition.

So do you have Ubuntu installed because in the first post you say you installed Ubuntu and were seeing the 450Gb where the FAT partition should be as free space?

Could you provide the output of:

```
df -T
```

---

### Post by fantab on 2013-12-02
Try the 64bit again, it should work. Perhaps the 'burn' didn't go well. Were there any error messages when you tried 64bit?

---

### Post by oldfred on 2013-12-02
While the installer uses most of gparted, it does not offer the NTFS partition as an option. But gparted does, so often better to partition in advance with gparted to create the partitions you want. You still have to use manual install to specify format as ext4, mount as / (root) etc for every system partition. 
Generally better to make NTFS partition first partition on drive. 
Also generally better to have smaller system partitions for both Windows & Ubuntu as it is slightly more efficient and then have larger data partitions like /mnt/data or /home. If dual booting a shared NTFS data partition like /mnt/shared helps avoid issues that writing into the Windows system partition may create.

---

