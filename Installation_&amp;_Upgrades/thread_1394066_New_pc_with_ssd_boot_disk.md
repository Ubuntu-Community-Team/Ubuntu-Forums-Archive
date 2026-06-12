---
title: "New pc with ssd boot disk"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by dajashby on 2010-01-30
I've just bought a new pc with a 128 GB ssd and 500 GB mechanical drive  (it should be delivered mid next week).  I want to install ubuntu as a host os and win 7 as a guest. I'm planning to use Virtual Box.  Obviously I want both os's to use the ssd for booting and main application storage, but space is limited.  I'm looking for some advice on how to partition both drives when I install ubuntu.

---

### Post by oshunluvr on 2010-02-09
Congrats on the new system: I'm confused - dual boot or virtualbox or both??? If you're using vbox to run W7 the partition setup won't matter - the guest OS's don't get direct drive access.

Dual boot:

ssd:
primary 1: swap (1 to 4 gb depending on your needs)
primary 2: for W7 (all remaining space)
extended/logical 5: 16gb 

500gb drive:
however you want for data - might want a NTFS and linux (your choice of format) partitions plus have a separate /home partition for linux.

You should do some reading on SSD performance re: filesystem formats and fstab settings to ensure best output of your ssd.

---

