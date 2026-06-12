---
title: "[SOLVED] Partitions of external harddisk not showing"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Bliepo32 on 2008-06-26
I have the following problem:

I have two harddisks. One is an internal SATA harddisk, and the other is an external USB harddisk. Now I have three partitions on the external harddisk (made them with Acronis).

1. A NTFS partiton (and I don't want to lose it)
2. An EXT3 partiton
3. A linux swap partiton

When I enter the installer, and get to the part of the partitioning, I select manual. I  then see both my disks in the menu. However, only the partitions of the internal disk show up, and not those of the external disks.

I do not want to use the whole disk for it. Only the EXT3 partition and the swap. So how can I do this?

EDIT: I am using the alternate installation disc.

P.S.: Spelling mistakes etc. are caused because it is quite late in my country.

---

### Post by logos34 on 2008-06-26
I'm wondering if the partitioner not seeing the external partitions is due to Acronis.  

Get the [Gparted live cd]("http://www.google.com/url?q=http://gparted.sourceforge.net/livecd.php&sa=X&oi=smap&resnum=1&ct=result&cd=2&usg=AFQjCNEexPGrlh_aaGDTveYX-NgcJyUKSg") and (if it can see the external) use it to delete the ext3 and swap.  Create new ones.  Try the ubuntu alternate install cd again

---

### Post by eldragon on 2008-06-26
why not leave the free space and let the alternate installer manage the free space? i dont see why it should be a problem.

---

### Post by Bliepo32 on 2008-06-27
> **eldragon said:**
> why not leave the free space and let the alternate installer manage the free space? i dont see why it should be a problem.

Why didn't I think of that one myself? But I think I will try Gparted first.

---

### Post by Bliepo32 on 2008-06-27
Ok, I have tried Gparted. When I looked at the USB disk, Gparted marked the whole disk as being unused. I think this is probably the cause. Is there anyway I can repair this, except for formatting the entire drive?

---

### Post by logos34 on 2008-06-27
> **Bliepo32 said:**
> Ok, I have tried Gparted. When I looked at the USB disk, Gparted marked the whole disk as being unused. I think this is probably the cause. Is there anyway I can repair this, except for formatting the entire drive?

Yes.  [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  Use it to fix the partition table.

On the ubuntu live cd, >system>admin>software sources>check **universe** repository.  
(or system>admin>synaptic>settings>repositories)

then in a terminal:

[B]sudo apt-get install testdisk

sudo testdisk
[/B] 
Be careful and read the documentation first.

---

### Post by Bliepo32 on 2008-06-29
Ah well, I already made a back-up and formatted it. It works now, and works well. If something like this should happen again, I will remember to use testdisk. Anyway, problem SOLVED.

---

