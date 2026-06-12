---
title: "UBUNTU Grub install /target/ failure and question about partitions."
date: 2018-12-24
forum: Installation &amp; Upgrades
---

### Post by penciltester on 2018-12-24
So I've have been distro hopping trying to figure out what I like best  and what I find to work will with my Surface Pro 3. I decide to to go  back to Ubuntu 18.04. Unfortunately I started getting this error when I  try to install it "The 'grub-efi-amd64-signed' package failed to install  into /target/". I had never had this issue before. I was choosing the  option to erase the disk and do a fresh install. No other operating  systems on the device. So I formatted the disk. Tried again. Same issue.  Is there some kind of partition lurking around that wont show up in  GParted that I have to erase or do i have to manually set up partitions  since I formatted the drive? I'm kinda confused. 

I did run Boot  Repair Tool. It just booted into a grub terminal afterwords. Then I  tried to reinstall ubuntu, gave me the same error. Ran BRT again. It  gave me an error about a locked ESP but when I rebooted it loaded Ubuntu  but it had a weird icon "Install RELEASE".

What the heck is going on?

Thanks and Happy Holidays.

---

### Post by oldfred on 2018-12-24
Error is because it cannot see/mount the ESP.

Locked ESP can be several things.
A few systems have settings in UEFI to lock a partition.
Most of the time it just needs file check.
A few cases, it is so corrupted, you have to backup data, erase partition, recreate ESP and restore data. Generally you then have to update UEFI boot entries.

Check which partition is the ESP.
sudo parted -l
The run this example using sda1, with your ESP.
       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by penciltester on 2018-12-26
Thanks oldfred. I tried that solution but no dice. I booted into a live version of boot repair and saw something odd. In "Disks" it shows my 256gb drive. In Gparted it shows a 238 drive. I went back into disks and did a format of the 256gb drive. Near completion of my format I was given this error. 

[https://imgur.com/a/9ykqiqA](https://imgur.com/a/9ykqiqA)

---

### Post by oldfred on 2018-12-26
It looks like you tried to format the drive, not a partition.
Most tools expect partitions, so formatting a drive can create issues later.

So you need to first create a partition sda1 and then format that.
I prefer gparted. Disks does some strange things sometimes. But it is better than it used to be.

---

