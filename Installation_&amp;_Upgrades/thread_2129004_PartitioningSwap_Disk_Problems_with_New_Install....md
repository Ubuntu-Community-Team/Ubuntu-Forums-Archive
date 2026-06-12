---
title: "Partitioning/Swap Disk Problems with New Install..."
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by artphotodude on 2013-03-25
Am attempting to install on a newer laptop, but I keep running into problems with 12.04s install partitioner not being accurate to 1MiB.  Went into the 'Try Ubuntu' section to run Gparted to get the main and swap partitions done, but then I can't install on them because the mount-point can't be set, except with the outdated install partitioner.  Is there any other way to set the mount-point on the drive so I can install on it?  

Tried it after the fact, but my swap partition keeps failing.  If it were a desktop, would just use a swap-file, but on a laptop, really need it to be encrypted.

Many Thanks for Any Help!

---

### Post by ibjsb4 on 2013-03-25
I guess I don't understand.

Why can't you just create free space on your drive and let the installer create swap and mount for you.  The installer will detect the free space and give you the option to install ubuntu to it.

---

### Post by artphotodude on 2013-03-25
> **ibjsb4 said:**
> I guess I don't understand.

Why can't you just create free space on your drive and let the installer create swap and mount for you.  The installer will detect the free space and give you the option to install ubuntu to it.

Because you can't use an encrypted swap-file without risking the  system's stability (or at least I have read that on dozens of posts  here).

---

### Post by ibjsb4 on 2013-03-25
Guess I have not seen those dozens of posts :)

Good luck

---

### Post by deadflowr on 2013-03-25
After setting the partition sizes, did you go to the 'something else' option in the installer.

I would use that, then click on the partition to have the main Ubuntu installation on and click 'edit.
Then mark the mount point as /.
Swap doesn't need to be mounted.

---

### Post by artphotodude on 2013-03-25
> **deadflowr said:**
> After setting the partition sizes, did you go to the 'something else' option in the installer.

I would use that, then click on the partition to have the main Ubuntu installation on and click 'edit.
Then mark the mount point as /.
Swap doesn't need to be mounted.  
I see what you mean, but since I have to reformat to add the '/' is it going to be set to the nearest MiB or nearest Cylinder?  I WISH the full Gparted options were there.

---

### Post by deadflowr on 2013-03-25
> **artphotodude said:**
> I see what you mean, but since I have to reformat to add the '/' is it going to be set to the nearest MiB or nearest Cylinder?  I WISH the full Gparted options were there.

.

Just set the mount point for the root partition.
No need to format it, if it's already set up.

Make sure the file system for the swap is set to Linux-Swap.

---

### Post by oldfred on 2013-03-25
I do not think you have an issue unless you use an old (over 2years old) copy of gparted or the installer. Also if you encrypt /home then gparted will not see swap as swap is also encrypted.

 Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

   First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by artphotodude on 2013-04-06
> **deadflowr said:**
> .

Just set the mount point for the root partition.
No need to format it, if it's already set up.

Make sure the file system for the swap is set to Linux-Swap.


This doesn't work.  It keeps pestering me about "No Mount Point" being set, and there isn't a way to set it without allowing the installer to mess with my existing partition and thus loosing the 'nearest MiB' accuracy.

---

### Post by artphotodude on 2013-04-06
> **oldfred said:**
> I do not think you have an issue unless you use an old (over 2years old) copy of gparted or the installer. Also if you encrypt /home then gparted will not see swap as swap is also encrypted.

 Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

   First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

Tried it, but the disk utility keeps telling me that the the disk is "not clean", and whenever I create the swap file partition it always gets misaligned and fails to mount after restarting a couple of times.  The installer simply needs the 'nearest MiB' option built in, or there needs to be a way to set the mount point to an already partitioned drive from the installer -without allowing the installer to futz with the partition scheme.  There appears to be NO WAY to create partitions in GParted and then install onto it.    Too Bad. :(

---

### Post by oldfred on 2013-04-06
I have always created partitions with gparted, then use manual install, choose my partition, set it to / (root), format to ext4 and it installs. I already have swap so it finds that. And I have all my data in other partitions so I usually am installing in just a 25GB partition.

---

### Post by artphotodude on 2013-04-07
> **oldfred said:**
> I have always created partitions with gparted, then use manual install, choose my partition, set it to / (root), format to ext4 and it installs. I already have swap so it finds that. And I have all my data in other partitions so I usually am installing in just a 25GB partition.

So if I format the partition, I will not be adjusting the partition boundary itself?

---

### Post by oldfred on 2013-04-07
If you run this and all the starts are divisable by 8, then there is nothing to worry about. Extended partition does not apply as you do not write to it directly but only the logicals in it which should be aligned.

sudo parted /dev/sda unit s print

---

### Post by artphotodude on 2013-04-11
> **oldfred said:**
> I have always created partitions with gparted, then use manual install, choose my partition, set it to / (root), format to ext4 and it installs. I already have swap so it finds that. And I have all my data in other partitions so I usually am installing in just a 25GB partition.



Thanks so much! This seems to have worked!! :D

---

