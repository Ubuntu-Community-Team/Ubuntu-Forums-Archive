---
title: "Installer Partioner Made Me Nervous"
date: 2005-08-05
forum: Installation &amp; Upgrades
---

### Post by cjoshuav on 2005-08-05
I have a 5GB partion already set up as FAT32 on my laptop harddrive, and that is where I want to install H. Hedgehog.  I have two other partions, both NTFS, that I want Ubuntu to ignore since I want to be able to boot to one of them (for Windows XP) and the other I'm going to use as read-only (for now) in Ubuntu.

So, I told the installer not to use the first two partions and to make the third bootable and keep it FAT32 and to mount to / .

If I proceed with these options, will H. Hedgehog in any way touch my two NTFS partitions?  Will the installer automatically set things up for dual-boot, or will I need to use BootCommander or some such utility?

Thanks very much for your help.  I apologize for my paranoia, but I don't feel like doing a clean install of WinXP if I screw this up.

Joshua

---

### Post by orev on 2005-08-05
Even though it can be scary, the installer does a very good job of partitioning if you trust it.  You should be able to use the guided partitioning to come up with an arrangement that is what you're looking for.

Hopefully you'll feel like you can ditch WinXP after you try ubuntu anyway!

---

### Post by cjoshuav on 2005-08-05
So will it completely ignore my two NTFS partitions if I've set it for "Do Not Use"?

As for going Linux-only, I'll have to wait until EndNote is a Linux-native app. :)

Joshua

---

### Post by cjoshuav on 2005-08-05
Perhaps I'm burying my question in too much text.  Here it is in a single sentence:

If I set my two NTFS partitions to "Do Not Use" will the partitioner completely leave them alone and allow me to dual boot?

---

### Post by az on 2005-08-05
They will not be touched.  You will need to make your "/" partition something other than fat32, though.

fat32 does not support unix permissions and so forth.  Maybe you will want to move your data to your other partitions and wipe whis one out, or resize it (using the partitioner)

---

### Post by cjoshuav on 2005-08-06
Thanks!  I don't mind wiping the partition.  What format option should I use?

---

### Post by az on 2005-08-06
Close your eyes and take the default (ext3)

Just boot from the cd and let it make it's way to the partitioner.  Do not take the default "blow away the first hard drive", but manually delete the fat32 partition you mean to use.  This makes some free space.  Then scroll down to guided partitionning and let it decide what to do with the free space.

---

### Post by kosmic on 2005-08-06
If you are looking for something like EndNote for linux try this programs :

refDB -> [http://refdb.sourceforge.net/](http://refdb.sourceforge.net/)
Publiographer -> [http://www.pybliographer.org/](http://www.pybliographer.org/)
sixpack -> [http://www.santafe.edu/~dirk/sixpack/](http://www.santafe.edu/~dirk/sixpack/)
Qbib -> [http://www.hsdi.com/qddb/applications/#qbib](http://www.hsdi.com/qddb/applications/#qbib)

---

