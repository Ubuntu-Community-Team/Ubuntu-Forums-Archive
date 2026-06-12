---
title: "Vista on sda doesn't like Ubuntu on hda"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by jerrybme on 2007-02-12
I didn't find this issue when searching for it, so I thought I'd post my problem & solution:

I've had Ubuntu and Windows XP living happily on my desktop for over a year. I recently decided to try Vista and my problems began:

My original setup:

/dev/hda1: ubuntu (Edgy)  199 gigs ext3 bootable
/dev/hda2: swap
/dev/hdb1: storage  150 gigs vfat
/dev/sda1: Win XP Pro 70 gigs ntfs bootable

Using the:
map (hd0) (hd1)
map (hd1) (hd0)
commands in Grub this worked fine the ntloader & boot.ini are all on the sda drive.

To install Vista, I disabled the hda & hdb drives so that vista would make the sda drive bootable and not touch the MBR of my ubuntu drive. All went well after the install and I enabled the hda & hdb drives. Grub came up and I was able to boot into Vista.

However when I wanted to return to Ubuntu and  I selected it from Grub, I got an error:
```
BusyBox v1.1.3( Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' dor a lst of built-in commands.

/bin/sh:can't access tty; job control turned off
```
Using my Edgy Live CD I was able to run fsck.ext3 on /dev/hda1 and it found multiple errors relating to partition table and other too numerous to list. They were all fixable and I booting into Ubuntu.

I have since found that every time I loaded Vista it was messing up the partition table of hda1 requiring me to run fsck.ext3 from the Live CD to fix the problem.

I know the simple answer is to dump Vista ;) But I found that the problem was fixed by adding a new partition at the start of hda that Vista could understand. So I added a 2 gig fat32 partition to hda and moved Ubuntu to the second partition. Now they are getting along better and I'm able to go back and forth.

Current setup is:

/dev/hda1 2 gig fat32 bootable
/dev/hda2 Ubuntu 197 gig ext3 
/dev/hda3 swap
/dev/hdb1 storage 150 gig vfat
/dev/sda Vista 70 gig bootable

Hopes this helps someone.

Cheers,
Jerry

---

