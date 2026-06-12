---
title: "how do i increase disk space in / File System?"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by ypkhoon on 2010-04-08
i just installed ubuntu 9.10 onto my windows vista laptop. i ran ubuntu update manager but it tells me i'm low on disk space. system monitor tells me that i still have 50.2 GB of space but the problem is that i only have 68 MB left in my / File System. how can i increase disk space in / File System? please help!

---

### Post by dominiquec on 2010-04-08
Boot using a LiveCD and run gparted.  Be careful, though: back up all important files first.  You could potentially hose the contents of your disk.

Read gparted instructions very carefully.

---

### Post by ypkhoon on 2010-04-08
what is LiveCD? i already have gparted on my system. i only have one HDD on my laptop, partitioned into 2 drives. if i create a new partition, i will erase everything?

---

### Post by dominiquec on 2010-04-08
LiveCD is the standard Ubuntu desktop CD.

Reason why you need to use gparted from a LiveCD is because you cannot resize partitions which are active.

Here's my own experiences: [http://ubuntuliving.blogspot.com/2008/05/partitioning-misadventures-part-1.html](http://ubuntuliving.blogspot.com/2008/05/partitioning-misadventures-part-1.html)

That said, I really do suggest you read up on the gparted instructions.

---

