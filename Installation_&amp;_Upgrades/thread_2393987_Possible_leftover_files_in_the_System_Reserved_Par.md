---
title: "Possible leftover files in the System Reserved Partition (SRP)"
date: 2018-06-11
forum: Installation &amp; Upgrades
---

### Post by levengli2 on 2018-06-11
Thank you in advance for any help.

After physically damaging my hard drive, I was forced to reinstall Ubuntu (14.04 LTS) and run [boot-repair]("https://sourceforge.net/p/boot-repair/home/Home/"). It appears as though boot-repair has left a directory with 2 large files (and a bunch of small ones) on my the System Reserved Partition (SRP). As this partition is limited in size, leftover files block Windows from updating my dual-boot laptop. The full details of the question (including a link to the contents of the directory) can be found at [URL="https://askubuntu.com/q/1045399"]https://askubuntu.com/q/1045399
[/URL]
The short version of the question is: can I safely remove the boot-repair folder and anything under it from the SRP without bricking my laptop?

---

### Post by yancek on 2018-06-11
Removing log files which are just a record of what was done, should not have any effect on the operation of the computer.  I find it surprising that they are on a windows System Reserve Partition.

---

