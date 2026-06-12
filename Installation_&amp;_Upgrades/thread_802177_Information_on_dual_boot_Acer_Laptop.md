---
title: "Information on dual boot Acer Laptop"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by Alan12345 on 2008-05-21
Hi All, just got my CD of Ubuntu 8.04 this morning.

I've tried out Ubuntu by simply booting to the CD, so am happy so far with the way it all works and want to now go as far as installing it on my laptop. No real probs - everything works (apart from Ubuntu apparently detecting a BIOS bug during loading from CD).

I have an Acer Travelmate 6410 which, as shipped, has the 80Gb hard disk already partitioned into two equal parts. The Winxp Pro installation is, as default, installed on the C: partition.

The way these laptops seem to work is that they don't ship with any system disks. Instead, there is a hidden file on the D: partition which, in the need to restore any system files or drivers, can be accessed from within the windows OS using a restore utility. I do have a CD backup of system files, which I created using the prompts after first use.

My question, as it relates to installing Ubuntu is twofold:

Firstly: If I install Ubuntu from the CD setup, will it automatically find this second D: partition? and will it ask me for any input options before simply installing itself? I obviously don't want a fully automated install if it's going to overwrite my C: partition.

Secondly: Can you tell me whether, by installing onto this otherwise empty D: partition, it might overwrite the hidden file, or whether there are any switches I can use during installation to avoid this? As mentioned above, I have backups of system files, but would prefer to leave WinXP as 'unmolested' as possible.

If there are any format/partition issues, or if this is referred elsewhere, please feel free to point me at info already provided.

Many thanks.

---

### Post by shifty_powers on 2008-05-21
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

invaluable reading ;)

oh and go and check out the absolute begginers forum. not saying you are, but it is one of the most active forums here and a great place to get advice ;)

---

### Post by Alan12345 on 2008-05-22
Thanks, will do

---

### Post by Herman on 2008-05-22
> Firstly: If I install Ubuntu from the CD setup, will it automatically find this second D: partition? and will it ask me for any input options before simply installing itself? I obviously don't want a fully automated install if it's going to overwrite my C: partition.
 The Ubuntu installer will find all of your partitions and offer you three main choices when it comes time to partition for Ubuntu.
You can use 'Guided partitioning', and resize a partition in your first hard disk, or you can use 'Guided partitioning- use entire disk', or 'Manual partitioning'. 
The Ubuntu installation CD won't do anything by itself, you have to tell it what to do.
The second option, 'Guided - use entire disk, will overwrite your Windows 'C:' drive, but only if you select that and click 'Forward'.
> Secondly: Can you tell me whether, by installing onto this otherwise empty D: partition, it might overwrite the hidden file, or whether there are any switches I can use during installation to avoid this? As mentioned above, I have backups of system files, but would prefer to leave WinXP as 'unmolested' as possible. I would advise against selecting the 'D' partition to install Ubuntu in. If you do, Ubuntu will certainly overwrite any files that are in there.
Instead, it would be best to resize the partition smaller (shrink it), and create new partitions beside it in the free space to install Ubuntu in. Ubuntu normally needs at least two partitions, one for the main operating system ('root'), plus a swap area, (something like a page file, but in a separate partition).

Regards, Herman :)

---

