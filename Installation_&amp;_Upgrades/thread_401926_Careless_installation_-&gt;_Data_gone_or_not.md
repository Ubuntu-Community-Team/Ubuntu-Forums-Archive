---
title: "Careless installation -&gt; Data gone or not?"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by Woek on 2007-04-05
I really hope someone can help. I've been incredibly careless and I should have known better. This is what happened:

I needed to install Linux at my work, and did so with kubuntu 6.10 (first encounter with kubuntu) on my every day desktop. It has two disks, one with winxp and one with all my work.
I started the kubuntu installation from the live cd, and at first selected the work disk for repartitioning. I slided the space slider all the way to the left, assuming this decreased the size of the linux partition. While the program was busy with something, I figured I shouldn't take the risk with this disk, since I had no backup of the data on it. When the installation program came to the point of "warning if you continue data will be lost" I clicked cancel (or "back" I don't remember) and now selected the other disk for repartitioning. Again I moved the slide way to the left and continued with the install.

When I booted into windows the next time I saw, to my horror, that:

 - My windows partition had become really small. Apparently moving the slider to the left decreases the EXISTING partition, not the NEW partition. Had I misunderstood?! But at least winxp still booted normally.

 - My work disk was unformatted, very small, and naturally contained NO WORK DATA. :shock: 

Since I canceled the install process on the work/data disk BEFORE the warning messages, and without interrupting any processes, my hope is that the data can still be recovered.
Please, if anyone has any idea of what I can try, let me know. It concerns years of work. This has been a very very tough lesson in prudence already. :oops: 

I've also posted this in the kubuntu forums. Please excuse the spam but maybe this increases my chances...

---

### Post by louieb on 2007-04-05
Well lets boot to kUbuntu and open a Terminal window. 
and then type ```
sudo fdisk -l 
```
(as in Little). 
Post the output here. This will list the partition table for the two drives.
From your description of what happened. there is a good chance that you can get your data back. This is just the first step.

---

### Post by Woek on 2007-04-09
I don't have access to the harddisk until tomorrow, but I'll do that. A friend advised me to make a dump of the entire disk (with dd) to be safe, and manually re-create the old partition table without formatting anything. He said this might make the data accessible again. What do you think?

---

### Post by louieb on 2007-04-09
Dumping it with dd is good sense.  I can think of 3 or 4 things to try.
What I would try first is to Use a Puppy or Knoppix Live CD and see if you can mount the partition and use their file manage to browse the disk and see if  it can list your files. 
If you have to try and rebuild the partition table there is a Live CD called **Parted** this has  a partition table guessing program that I've heard is very good. 
A couple of other live CDs to try are test disk and system rescue. good luck.

---

### Post by Woek on 2007-04-10
Ok, I finally have access to the computer. I have parted available in Kubuntu. I also have the System Rescue Disk, with dd_rescue on it (and GParted). 

The output of fdisk -l /dev/hdb (the affected drive) is:

```

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2481    18756328+   f  W95 Ext'd (LBA)
/dev/hdb5               2        2481    18748800    7  HPFS/NTFS

```

The original partition, as far as I know, was an NTFS format. I don't think it used an extended partition...

Hope this is useful for you...

---

### Post by Woek on 2007-04-11
Ok people, I have my data back  :D

A friend could retrieve the data. He saw that the sectors in the NTFS partition had a strange offset. He looked up specific markers (from the MS website), using ghex2, and saw that the first sectors contained a lot of junk (old FAT32 tables etc), and that the NTFS master boot record was located much further on the partition. He then made a dump of the disk starting from the MBR sector until the end of the partition, which we could then mount without any errors. After checking that the files contained the actual data, we formatted the disk with FAT32 (no user-rights, avoids possible problems reading the data in WinXP) and just copied the files from the mounted file to the disk.
Only one directory that was encrypted was not copied, but luckily I also have those files in a CVS repository.

Louieb, thanks for the suggestions!

---

