---
title: "fat32 drive goon after upgrade???"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by bradc28 on 2008-05-12
I upgraded to 8.04 and had problems during the upgrade. Since I had my home directory copied off I figured I could put anything I need back and did a fresh install. 

Somewhere along the lines, I may have told it my data drive (pics, mp3s, kid's first steps video) was the install drive but don't think I did. Heron is installed on the correct drive now but still can't mount that old drive which I believe was originally a fat32 drive.

Is there any way I can pull the data off this drive and move it somewhere else? I tried mounting this in a USB drive enclosure in a windows host and it is unreadable, I also tried mounting it as is in Ubuntu without success. Since the stuff below is so messed, I am guessing there is no data written to the drive yet so I may be able to save it. Something along the lines of rewriting the superblock or something.

The drive I am concerned with is sdb which I believe was one large fat32 partition before.

Here is the info:
fdisk -l output
Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00046765

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       23576   189374188+  83  Linux
/dev/sdb2           23577       24321     5984212+   5  Extended
/dev/sdb5           23577       24321     5984181   82  Linux swap / Solaris

brad@connery:~$ sudo mount -t ext3 /dev/sdb1 /testmount/
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg says:
[133950.122080] VFS: Can't find ext3 filesystem on dev sdb1.

brad@connery:~$ sudo dumpe2fs /dev/sdb1 |grep -i superblock
dumpe2fs 1.40.8 (13-Mar-2008)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

Thanks for the help, Brad

---

### Post by bobnutfield on 2008-05-12
> /dev/sdb1 1 23576 189374188+ 83 Linux
/dev/sdb2 23577 24321 5984212+ 5 Extended
/dev/sdb5 23577 24321 5984181 82 Linux swap / Solaris

If sdb was a fat32 disk, it isn't now.  There are commands available for restoring parttion tables superblocks, but if your data was on a fat332 drive, this doesn't look good.  There are a number of posts on the Linux Questions.org forum about this issue.  You might take a look there.

Bob

---

### Post by bradc28 on 2008-05-15
The world is good thanks to Photorec and a closeout deal on 500GB drives.

I downloaded photorec & testdisk the other day. Once my new 500GB drive arrived I plugged it in, fired up photorec and it just started sucking MP3s, avis, mpg, jpg and just about everything else off of the old drive onto the new one.

I chose the no partition table option so it would not try to make sense of it. Great tool and thanks to those who replied to my post.

The only thing is is does not get the file names so I am going to look for an mp3 tag/file writer and spend hours viewing home movies, car races and porn while configuring my new NAS. I guess life isn't that bad after all.

---

