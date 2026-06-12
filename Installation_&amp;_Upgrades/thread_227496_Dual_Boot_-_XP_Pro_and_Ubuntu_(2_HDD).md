---
title: "Dual Boot - XP Pro and Ubuntu (2 HDD)"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by PseudoEvolution on 2006-08-01
I have a fresh copy of XP pro, Ubuntu 6.06 and 2 clean Hard drives. 80gb (master) and 40gb (slave). 
What I want to do is this: Install XP and Ubuntu on the 80gb hard drive and dual boot them. I want 40gb for each OS and then use the 40gb slave drive to store user files to be shared by both operating systems. 

So how would I go about doing this, safely? Would I just install XP pro first as a regular installation, then install Ubuntu as a second logical (and active) partition, and they will both recognize the additional hard drive automatically? Then install GRUB to the Windows MBR? That's the idea I'm getting from other forums. 
Also, do they both need to be "active partitions" or just 2 logical partitions, with XP being the active. (Also, what do I do about this extended partition that Ubuntu "needs"?)

I have installed various versions of linux before, but never with a dual boot. Atleast not a successful one. I am unfamiliar with the new Ubuntu partitioner, I have only used the one from 4.10. So any lame-man instructions for the new one would be nice.

Thanks!

---

### Post by drosophyllum on 2006-08-01
Ok,install wiindoz first at the end of the drive then install ubuntu in the begining. This will duall boot. Then plug in the slave and use it as a mass storage device. This can be used only if you can find a way to usb plug it, usually ebay has those thingys that you insert a hard drive and it works like a usb stick.

---

### Post by drosophyllum on 2006-08-01
oh and Welcome to UBUNTU!!!!

---

### Post by confused57 on 2006-08-01
Here's an excellent guide for installing Ubuntu:

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

I've seen more posters have success dualbooting if Windows is installed first at the beginning of the drive, then install Ubuntu on a partition located after Windows.
I've only installed Windows XP once, but you'd probably want to install it on a 40 Gb partition at the beginning of the hard drive.
Then the Ubuntu installer will set up partitions on the remaining unallocated space.  You can have up to 4 primary partitions, Ubuntu sets up swap as a logical partition.  Your 2nd storage HD should probably be formatted as FAT32 to share files between Windows & Ubuntu.  Windows should automatically recognize the storage HD, but you'd need to mount the parition in Ubuntu(plenty of guides here to do this).

---

### Post by Megamanic on 2006-08-02
Further to Confused57's exceptionally helpful post (which helped me) there's another nice page linked to from his link on [Partitioning]("http://www.psychocats.net/ubuntu/partitioning.html")
That gives a few options that you may find useful.  For example formatting the 40Gb drive "Ext3" and using [FS-Drive]("http://www.fs-driver.org/") to allow XP to read/write to it, which appeals to me.  You can also partition the 80Gb master drive with a relatively small XP partition, a chunk of shared space and a couple of Ubuntu partitions at the end.  That's probably what I'd do:-

80Gb: 20Gb NTFS "/Windows"; 50Gb Ext3 "/home"; 9Gb Ubuntu "/"; 1Gb Swap
40Gb: 40Gb "/Share"

---

### Post by confused57 on 2006-08-02
> **Megamanic said:**
> Further to Confused57's exceptionally helpful post (which helped me) there's another nice page linked to from his link on [Partitioning]("http://www.psychocats.net/ubuntu/partitioning.html")
That gives a few options that you may find useful.  For example formatting the 40Gb drive "Ext3" and using [FS-Drive]("http://www.fs-driver.org/") to allow XP to read/write to it, which appeals to me.  You can also partition the 80Gb master drive with a relatively small XP partition, a chunk of shared space and a couple of Ubuntu partitions at the end.  That's probably what I'd do:-

80Gb: 20Gb NTFS "/Windows"; 50Gb Ext3 "/home"; 9Gb Ubuntu "/"; 1Gb Swap
40Gb: 40Gb "/Share"
Thanks, I like your partitioning plan better for the OS hard drive...probably wouldn't matter which to use for the storage drive(ext3 might be better, no 4 Gb file limit, less fragmentation).  Lots of good information on the psychocats.net site, as well as Herman's site:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
(It's not just a dualboot site, there's a lot of good information about grub, configuring xserver, uninstalling Ubuntu,etc...a good read)
Later, when you want to install programs:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

These are all sites maintained by members of this forum.

---

