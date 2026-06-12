---
title: "Partition problems (installer looping)"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by liverpoolfcfan on 2006-08-17
Hi,

I am installing Ubuntu 6.0.6 - alternative version (since only have 64MB RAM) - on an Omnibook 7100 laptop. The CD rom,etc.. is recognized and the installed kick off and detects various devices however when I get to partition disks I get the following message:

- The following partitions are going to be formatted:
 partition #1 of IDE master (hda) as ext3
 partition #5 of IDE master (had) as swap.

Write changes to disk ?

I accept yes..and then after sometime I get the "Starting up partitioner" dialog which finishes and gets to the following dialog:

Configure software RAID
...
Finish partitioning and write changes to disk ?

If I pick finish partitioning  I get back to the screen:

- The following partitions are going to be formatted:
 partition #1 of IDE master (hda) as ext3
 partition #5 of IDE master (had) as swap.

I can't seem to get to the next step in the installer and no error seems to be occuring. 

Can anyone suggest some solutions ?

Thanks in advance.

---

### Post by swamytk on 2006-08-17
If you have used some other partition tool on this hard disk from other OS/distro (especially Mandriva), your partitions are not properly recognizable by Ubuntu. I have faced this problem. Try to clean up and organize your partition without any error messages like, "partition merge", "partition not on cylinder boundary",...

---

