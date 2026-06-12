---
title: "Disk partitioning fails during installation"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by uptempo on 2007-09-07
Hi.  I'm installing Ubuntu 7.04 on my Dell Latitude D600 (Pentium M, 1.8GHz, 2GB RAM, latest BIOS).  Already have Win XP installed so am setting up a dual boot.  The disk partitioning is failing.  I select the option to resize the main partition and use the free space.  Have tried this with the recommended partition size (88%, 67GB) and with the minumum size (77%, 56GB).  These numbers surprised me because I have a 75GB hard disk with only 19GB free.  In both cases I get the following error.

An error occurred while writing the changes to the storage devices.  The resize operation is aborted.

From searching the forums, it looks like I may need to use gparted or some such to partition the hard disk prior to installing Ubuntu.  Maybe it will work if I partition manually, though am a bit gunshy since I'm brand new to all of this.

So, two questions:

1. Is it really the case that I need to partition the disk separately from the install?  

2. How can it be that the installer recommends a partition of 67 GB when I have only 19 GB free?


thanks,
michael

---

### Post by merlinus on 2007-09-07
Maybe because the partitioner is telling you the size for your windows partition?

BTW, did you delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

-merlin

---

### Post by uptempo on 2007-09-07
> **merlinus said:**
> Maybe because the partitioner is telling you the size for your windows partition?

BTW, did you delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

-merlin

I did all that except setting the virtual page size to zero, which is a good idea.  I'll do that and refrag overnight.

Am still not clear on the partition size.  The partitioner was suggesting I create a new partition using 88% of my hard disk, or approximately 67 GB.  The minimum it would let me choose was 56 GB.  Since there is only 19 GB of free space on my hard disk, that's not going to work.  

Thanks for the feedback,
michael

---

### Post by merlinus on 2007-09-07
Another option is to use gparted live cd to set up the partitions manually before install.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by uptempo on 2007-09-07
> **merlinus said:**
> Another option is to use gparted live cd to set up the partitions manually before install.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

Yes, that looks like what I'll need to do.  Thanks for your help.

michael

---

### Post by merlinus on 2007-09-07
You are welcome, and let us know how it goes.

-merlin

---

### Post by uptempo on 2007-09-09
Just to close the loop, letting you know that I was able to repartition with gparted and successfully install 7.04.  Thanks a lot for your helpful advice.

m.

---

### Post by merlinus on 2007-09-09
Excellent -- glad to hear it!

---

