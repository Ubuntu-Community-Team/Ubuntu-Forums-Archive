---
title: "GRUB Refuses to Install"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by TruthElixirX on 2007-01-15
I've tried about 20 times to install Ubuntu with no luck. I finally wound up in the IRC channel, where I eventualy got some help from someone named "adaptr". He walked me through a ton of stuff. He or I had to leave though, so we got interuppted.

We finally figured out that my hard drive isn't writing GRUB correctly. Something about MBR or some such as well. 


I'm not sure what to do. I've done a run though of the wikipage that tells you how to install GRUB, and it doesn't work. I've replaced the cable on my HDD, at the suggestion of adaptr, but nothing changed. 

After installing Ubuntu and rebooting, upon the reboot I get this "Please insert boot media and press a key, or reboot."

I have also tried sticking in the live CD, and pressing "Boot from local disk" but it doesn't do anything.

Its a brand new HDD that is in a computer that used to have XP installed on it, til the old HDD failed.

I do not have access to a computer to burn the super grub CD, but if that is my only option then I'll have to figure it out somehow...

---

### Post by hal10000 on 2007-01-15
First thing I would try is to boot vour live cd and try to see whats going on.

1. open a terminal window and type sudo fdisk -l

2. try to mount the partition where your ubuntu resides:
sudo mount -t ext3 /dev/yourpartition /mnt

It looks like something went wrong either when partitioning or when installing grub

You may post the outputs of the above commands so peole here can see whats going on.

---

### Post by TruthElixirX on 2007-01-15
[quote=terminal]Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30213   242685891   83  Linux
/dev/hda2           30214       30401     1510110    5  Extended
/dev/hda5           30214       30401     1510078+  82  Linux swap / Solaris
[/quote]

[quote=terminal]
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda2 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda5 /mnt
mount: /dev/hda5 already mounted or /mnt busy
mount: according to mtab, /dev/hda1 is already mounted on /mnt
[/quote]

That is what I got.

---

