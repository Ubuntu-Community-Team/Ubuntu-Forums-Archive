---
title: "Vista defrag borks ubuntu"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by Cybyrsoldat on 2007-02-23
I have both vista and ubuntu installed on the same machine. I ran vista's defrag and it somehow screwed my ubuntu partitions. Is there anyway to make ubuntu partitions invisible in windows? I can't see them in computer but I can see them in disk management. Grub gives me an error 17.

---

### Post by louis_nichols on 2007-02-23
Typical. There's nothing you can do, unfortunatelly. Disk Management will display all partitions on the HDD. The ones that don't have recognizable filesystems tto windows, will be of type unknown. However, a defrag should have no influence on those. A defrag should just take care of the partition it was started for. Although, the ways of Microsoft are many...

---

### Post by Cybyrsoldat on 2007-02-23
I reinstalled Ubuntu to salvage things. I just installed it not too long ago anyways so nothing really lost. Grub is up and running again and I've discoverd that vista defrag can be run from the command line on a single volume.

BTW, if you run defrag normally, it doesn't let you choose the volume, it just does a full sweep. Guessing that had something to do with screwing even partitions it doesn't recognize over. Both Ubuntu partitions show up as primary partitions in disk management... I ran defrag assuming it wouldn't affect the Ubuntu partitions but guess I was wrong.

---

### Post by louis_nichols on 2007-02-23
In XP, the defrag utility displays a GUI that lets you choose the volume to defrag. They obviously thought to prevent ppl from dual booting with other OS's.

I would sue them for anti-competitive measures for such a thing, but hey! That's just me.

---

