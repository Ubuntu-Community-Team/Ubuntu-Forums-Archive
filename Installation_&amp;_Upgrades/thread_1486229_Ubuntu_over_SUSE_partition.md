---
title: "Ubuntu over SUSE partition"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by xizzling on 2010-05-17
Im choosing to install kubuntu 10.04 over OpenSUSE 11.0.
WIll the installer need a formatted partition or can i safely do it over my SUSE partition

Thanks in advance

---

### Post by ajgreeny on 2010-05-17
Chose manual partitioning when the installer gets to that part, and chose the partitions you have at present for Suse.  Simple.

---

### Post by srs5694 on 2010-05-17
Do you want to save anything in your current SUSE installation? If so, it may get tricky, depending on how your system is partitioned; best to post the output of "fdisk -lu" and "df -h" in your current SUSE setup (the first command done as root) for advice. If you're willing to lose everything, including your personal files, then ajgreeny's advice is good, with the addition that you should tell the installer to create fresh filesystems on everything.

---

