---
title: "Need partitioning etc advice before installing 10.04 i386 + Windows7 for dualboot"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by j4ck455 on 2011-01-02
I've done a bit of searching (forum & tags & Google) for existing threads, unfortunately there are too many search results none of which seem to help me. If there is a better way to search or links to existing threads please post them and I will use that for finding the answer to my problem.

The problem is this, I have an oldish notebook that I want to wipe clean and install 10.04 on as well as dual boot Windows7 (it used to run Vista until I overwrote that with Ubuntu a long time ago). I have already backed up my /home folder to external storage, I'm ready to reinstall the notebook as soon as I know the best way of doing it.

What I want is a separate boot partition where Grub is the bootloader (not Windows7).

[list=1][*]Should I first install Windows7 by creating a "C:" partition for the ntloader (with Windows7 installed to an "E:" partition) and then install Ubuntu 10.04 on an adjacent (to "E:") partition and simply overwrite that "C:" partition with Grub?

[*]Or, should I first install Ubuntu 10.04 with a separate partition for Grub (where "C:" would have been)?[/list]

Logic tells me to first install Windows7 as per my 1st option and then install Ubuntu afterwards, I'm just not sufficiently familiar with Windows7 to know all the caveats.

PS: I do not want to run Windows7 in a VM.

---

### Post by Quackers on 2011-01-02
I would recommend that Win 7 be installed first. Then I would suggest that you look at the disk management screen and find out how many primary partitions have been used. 3 or less is good - 4 is bad.
This then governs what is required to install Ubuntu.

---

### Post by j4ck455 on 2011-01-24
I used Linux for the partitioning then installed Windows7 and then installed Ubuntu.

```
   Device Boot      Start         End      Blocks   Id  System                                                                                                                      
/dev/sda1               1          61      487424   83  Linux                                                                                                                       
Partition 1 does not end on cylinder boundary.                                                                                                                                      
/dev/sda2              61        6140    48828416   83  Linux                                                                                                                       
/dev/sda3   *        6140       12219    48828416    7  HPFS/NTFS                                                                                                                   
Partition 3 does not end on cylinder boundary.
/dev/sda4           12219       14594    19074049    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           12219       12645     3417088   82  Linux swap / Solaris
/dev/sda6           12645       13617     7811072   83  Linux
/dev/sda7           13617       14594     7843840    7  HPFS/NTFS

```

---

