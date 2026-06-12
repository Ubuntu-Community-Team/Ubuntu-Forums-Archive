---
title: "XP Partitioning Issue..."
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by JustDon on 2006-06-28
My partitions currently on my Dell Desktop (80GB HD) are:

   1.  Basic - 39MB - FAT - EISA Configuration
   2. Basic - 3.14 GB - FAT32 - Unknown Partition
   3. Basic - 52.71 GB - NTFS - System

The rest (35GB or so) is "unallocated". I have been told by an avid Ubuntu and SuSE user that I cannot re-partition this HD, that I must scrub, re-format and re-install XP in order to dual boot. Does anyone else see a way to correct this and dual boot WITHOUT having to re-intall XP?

---

### Post by glotz on 2006-06-28
Uhm, I see no problem there. Did he say anything specifically?

---

### Post by az on 2006-06-28
[QUOTE=JustDon]My partitions currently on my Dell Desktop (80GB HD) are:

   1.  Basic - 39MB - FAT - EISA Configuration
   2. Basic - 3.14 GB - FAT32 - Unknown Partition
   3. Basic - 52.71 GB - NTFS - System

The rest (35GB or so) is "unallocated". I have been told by an avid Ubuntu and SuSE user that I cannot re-partition this HD, that I must scrub, re-format and re-install XP in order to dual boot. Does anyone else see a way to correct this and dual boot WITHOUT having to re-intall XP?[/QUOTE]

Why would you have to reinstall windows to dual boot?

---

### Post by JustDon on 2006-06-28
[QUOTE=glotz]Uhm, I see no problem there. Did he say anything specifically?[/QUOTE]

Not really, just that the configuration that I have will render Windoze unbootable if I repartition for a Linux partition. Is there anything that I certainly should NOT do with this partition. I mean, obviously there are some things I should not do, but within reason... If I just create a swap partition and a root partition am I going to hose up XP? I think it had something to do with having more than 4 primary partitions....

---

### Post by confused57 on 2006-06-28
[QUOTE=JustDon]Not really, just that the configuration that I have will render Windoze unbootable if I repartition for a Linux partition. Is there anything that I certainly should NOT do with this partition. I mean, obviously there are some things I should not do, but within reason... If I just create a swap partition and a root partition am I going to hose up XP? I think it had something to do with having more than 4 primary partitions....[/QUOTE]

The swap partition will be set up as a logical partition, so if root "/" is set as a primary partition, you'd still possibly have only 4 primary partitions.
Ubuntu will install grub to the Windows mbr and you'll be able to select Windows or Ubuntu to boot into.  I recommend backing up any data you don't want to lose, things can go "not as expected".

---

### Post by RRS on 2006-06-28
[QUOTE=confused57]The swap partition will be set up as a logical partition, so if root "/" is set as a primary partition, you'd still possibly have only 4 primary partitions.
Ubuntu will install grub to the Windows mbr and you'll be able to select Windows or Ubuntu to boot into.  I recommend backing up any data you don't want to lose, things can go "not as expected".[/QUOTE]

Also I'd recommend defraging windows once or twice along with backing up any files you don't want to risk loosing.

Check these two guides for more detailed instructions;
[Moving from Windows to Ubuntu Linux: Getting Started]("http://psychocats.net/ubuntu/windowstoubuntu.html")
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/index.htm")

These should cover your concerns, if not, don't hesitate to ask more questions.

---

### Post by glotz on 2006-06-29
Backing up the stuff you gonna miss is always a good idea OS installing apart. Besides that, the partitioning tools are very safe as long as there's no power outtage mid-partitioning, etc. Make a **swap** (extended partition) roughly double the size of your RAM (up to one gig I think) and then the **/** (primary partition). The only way you can *fcsk up* is by installing *onto* the windoze partition thus wiping it.

---

### Post by az on 2006-06-29
[QUOTE=JustDon]If I just create a swap partition and a root partition am I going to hose up XP? I think it had something to do with having more than 4 primary partitions....[/QUOTE]

I think the great majority of people who visit the forums dual-boot ubuntu with windows.  It is very rare that the patitioner fails and borks your windows partition.  Don't worry about partitioning, the installer will do it for you automagically.  If it refuses to do anything, it's because it thinks you have an issue that will render your box unbootable or cause data loss.

That's no excuse to not back up your data, just in case, though....

The installer abstracts all the problems you could face - you don't have to know about number of partitions and so forth.

---

### Post by leo_m on 2006-06-29
Yes, the first partition is of type EISA configuration - so it is where hard-drive stores some information...

Um, I am not sure if you have the ability to create 2 more primary partitions or 1 primary and 1 extended (having many logical ones) partitions.

If not, ie, if EISA config partition counts as a primary partition, thus leaving you with only 1 possible new partition, then you have to forego the swap partition.

---

### Post by JustDon on 2006-06-29
[QUOTE=leo_m]Yes, the first partition is of type EISA configuration - so it is where hard-drive stores some information...

Um, I am not sure if you have the ability to create 2 more primary partitions or 1 primary and 1 extended (havine many logical ones) partitions.

If not, ie, if EISA config partition counts as a primary partition, thus leaving you with only 1 possible new partition, then you have to forego the swap partition.[/QUOTE]

So it is true that I can only have four primary partitions? That could be what the issue is that my friend had seen. Does the Live version use any swap? If not, then I am fine without it - because it SMOKES on the Live CD!

---

### Post by RRS on 2006-06-29
Both my dual boot machines have swap in the extended partition with no apparent problems. 

When I installed I created a fat32 for file sharing which also got placed in the extended so I only have an ext3 (Ubuntu) and a NTFS (windows) as primary.

Both where done from the 5.10 install cd and I seem to recall the extended partitions being created automatically. Not sure if the Dapper cd will but you could always run gparted from the live cd and partition before installing.

---

### Post by woopud on 2006-06-30
Use Gparted !

---

