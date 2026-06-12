---
title: "[SOLVED] &amp;quot;Problem with operating system&amp;quot;"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by joobleblob on 2008-09-04
Hi all,

I installed ubuntu quite some time ago (shortly after the official release of 8.04 after having run on the beta)
the other day I decided that I'd quite like to play some of my games and so stupidly decided to install a WINDOWS *spit* partition. but I fear that ALL of my ubuntu data is lost,

I didn't install over ubuntu, I resized the ubunut partition from 120GB (ish) to 30 so I could install an 80GB Windows XP partition (because windows games take up more space than most of my ubuntu stuff.

now, I can boot windows, but when I try to boot ubuntu I'm given the message "Problem with operating system" on the second boot screen on my machine. I haven't re-sized the partition to be any smaller than what space it uses, it has twice the amount of space that it used.

does anyone know if there's any way that I can get it back? I have the ubuntu disk, G-parted and the windows XP *spit* disk and am more than willing to download and burn any other that may be needed.

thanks in advance.#-o

---

### Post by kosmiciatakuja on 2008-09-04
First of all run any partition editor to verify that the ubuntu partition still exists. 
Either do it from windows (with something like partitionmagic) or run an Ubuntu liveCD and gparted from there. 

If it does exist, we can work from there.

---

### Post by prshah on 2008-09-04
> **joobleblob said:**
> decided to install a WINDOWS partition. but I fear that ALL of my ubuntu data is lost,

I didn't install over ubuntu, I resized the ubunut partition from 120GB (ish) to 30 so I could install an 80GB Windows XP partition

First, check if the ubuntu partitions exist; post a screen shot of the windows disk management utility; to use the disk management utility, click start-Run, and give the command```
diskmgmt.msc
```

---

### Post by joobleblob on 2008-09-04
it does still exist, I'm running the live session from the ubuntu install disk to use this, I checked using G-parted and the 30.0GB ubuntu part. is existant

EDIT: it'll be hard to get anything to you from the windows section because for some obscure microsoft reason I can't connect to my own router

RE-EDIT: my brother helped me sort it, if anyone was looking to have their problem of the same type fixed heres a HOWTO on the topic [http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with)an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with)an_Ubuntu_Live_CD)

---

### Post by kosmiciatakuja on 2008-09-05
Okay, so I guess this is solved :)

You can add [Solved] to the topic so that other people with similar problems may find the solution easier.

---

### Post by Sef on 2008-09-05
When you install Windows after Ubuntu, the Windows bootloader overwrites GRUB and only recognizes Window oses.

Another way to resolve the problem is with [Super GRUB Disk]("http://www.supergrubdisk.org/index.php").

---

