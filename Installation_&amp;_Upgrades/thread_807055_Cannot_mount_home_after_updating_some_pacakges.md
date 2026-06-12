---
title: "Cannot mount /home after updating some pacakges"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by jerzyUs on 2008-05-25
Hi,

I updated some Ubuntu 8.04 packages earlier today using the update manager (I don't know which ones; is there a log anywhere?).  My /home partition now cannot be mounted.

On startup, there is an error displayed.  It looks something like this (since I only have command line access on my laptop, I am having to write the details up on my wife's laptop):



* A file system check failed
A log is being saved in /var/log/fsck/checkfs if that location is writable.  Please repair the filesystem manually.



The contents of /var/log/fsck/checkfs is:



fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Filesystem revision too high while trying to open /dev/sda6.  The filesystem revision is apparently too high for this version of e2fsck. (Or the filesystem superblock is corrupt).

/dev/sda6:
The superblock could not be read or does not describe a correct ext2 filesystem.  If thee device is valid and it really contains an ext2 filesystem (not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8



According to blkid, /dev/sda6 has TYPE="ext4".  Does this mean my partition has been updated from ext3 to ext4?  If so, why and what do I do to fix it so that /dev/sda6 can be mounted again?

Cheers,
Dave.

---

### Post by jjgomera on 2008-05-25
maybe a problem with /etc/fstab, for same reason change the uuid for that partition, like [here]("http://ubuntuforums.org/showthread.php?t=291890&page=2")
uuid in fstab must be equal than the uuid for each partition of command **blkid**, if isn't, you must change uuid in fstab

---

### Post by jerzyUs on 2008-05-25
> **jjgomera said:**
> maybe a problem with /etc/fstab, for same reason change the uuid for that partition, like [here]("http://ubuntuforums.org/showthread.php?t=291890&page=2")
uuid in fstab must be equal than the uuid for each partition of command **blkid**, if isn't, you must change uuid in fstab

Sorry, I should have mentioned that I have already tried this, and the uuid matches.

I tried mounting /dev/sda6 (my /home partition) via the 7.04 live CD, and received this message in dmesg:

EXT3-fs: sda6: couldn't mount because of unsupported optional features (8000800).

---

### Post by jjgomera on 2008-05-25
have you tried to run fsck manually for that partition?

---

### Post by jerzyUs on 2008-05-25
> **jjgomera said:**
> have you tried to run fsck manually for that partition?

Here is the output of running fsck manually:


ubuntu@ubuntu:/media$ sudo fsck /dev/sda6
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Filesystem revision too high while trying to open /dev/sda6
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


and the output of e2fsck:

ubuntu@ubuntu:/media$ sudo e2fsck /dev/sda6
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Filesystem revision too high while trying to open /dev/sda6
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)


The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by jjgomera on 2008-05-25
what's the output of command **tune2fs -l /dev/sda6** ?

you can prove too with e2fsck -b xxxx where xxxx is

tune2fs -l /dev/sda6 | grep "Block size"

---

### Post by jerzyUs on 2008-05-25
> **jjgomera said:**
> what's the output of command **tune2fs -l /dev/sda6** ?

you can prove too with e2fsck -b xxxx where xxxx is

tune2fs -l /dev/sda6 | grep "Block size"


Here is the output of the tune2fs command:

ubuntu@ubuntu:/media$ sudo tune2fs -l /dev/sda6
tune2fs 1.40-WIP (14-Nov-2006)
tune2fs: Filesystem revision too high while trying to open /dev/sda6
Couldn't find valid filesystem superblock.

It seems like the filesystem is not happy :-(

---

### Post by jerzyUs on 2008-05-26
> **jerzyUs said:**
> Here is the output of the tune2fs command:

ubuntu@ubuntu:/media$ sudo tune2fs -l /dev/sda6
tune2fs 1.40-WIP (14-Nov-2006)
tune2fs: Filesystem revision too high while trying to open /dev/sda6
Couldn't find valid filesystem superblock.

It seems like the filesystem is not happy :-(

Well I sorted out my problem :-).  Here's how I did it:

1) sudo mke2fs -n -j /dev/sda6
2) sudo e2fsck -b id /dev/sda6
where id comes from some of the info provided my mke2fs
3) Answered yes to all of the questions about block/inode size.

I then backed up all of the remaining files that I had not backed up, and all is now as it was.

---

### Post by jjgomera on 2008-05-26
happy end :)

---

### Post by jerzyUs on 2008-05-26
Yup. :-)

---

