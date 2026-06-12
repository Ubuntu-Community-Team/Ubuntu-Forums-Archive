---
title: "Partition does not end at cylinder boundary"
date: 2005-02-06
forum: Installation &amp; Upgrades
---

### Post by stevetxt on 2005-02-06
I just noticed, since installing Ubuntu Warty a couple of weeks ago, my partition table now shows small areas of blank space at the ends of partitions.  Here is the table from fdisk /dev/hda:


Disk /dev/hda1: 255 heads, 63 sectors, 1146 cylinders
Units = cylinders of 16065 * 512 bytes

     Device Boot    Start       End    Blocks   Id  System
/dev/hda1p1   ?     13578    119522 850995205   72  Unknown
Partition 1 does not end on cylinder boundary:
     phys=(371, 101, 51) should be (371, 254, 63)
/dev/hda1p2   ?     45382     79243 271987362   74  Unknown
Partition 2 does not end on cylinder boundary:
     phys=(299, 114, 44) should be (299, 254, 63)
/dev/hda1p3   ?     10499     10499         0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary:
     phys=(353, 115, 52) should be (353, 254, 63)
/dev/hda1p4        167628    167631     25817+   0  Empty
Partition 4 does not end on cylinder boundary:
     phys=(0, 0, 0) should be (0, 254, 63)

Partition table entries are not in disk order


My last install was Debian 3.0 (which still resides on partition 4).  The partition table did not show these bits of free space then.  Ubuntu is on Partition 6.

Any idea what is the problem here?

Steve

---

### Post by Xian on 2005-02-06
What applications have you been using to create and manage your partitions?

---

### Post by ulefr01 on 2005-02-06
[QUOTE=stevetxt]I just noticed, since installing Ubuntu Warty a couple of weeks ago, my partition table now shows small areas of blank space at the ends of partitions.  Here is the table from fdisk /dev/hda:


Disk /dev/hda1: 255 heads, 63 sectors, 1146 cylinders
Units = cylinders of 16065 * 512 bytes

     Device Boot    Start       End    Blocks   Id  System
/dev/hda1p1   ?     13578    119522 850995205   72  Unknown
Partition 1 does not end on cylinder boundary:
     phys=(371, 101, 51) should be (371, 254, 63)
/dev/hda1p2   ?     45382     79243 271987362   74  Unknown
Partition 2 does not end on cylinder boundary:
     phys=(299, 114, 44) should be (299, 254, 63)
/dev/hda1p3   ?     10499     10499         0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary:
     phys=(353, 115, 52) should be (353, 254, 63)
/dev/hda1p4        167628    167631     25817+   0  Empty
Partition 4 does not end on cylinder boundary:
     phys=(0, 0, 0) should be (0, 254, 63)

Partition table entries are not in disk order


My last install was Debian 3.0 (which still resides on partition 4).  The partition table did not show these bits of free space then.  Ubuntu is on Partition 6.

Any idea what is the problem here?

Steve[/QUOTE]


I think that this can help you :

do :
fdisk /dev/hda
use option : x (expert mode)
use option : f (fix partition order)
use option : v to verify partition
if it is ok 
then you can do
option : w ( to write table to disk)
option : q to quit

---

### Post by stevetxt on 2005-02-06
Earlier, prior to installing Debian 3.0, I partitioned using fdisk or cfdisk.  Then the partition talble showed no irregularities.

This time I used the Ubuntu installer to repartion, asking it to delete the final two partitions, which freed up about 2.7 gb of space.  Then I asked it to automatically partition the free space and install Ubuntu in it.  So it created partition 6, at about 2.5 gb, and partition 7 for swap at about 150 mb.  After that I've had these partition tables showing the partitions not ending at cylinder boundaries, with little odd bits of free space.  

Here is the output from the commands x, f, and v in fdisk /dev/hda.  I didn't write it because it looked possibly problematical:

Command (m for help): p

Disk /dev/hda: 20.0 GB, 20003880960 bytes
16 heads, 63 sectors/track, 38760 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18281     9213246    7  HPFS/NTFS
/dev/hda2           18281       20321     1028160    c  W95 FAT32 (LBA)
/dev/hda3           31939       38760     3437879    f  W95 Ext'd (LBA)
/dev/hda4           20321       31939     5855692+  83  Linux
/dev/hda5           31939       33294      682731   82  Linux swap
/dev/hda6   *       33295       38457     2602120+  83  Linux
/dev/hda7           38458       38760      152680+  82  Linux swap

Partition table entries are not in disk order

Command (m for help): x

Expert command (m for help): f
Done.

Expert command (m for help): v
Logical partition 5 not entirely in partition 3
Logical partition 6 not entirely in partition 3
Logical partition 7 not entirely in partition 3
815 unallocated sectors

Expert command (m for help): p

Disk /dev/hda: 16 heads, 63 sectors, 38760 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0  15  63 1023         63   18426492 07
 2 00  15  63 1023  15  63 1023   18426555    2056320 0c
 3 00  15  63 1023  15  63 1023   20482875   11711385 83
 4 00  15  63 1023  15  63 1023   32194322    6875758 0f
 5 00  15  63 1023  15  63 1023          1    1365462 82
 6 80  15  63 1023  15  63 1023          1    5204241 83
 7 00  15  63 1023  15  63 1023          1     305361 82

Expert command (m for help):

---

### Post by ulefr01 on 2005-02-09
Please can you do the following :
fdisk /dev/hda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
    then you can do
    option : w ( to write table to disk)
    option : q to quit
else if it is not ok
    then send me the output of option p and v

---

### Post by ulefr01 on 2005-02-09
[QUOTE=stevetxt]Earlier, prior to installing Debian 3.0, I partitioned using fdisk or cfdisk.  Then the partition talble showed no irregularities.

This time I used the Ubuntu installer to repartion, asking it to delete the final two partitions, which freed up about 2.7 gb of space.  Then I asked it to automatically partition the free space and install Ubuntu in it.  So it created partition 6, at about 2.5 gb, and partition 7 for swap at about 150 mb.  After that I've had these partition tables showing the partitions not ending at cylinder boundaries, with little odd bits of free space.  

Here is the output from the commands x, f, and v in fdisk /dev/hda.  I didn't write it because it looked possibly problematical:

Command (m for help): p

Disk /dev/hda: 20.0 GB, 20003880960 bytes
16 heads, 63 sectors/track, 38760 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18281     9213246    7  HPFS/NTFS
/dev/hda2           18281       20321     1028160    c  W95 FAT32 (LBA)
/dev/hda3           31939       38760     3437879    f  W95 Ext'd (LBA)
/dev/hda4           20321       31939     5855692+  83  Linux
/dev/hda5           31939       33294      682731   82  Linux swap
/dev/hda6   *       33295       38457     2602120+  83  Linux
/dev/hda7           38458       38760      152680+  82  Linux swap

Partition table entries are not in disk order

Command (m for help): x

Expert command (m for help): f
Done.

Expert command (m for help): v
Logical partition 5 not entirely in partition 3
Logical partition 6 not entirely in partition 3
Logical partition 7 not entirely in partition 3
815 unallocated sectors

Expert command (m for help): p

Disk /dev/hda: 16 heads, 63 sectors, 38760 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0  15  63 1023         63   18426492 07
 2 00  15  63 1023  15  63 1023   18426555    2056320 0c
 3 00  15  63 1023  15  63 1023   20482875   11711385 83
 4 00  15  63 1023  15  63 1023   32194322    6875758 0f
 5 00  15  63 1023  15  63 1023          1    1365462 82
 6 80  15  63 1023  15  63 1023          1    5204241 83
 7 00  15  63 1023  15  63 1023          1     305361 82

Expert command (m for help):[/QUOTE]


Your printout after the f option seems to be ok; your hda4 is now hda3 and the extended hda3 is now hda4

Please do my previous tip

---

### Post by stevetxt on 2005-02-10
But I don't want to change anything about the partition number labels.  That is not a problem.  If I change them, then I might have to change my mount statements, right?  

The problem was the little bits of free space at the ends of the partitions.  It's as if the Ubuntu installer does some sort of miscalculation when it repartitions some of those.

Steve

---

### Post by ulefr01 on 2005-02-12
[QUOTE=stevetxt]But I don't want to change anything about the partition number labels.  That is not a problem.  If I change them, then I might have to change my mount statements, right?  

The problem was the little bits of free space at the ends of the partitions.  It's as if the Ubuntu installer does some sort of miscalculation when it repartitions some of those.

Steve[/QUOTE]

The problem 'Partition does not end at cylinder boundary' is another thing,
You only only lose some free spaves because you have not optimal chosen the blocks   in a partition, thats all

---

