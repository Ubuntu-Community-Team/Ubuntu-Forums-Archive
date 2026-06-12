---
title: "Karmic won't format partition to NTFS"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by xpacker on 2009-12-21
I've been using Ubuntu for about 2 months now (love it) on my laptop. I installed Karmic on it, no problems, formatting a storage partition to NTFS (with other partitions: Windows, Swap, Root, Home).
 
I'd like to do the same on an old desktop I am resurrecting to play with (want to try different distros, software, etc). But when I installed via live CD, there was no option to format a storage partition to NTFS. There's XFS and JFS, but no NTFS. I'd like to be able to use any files written to this partition, by both Windows and Linux.
 
Am I doing something wrong? Or is there an alternate format that would serve my purposes? I want to be able to write large files (20GB or so), that can be read later by either Windows or Linux.
 
I'm not very computer-savvy, so please make any suggestions/help as basic as possible.
 
Thanks!

---

### Post by darkod on 2009-12-21
For ntfs support you need to install ntfsprogs (or ntfs-progs, don't remember exactly).
In terminal try:
sudo apt-get install ntfsprogs

After that you can format as ntfs, provided this was the problem.

---

### Post by xpacker on 2010-01-18
There didn't seem to be a problem using NTFS files -- the install program just didn't offer the option.  So I did it this way:


[LIST]
[*]formatted to ext3 during installation
[*]used Gparted afterward to re-format to NTFS
[/LIST]

---

