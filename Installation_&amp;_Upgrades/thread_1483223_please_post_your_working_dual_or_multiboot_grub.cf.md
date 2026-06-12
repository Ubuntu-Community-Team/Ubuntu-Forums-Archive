---
title: "please post your working dual or multiboot grub.cfg file (GRUB2 only plz)"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by malrost on 2010-05-14
I'm comfortable w/ GRUB, but it's time to move to GRUB2. Did you manage to get GRUB2 working on a dual or multiboot system? I'd like to see some examples that work.

If so, please post your working grub.cfg file & describe how & why you partitioned the way you did. 

Please let me know if you have any suggestions as to useful strategies for the following configuration.

I have enough space now that I'd like to partition it for about 3-4 BSDs, 5-7 Linux distros, 2 Windows installations. (Why not?) I will be structuring and writing a GRUB2 file for the following boot configuration:

[LIST]
[*]A small & fast SSD drive for boot and system files (sda)
[*]Three increasingly large and slow drives for data (sdb-sdd)
[/LIST]

Would ext4, xfs, jfs, btrfs, or other formats be better suited for any of the following files?
[LIST=1]
[*]large consumer video & consumer files
[*]audio files related to Ardour and JACK apps
[*]documents
[/LIST]

Attached is my most recent GRUB legacy menu.lst file, from a two disk (sda & sdb) configuration with working Ubuntu Studio, Fedora, XP, and Ubuntu.

---

