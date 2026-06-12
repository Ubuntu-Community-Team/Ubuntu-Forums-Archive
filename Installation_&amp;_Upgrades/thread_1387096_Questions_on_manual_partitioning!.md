---
title: "Questions on manual partitioning!"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2010-01-21
Hi.
I have some questions on manual partitioning!

What is the minimal size for a home directory?

I did a manual partition install in VirtualBox.
My vdi had these settings: RAM = 500MB & HDD = 10GB
Does this look correct. [Three pictures attached]

I am never certain as to the options for Primary, Logic, Beginning and End.

Does it matter the order in which you make partitions in Ubuntu?

---

### Post by oldfred on 2010-01-21
the order you create them does not matter. It does not do anything until you commit to the changes.

I just created a separate /home copied from my 3 years of updated install, but I moved all my data into another data partition and linked it into home. /home is about 1GB and I see a lot of the three years of cruft (history) that I did not need to copy over. Of course if you are adding data it can grow quickly.

---

### Post by Rytron on 2010-02-09
In plain language though, can someone explain the options for Primary, Logic, Beginning and End.

---

### Post by Herman on 2010-02-09
[Understanding Partitions and Partition Tables]("http://thestarman.pcministry.com/asm/mbr/PartTables.htm")  - thestarman.pcministry.com

See the detailed link above.
You probably don't need the level of detail explained in that link but if you can even understand a little of it you should be able to learn something.

Basically, a 'Primary' partition is a partition which is listed in one of the four sixteen byte spaces reserved for a partition in the partition table.
The partition table is part of the MBR, which is situated at the 'Beginning', (sector 0), of every formatted hard disk. 
'Formatting' a hard disk means writing a MBR to it.
'Partitioning' a hard disk means writing details about a partition in one or more of the four sixteen byte spaces in the partition table.]
Afterwards we usually 'format' a partitions with a file system, which means we install a file system in the partition. Most of it is in sectors close to the beginning of the partition.
The 'file system' is where the operating system writes down where it puts your files, or pieces of your files.

At first it was not possible to have more than four 'Primary' partitions, then somebody invented a special kind of primary partition called an 'extended' partition, which can contain more partitions (logical), as long as they are connected in a series. 
Many people say that an 'extended' partition is something like a box which can house a lot of 'logical' partitions. 

The 'Beginning' of a hard disk is sector zero, which is somewhere on the outside edge.
The 'End' of a hard disk is the last sector, somewhere close to the center of the hard disk, much like a record. The tracks of a hard disk are not spiral though, they're concentric, like rings in a tree trunk.
Each track is made of a lot of small squares called 'sectors'.
Each sector is given a number from the 'Beginning' of the disk to the 'End'.

---

### Post by Rytron on 2010-02-10
Go raibh míle maith agat (Thank you in Irish) Herman.

You explained the topic very well. 

:P

---

