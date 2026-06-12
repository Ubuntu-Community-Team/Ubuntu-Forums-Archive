---
title: "Recovering Logical Volme from old machine"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by JetPack on 2010-11-14
I had an old PC running as a file server which had been hacked together with old spare parts. There were two hard disks that had several partitions on each and I had combined one partition off each disk into a Volume Group using LVM.

I upgraded to a better server (now with one HD dedicated to the system and two 1TB HDs for data and backup).

Time passed.... (over a year). The old server is now in Silicon Heaven with all the calculators. (<----Red Dwarf)

However, I still have the disks and I now want to try to get the data off the LVs on those two HDs.

I just had a look at the disks using LVM2 on an Ubuntu 9.10 system and it sees the partitions formatted as LVs but doesn't seem to let me do anything with them. I had a go with LVM at command line as well but I don't know enough (but I got the name of the VG).

Anyone able to provide some guidance, please?

Thanks in advance.

---

### Post by searchfgold6789 on 2010-11-14
There is software called Testdisk that will let you get the data off of the hard disks. The favored method of using this software is booting from a Linux live CD, installing it, and running it as root. Then a search for lost partitions is initiated and the files can be copied by the user to a different hard disk or some other external media.
Then you can put the data back on the hard disks and do what you want with them.

There is a good HowTo guide [_**here**_]("http://tldp.org/HOWTO/LVM-HOWTO/") explaining LVM.

---

### Post by JetPack on 2010-11-14
@search

Thanks very much for the post. I had a play with TestDisk and it's a good tool but it didn't move me forward as the HDs in question are fully working and the file systems are fine. It's just that the partition used to be part of an LV which means that it can't be mounted and handled like a normal partition.

I had already read the LVM guide you pointed to, which is also good, but it's really for setting up LVs and it doesn't help me with my need to re-attach an orphaned partial LV.

What I need is some guidance on combining a "lost" volume from a volume group to create a working LV (even if it means losing a few files).

Cheers!

---

