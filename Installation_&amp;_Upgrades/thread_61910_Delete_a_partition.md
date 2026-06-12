---
title: "Delete a partition"
date: 2005-09-02
forum: Installation &amp; Upgrades
---

### Post by daniminas on 2005-09-02
Hi, i'm a new user... and this is the history: 
I been installed ubuntu in a partition in the harddisk because i've a lot of data stored... So, everything it's ok, but now i been moved the data to the linux partition... so, my old partition have only unneccesary files saved.. my idea is delete all the data in that partition and change the filesistem to a linux-fs (actually is a 'dos' partition).. Thanks for any help in tellme how can i do that..


Daniel

pd->sorry my enlgish...

---

### Post by teebones on 2005-09-02
Let me get it clear.
You want to delete the partition on wich the old data WAS stored, and create a new linux partition from it?
(because you moved the data to another partition?)


WARNING! 
If you do this wrong, it could ruin your installation and create DATALOSS permanent!! 
CAUTION NEEDED!


Still here? good!
--------------------------

Well... you could simply reformat it to the filesystem you want.

Firstly you need to know the linux "drive" for this partition:

sudo fdisk -l  (that a -L in non-capital)

this will output the drives (partitions) known by linux.
(alternatively you could do: sudo df -h (this outputs the mounted partitions and the size of them))

Anyway.. if you know wich one it is (e.g. /dev/hdc3), you could format this partition in a filesystem of your liking.


The most common linux filesystems:

for ext2 filesystem:

sudo mke2fs /dev/thedevicehere (example: sudo mke2fs /dev/hdc3)

for ext3 filesystem:

sudo mke2fs -j /dev/thedevicehere (example: sudo mke2fs -j /dev/hdc3)

I can't stress this enough, USE CAUTION!

cheers.

---

### Post by twowheeler on 2005-09-02
If you are truly sure you are ready to dump the data on that partition, you just have to do a mkfs on it.  Suggest you read "man mkfs".  Basically you decide what kind of file system you want, unmount the partition, and then run 'mkfs -t ext3 /dev/hd??' for a ext3 file system.  That could be reiserfs, or ext2, or whatever.  Then mount the partition and you are ready.  If you put the appropriate mount information in /etc/fstab then it can be mounted automagically.

---

### Post by teebones on 2005-09-02
[QUOTE=twowheeler]If you are truly sure you are ready to dump the data on that partition, you just have to do a mkfs on it.  Suggest you read "man mkfs".  Basically you decide what kind of file system you want, unmount the partition, and then run 'mkfs -t ext3 /dev/hd??' for a ext3 file system.  That could be reiserfs, or ext2, or whatever.  Then mount the partition and you are ready.  If you put the appropriate mount information in /etc/fstab then it can be mounted automagically.[/QUOTE]
 You might use "sudo" in front of the suggested commands (as it is root only commands)

---

