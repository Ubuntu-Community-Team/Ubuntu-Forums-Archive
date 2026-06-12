---
title: "Ubuntu partitions as unformatted partition in Windows XP"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by jukkakar on 2007-09-28
Hi,

I just installed Ubuntu on new HP laptop with pre-installed Windows XP Pro.
The problem: Windows is showing the Linux root partition as drive d: and offer to format it. 
Why windows is showing Linux partition?
How to hide this partition from Windows so I do not accidentally format my Ubuntu installation?

Here is output of fdisk:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2           17292       19457    17398395    7  HPFS/NTFS
/dev/sda3            4865        6080     9767520   83  Linux
/dev/sda4            6081       17291    90052357+   5  Extended
/dev/sda5            6081        6566     3903763+  82  Linux swap / Solaris
/dev/sda6            6567       13861    58597056    7  HPFS/NTFS
/dev/sda7           13862       17291    27551443+   7  HPFS/NTFS

sda1 is windows partition (C: )
sda2 is HP recovery partition (E: )
sda3 Linux root (D: ) <-I want to hide this in Windows
sda6 (F: )
sda7 (G: )

Jukka

---

### Post by sstusick on 2007-09-28
Are you sure Windows is seeing the root partition? Windows shouldn't be able to see a Linux partition.

---

### Post by jukkakar on 2007-09-28
Windows does not tell which partition My drive d: is, but size in the format dialog matches the size shown in the Disk Management for my Linux root partition.

Jukka

---

### Post by jukkakar on 2007-09-28
No I got confirmation that drive D is my Ubuntu root.

I installed Ext2 Installable File System For Windows from [http://www.fs-driver.org/](http://www.fs-driver.org/)

I defined the drive L for Linux partition. After this both D: and L: showed the content of the Ubuntu root file system.

Control Panel of IFS Drives does not show any info about drive D:. When I removed the assignment of drive L:, drive D: is still showing data of ext3 Linux partition.

So this is a good workaround, Windows does not any more offer to format this partition.

If there is way to hide this Linux partition, I would like to do that. 

So please post if you have new ideas?

Jukka

---

### Post by sstusick on 2007-09-28
Ahh the FS driver.. that explains that problem... tho I am not sure how you would hide it in Windows. Rename it, maybe. Would that help? "Linux Root" or something.

Sorry I couldn't be of more help. Hopefully someone else will come up with a better solution.

---

