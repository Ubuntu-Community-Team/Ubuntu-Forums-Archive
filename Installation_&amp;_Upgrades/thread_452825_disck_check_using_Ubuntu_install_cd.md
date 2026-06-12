---
title: "disck check using Ubuntu install cd"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by ngdias on 2007-05-23
It seems its not possible to list contents or use in anyway the local hard drives when booting the computer from the Ubuntu install CD. I'd like to know if there is a way to run for example fsck on a local hard drive using the terminal on the Ubuntu CD.

---

### Post by taurus on 2007-05-23
```
sudo fsck /dev/sda1
```
Assuming /dev/sda1 is the partition you want to fsck.

---

### Post by ngdias on 2007-05-23
My Ext3 partitions are actually sda3 and sda4. sda1 is NTFS and sda2 is SWAP.

I can-t mount any hard drive partition while running the boot CD.

This is what I get from sudo fsck /dev/sda(1-4)>

fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda3


The thing is, something went very wrong today and my Linux partitions are not working and Im trying to fix them... I can recover the data using Windows software, but what I really want is to fix (repair) everything so I don-t have to back up and try a format and fresh install.

---

### Post by ngdias on 2007-05-23
Something I just tried

```
sudo fsck /sys/block/sda/sda4
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Is a directory while trying to open /sys/block/sda/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```


AND

```
sudo e2fsck -b 8193  /sys/block/sda/sda4
e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Is a directory while trying to open /sys/block/sda/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

---

### Post by ngdias on 2007-05-24
can anyone please help? I can't acess my /home partition at the moment....

---

### Post by ngdias on 2007-05-24
Does the installation CD come with any disk repair/analyse tools?

---

### Post by psusi on 2007-05-24
That's because /sys/block/sda/sda4 is not a block device. 

What is the output of:

```
sudo fdisk -l
```
and
```
sudo dd if=/dev/sda3 of=/dev/null count=1
```

---

### Post by ngdias on 2007-05-24
> **psusi said:**
> That's because /sys/block/sda/sda4 is not a block device. 

What is the output of:

```
sudo fdisk -l
```
and
```
sudo dd if=/dev/sda3 of=/dev/null count=1
```

--------------------------------

1st: I think its only detecting the live cd (heres why my 1st post)

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 125 MB, 125682176 bytes
255 heads, 63 sectors/track, 15 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          16      122705    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(14, 254, 63) logical=(15, 71, 25)
```

--------------------------------

2nd:

```
ubuntu@ubuntu:~$ sudo dd if=/dev/sda3 of=/dev/null count=1
dd: reading `/dev/sda3': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000596408 seconds, 0.0 kB/s
```

I-m going to try using another linux boot cd and see what happens when issuing these commands.

---

### Post by ngdias on 2007-05-24
Using another boot disk I can read the hard drive. Next are some screenshots of the results:

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1103.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1105.jpg[/IMG]

[IMG]http://i192.photobucket.com/albums/z183/ngdias/IMG_1106.jpg[/IMG]

---

### Post by psusi on 2007-05-24
After the dd command fails, check the output of dmesg for more specific errors.  They should appear at the end of the listing.  Also the fdisk -l should have shown sda but did not.  Then you show it does.  Am I correct in assuming that that the second was from another boot cd and the first was from ubuntu?

What if you run fdisk -l /dev/sda from ubuntu?

---

### Post by ngdias on 2007-05-25
> **psusi said:**
> After the dd command fails, check the output of dmesg for more specific errors.  They should appear at the end of the listing.  Also the fdisk -l should have shown sda but did not.  Then you show it does.  Am I correct in assuming that that the second was from another boot cd and the first was from ubuntu?

What if you run fdisk -l /dev/sda from ubuntu?

1. What is 'the output of dmesg'? all output produced by the command was in the photo-screen - you can see the prompt again at the bottom.

2. 'Am I correct in assuming that that the second was from another boot cd and the first was from ubuntu?' Yes. You get a clue of that by looking at the command prompt.

3. After 3 days going about with several boot CDs, several attempts to run fsck and windows-based utilities, I got it working again. What I did:

    a. Loaded the Ubuntu live cd
    b. At the terminal, typed:
```
sudo fsck.ext3 -fv dev/sda4
```
    c. Said yes to a correction to the superblock once and yes to several corrections for empty blocks/sectors/whatever.

4. As everyone can see in the screenshots, i tried that same magic command using another boot CD and got the 'recovering journal' message - same as when I tried loading Ubuntu from the hard drive - and I/O errors right after. I don't understand how that didn't work all those other tries and this one using the Ubuntu live CD solved the problem...

---

