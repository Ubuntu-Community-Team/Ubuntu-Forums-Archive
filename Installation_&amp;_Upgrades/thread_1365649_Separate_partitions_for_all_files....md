---
title: "Separate partitions for all /files..."
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by shuffman37 on 2009-12-27
Whats your guy's take on having all of the /usr../etc folders on their own drives/partitions. I'm familiar with having a separate boot partition and home partition but how much faster would it be having the primary folders on their own drives. Such as /usr, /home, /lib, /boot, /var. I'm planning on having 50gb of one HDD be my home partition and having the other locations being smaller partitions on separate drives. I know it may be a little bit less reliable but would it make things faster to load/boot?

---

### Post by efflandt on 2009-12-27
I doubt if it would make anything faster, the drive has to seek if a different file or different partition.  And you may run into problems with either wasted space or insufficient space if you guess wrong on partition sizes.

It is different if you have a major server with heavy use and different drives for different things, which can be simultaneously accessed faster.  But that is not something you would notice on a home PC.  Enough RAM to cache programs/data would make more sense (and/or faster type of drive).

---

### Post by SecretCode on 2009-12-27
I have not bothered with anything except putting /home on another partition ... and not even that on my current system.

If I were going to partition deeply I might:
- put /boot on its own ~500MB partition. This allows some flexiblity in keeping grub / grub2 isolated from OS changes.
- put /var or at least /var/log and /var/cache on separate partitions - because they can grow a lot.


There are arguments for putting /usr on its own read-only partition ... if you have a lot of logged-in users ... not really relevant to most of us.
I can't think of any good reasons for putting /etc, /lib, etc on separate partitions.

---

### Post by Morbius1 on 2009-12-27
Let me respond to your question by telling you how I set up my machines. I have multiple OS's on my machines and each one of the linux installs are placed in their own "/" partition. No separate /home partition and just one swap and 2 data partitions - one ntfs and one ext3.

Of course I also don't use grub to multiboot so I guess I'm out of the mainstream. :)

---

### Post by Ginsu543 on 2009-12-28
On my main rig, I have my main OS, Karmic, set up on separate partitions on my RAID0 array as follows:

/ = 1 GB
/boot = 100 MB
/usr = 12 GB
/var = 6 GB
/opt = 100 MB
/home = 120 GB
/swap = 1 GB

I chose the various sizes for the partitions after much trial and error and have found the current settings to work really well for my setup. I don't know if having all of them in separate partitions speeds things up during normal operation, but I do think it is faster when the OS does occasional file system integrity checks during boot-up. Instead of checking the entire hard drive (or two large partitions on the hard drive), it can check several smaller partitions. Having said that, I think having all these separate partitions is probably overkill. You only really need separate / and /home directories IMHO.

---

