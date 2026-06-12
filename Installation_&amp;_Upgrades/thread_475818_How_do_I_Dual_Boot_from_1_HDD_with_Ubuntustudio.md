---
title: "How do I Dual Boot from 1 HDD with Ubuntustudio?"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by mshadow818@msn.com on 2007-06-16
I have not been able to find consistent instructions on how to set up a single hard drive to dual boot Ubuntustudio and Windows XP.  Here is my setup:

Pentium 4 / 2.93GHz
504MB of RAM
Windows XP
1 Hard Drive with two partitions - One 4.5GB FAT32 Recovery partition that came with the computer and one 181GB NTFS partition with Windows installed.

There seems to be a difference of opinion on how many additional partitions to use (for the swap, etc) and whether to use FAT32 or NTFS or even whether to partition first or use the install disc.  

Any help anyone could give would be greatly appreciated.

---

### Post by merlinus on 2007-06-16
These instructions should be applicable to studio as well as ubuntu:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

-merlin

---

### Post by mshadow818@msn.com on 2007-06-16
Under what circumstances would the different options listed on [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) be used?  
How many of these options are reversible?

---

### Post by merlinus on 2007-06-16
This might be more helpful:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Once you have applied the partitioning and installed ubuntu, you can always remove it, go back to windows only, and re-size that partition.

You will have to also remove grub and reinstall the windows bootloader, but that it easy from your original windows cd.

As for partitioning schemes:

you will need / and /swap.  I also recommend /home, and an additional one for /data, where you can keep your files and share them between both operating systems.

There are drivers that will allow you to read and write to and from windows and ext3.

-merlin

---

### Post by mshadow818@msn.com on 2007-06-16
What are the advantages/dissadvantages of using FAT32 or NTFS on the various partitions?

---

### Post by merlinus on 2007-06-16
Windows uses FAT32 and NTFS; ubuntu uses EXT3 (or EXT2 or Reiserfs), but EXT3 is much better than anything from redmond.

As I said, you can install drivers that will allow ubuntu to read and write to NTFS, and it will do that with FAT32 without anything extra.  And IFS, a windows driver, will allow you to read and write to and from EXT3.

FAT32 wastes disk space, due to its allocation scheme, and gets awfully fragmented in a hurry.

Use NTFS for windows, and EXT3 for /data (and everything else).

That is what I do.

-merlin

---

