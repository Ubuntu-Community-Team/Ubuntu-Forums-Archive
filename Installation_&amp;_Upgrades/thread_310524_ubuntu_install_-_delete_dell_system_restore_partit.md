---
title: "ubuntu install - delete dell system restore partition?"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by mcs101 on 2006-12-01
I'm a new ubuntu user in the process of installation.  I'm attempting to partition my hard drive (160 GB SATA on a new Dell Dimension) so that I can dual boot Ubuntu and Windows XP.  There's an existing 6 GB fat32 partition which I *think* is used for Dell's system restore.  Currently none of the 6 GB are used. Should I delete this partition or leave it?  

I've tried searching the forums for an answer, but see mixed advice (some say it's useless, some say it's crucial).

---

### Post by Ashrael on 2006-12-01
depends on if you ever want windows back....if not: use it...

---

### Post by dbott67 on 2006-12-01
The partition contains some diagnostics for hardware that you might require in order to receive an RMA for warranty and support purposes.  For example, the partition has a hard drive utility that the support personnel would ask you to run in order to check the status of the hard drive.

It may also contain the original OS image, included applications and hardware drivers if you ever want to restore the original OS.

I would recommend using a "Drive Imaging" application (Ghost, Drivesnapshot, etc.) to create an image of the partition and then burn it to DVD.

-Dave

---

### Post by mcs101 on 2006-12-01
there's also a 40 MB fat16 partition.  I read somewhere that that's used for diagnostics.
I don't have time right now to burn a DVD (first have to go buy the DVDs ;) .
I think I'll leave the partition in for now... just to play it safe.

---

### Post by dbott67 on 2006-12-01
Good idea... better safe than sorry. :)

-Dave

---

