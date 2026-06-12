---
title: "good partition programs for windows? (attempting hd install)"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by Tigey on 2006-07-01
can anybody reccommend a good partitioner program thats NOT partition magic? my laptop wont let it install for some reason. im going to attempt to use instlux to install on a laptop with a busted cd/floppy drive.

---

### Post by aysiu on 2006-07-01
I know a great partitioning program, but it would require a working CD drive--DiskDrake, which is available on the PCLinuxOS live CD.

---

### Post by Tigey on 2006-07-01
well i can download an iso of a program and mount it with daemon tools, so as long as i dont have to reboot to install it it wont be a problem

---

### Post by aysiu on 2006-07-01
Well, the problem is that you can't really repartition a disk that's in use--that's why most partitioning programs operate as live CDs.

---

### Post by Tigey on 2006-07-01
oh. cause ive done it with partitionmagic before, it rebooted and windows did it in that little window.

---

### Post by aysiu on 2006-07-01
So you rebooted to Partition Magic? That sounds a lot like a live CD, then.

In other words Windows wasn't in use, right?

Partitioning a drive that's in use is usually impossible, and even if it is possible, it's always a bad idea.

---

### Post by reacocard on 2006-07-01
as aisiu said, partitioning a drive in use is never good, even when it's possible. how programs like partitionmagic work is they reboot windows into a mode where it doesn't need to write to the disk, so the disk can be unmounted, then partitioned. partitioning from a livecd is a better option, IMHO. just use gparted on the ubuntu livecd.

---

### Post by Tigey on 2006-07-01
one problem. cd/floppy drive on this laptop is busted. i can get an iso and mount it with daemon tools, but booting from a media is out of the question

---

### Post by rcarring on 2006-07-01
I guess its really a question of how to go about it. If you can get the hard drive out of the latop and use a cable adapter to connect up to a friend's pc, you can partition it quite easily using the Live CD tool in your friends pc.

Or you could borrow a usb/parallel port/pccard cd rom drive.

---

### Post by reacocard on 2006-07-01
ah. then just use something like partitionmagic or disk director. i don't know of any free windows programs that would be able to partition the drive windows is running from. if you have a USB thumbdrive/harddrive you might be able to find something that will run from there.

---

### Post by albatross83 on 2006-07-01
I'd highly recommend AGAINST PartitionMagic, especially for NT5.0 (XP) partitions.  I've had terrible results with PM.

OTOH, I've had outstanding results from [Paragon Partition Manager]("http://www.partition-manager.com/").

Just realize that any time you repartition a drive, total data loss is entirely possible.

---

### Post by Tigey on 2006-07-02
thanks a lot. i'll look into the link. and data loss isnt a concern because theres absolutely nothing on this laptop exept for system stuff

---

