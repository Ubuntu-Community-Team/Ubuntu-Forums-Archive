---
title: "guided partitioning does not work :("
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by weijie90 on 2005-04-19
i have an ntfs partition running winxp, three other fat32 partitions  for data and 10 gb of free unused space.

however, it shows up as unusable in the ubuntu installer. i can only see information about it when i select it using manual partitioning, and the guided partitioner says that it cant be used, "mabye because there are too many primary partitions". it is the largest continuous free space on my disk.
im running the i386 version. i have an intel pentium 4 1.6ghz . (dell 4300s)

please help me. thanks!

---

### Post by tmowerman on 2005-04-19
Traditionally, it was only possible to have four partitions on a disk.  Obviously, people soon began to need more, and a scheme was invented to allow this.  It had to remain backwardly compatible with the old scheme.  

A notion of primary and extended partitions was created.  You were (and still are) allowed four primary partitions.  If you needed more, you create an extended partition, then create more partitions inside it.

Unfortunately, you have four primary partitions.  The simplest solution would be to backup the smallest one, and delete it.  You can then create an extended partition and add the fat partition, and ubuntu partition and swap within this.  You may need to make sure the 3 partitions are at the front of the disk, so you have a continuous block of free space.

To simplify this, you might want to try qtparted on the knoppix live cd, or also parted from a console window, if that is not too scary!  

It may be possible to rewrite the partition table without affecting the data, but you will have to hope someone who knows more than me answers!  I am having trouble with partitioning too.

Tim

---

### Post by weijie90 on 2005-04-19
right now i have 10gb of space in between the 2nd fat32 and the 3rd fat32 partitions. should i make it a fat32 partition, and then select it in the ubuntu partition manager?
and should i "shift" the last 2 fat 32 patritions to the end of the disk? can qtparted do this without data loss?

---

### Post by tmowerman on 2005-04-19
If you tell me the size of all the partitions I might be able to help more.  I am a little confused at the moment!

---

### Post by weijie90 on 2005-04-20
never mind.. ive done the installation.

---

