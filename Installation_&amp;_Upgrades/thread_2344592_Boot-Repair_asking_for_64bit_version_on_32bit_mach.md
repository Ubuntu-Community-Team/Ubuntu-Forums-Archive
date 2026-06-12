---
title: "Boot-Repair asking for 64bit version on 32bit machine."
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by Jonathan Brian Francoeur on 2016-11-26
Hi, I have a 1Gig ext4 partition at the beginning of a new disk which I'd like to boot from.  My linux OS is installed on another partition on the rest of the disk.
I'm following these instructions "[https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)" on a 32bit computer and I'm getting this error:
"64bits detected. Please use this software in a 64bits session. (Please use Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")) which contains a 64bits-compatible version of this software.) This will enable this feature."
What should I do?
Thanks.

---

### Post by oldfred on 2016-11-26
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by gordintoronto on 2016-11-27
Can you get to the command prompt and enter this command: uname -a

If boot-repair thinks your computer is 64-bits, methinks it's 64-bits, like most computers which are less than 8 years old.

---

