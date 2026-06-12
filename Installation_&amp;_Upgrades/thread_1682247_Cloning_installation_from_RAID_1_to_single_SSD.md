---
title: "Cloning installation from RAID 1 to single SSD"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by vodgut on 2011-02-05
I don't really have a question here, as I've gotten this to work, but I did want to share my experience in case anyone runs into something similar.

Anyway, I have an Asus P6X58D motherboard, which previously I had set up with a hardware RAID 1 volume over 2 1.5TB disks.  These functioned as my boot, install and data disks.  I'm running Lucid 10.04.

I bought a much smaller (64GB) SSD that I wanted to clone the / and /var partitions to.  I'm only using /usr/local and /home as separate partitions, so /usr is on the same partition as / and are moved to the SSD and /usr/local and /home stay on the RAID.  I figure the SSD has better reliability and I can recover / and /usr and /var from a new install in a pinch.  I also have an external 2TB backup disk that really didn't come into play here.

I started off here which is a good guide, and took me through most of it:

[https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)

However, due to my RAID setup, I would skip the System Rescue CD mentioned there and use an Ubuntu LiveCD instead.  LiveCD sees the combined RAID volume and partitions under /dev/mapper which was very useful, whereas the System Rescue CD did not.

The kinks in the matter were 1) having the data disk as RAID and 2) moving from larger to smaller partitions on / and /var

gparted sees the RAID volumes as separate disks, /dev/sda and /dev/sdb so it really doesn't work for manipulating those, though I did find it was possible to copy off of those to other, single disks using gparted.  I selected the partition on /dev/sda or /dev/sdb that I wanted and was able to copy that data off.  Obviously it would have been a bad idea to try and change anything on the single disks within the RAID volume with gparted.

The amount of data in / and /var was small and there was no issue with being able to fit on the smaller partitions, but...

Since the destination partitions were smaller, I had to copy to an interim partition (I affixed an external firewire disk with 80GB capacity to the machine for this) then resize that below the destination, then copy the reduced size one off the interim disk to the SSD partition.  gparted worked for most of this but a couple times bombed out with some stupid errors.  So I fell back to trusty dd to copy the partitions.  Then returned to gparted to resize them.

As an aside, I found this very helpful in monitoring the progress of dd:

[http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html](http://linuxcommando.blogspot.com/2008/06/show-progress-during-dd-copy.html)

After getting the partitions cloned, and editing /etc/fstab on the new disk, it was time to tackle grub.

Annoyingly, the P6X58D, when in SATA RAID mode, only allows you to select RAID volumes as the boot device.  Fine, I'll install grub everywhere including the RAID volume.

My new SSD that I wanted to boot from shows up as /dev/sdc  So, according to the common wisdom that this is the 3rd drive, and the 1 partition is / this should be referred to as (hd2,1) in grub.cfg, right?

Wrong.  Unlike gparted, grub sees the RAID volume as a single disk and does not differentiate between /dev/sda and /dev/sdb.  Those are both combined into (hd0,X).  So then what is /dev/sdc becomes (hd1,X).  I figured this out by doing an 'ls' at the grub command line at boot and matching up what I knew were the partitions on each disk.  grub and gparted see RAID volumes in completely different ways.  Because of this when I was using (hd2,1) I was getting errors at grub boot like:

No such device

and 

Cannot determine C/H/S

Once I realized that I needed to change the (hd2,1) to (hd1,1) I was able to get past this point.

My next problem was that I had incorrect UUID's in /etc/fstab and grub.cfg.  After booting from my older RAID install, and using blkid to find the correct UUID's, I updated grub.cfg and /etc/fstab to the correct values, reinstalled grub to all partitions, including the unified RAID device under /dev/mapper and now all is happy.

The P6X58D takes forever to go through all the boot stuff on the motherboard, but after it gets through that, I'd estimate using the SSD gets me to the login prompt about 3 times faster than using the RAID volume did.

Hopefully someone finds this useful

---

