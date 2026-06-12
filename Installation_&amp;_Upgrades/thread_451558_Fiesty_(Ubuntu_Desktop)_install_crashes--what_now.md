---
title: "Fiesty (Ubuntu Desktop) install crashes--what now?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by yababom on 2007-05-22
Current setup:

Dimension 4700 (P4-3Ghz, 1.5GB ram, nVidia 7600)
3 hard disks and 1 DVD-R/RW
2 hard disks on SATA0 and SATA2
1 hard disk and DVD/RW on IDE
BIOS set to boot SATA first.

Currently running FC5 on SATA2 HD.

I want to install Ubuntu fresh on SATA0 HD so that I can dual-boot FC5 and ubuntu for a while.

I can load live CD without problems and start install process. I select manual partitioning: I delete an old windows partition from first 40GB of SATA0, and partition that space to use ~36GB as / (ext3), and 1.5 GB as swap. Remaining space on SATA0 is already formatted as  ext3 data partition. 

After starting automated install process, the drives are partitioned and formatted, and it appears to start copying data from the DVD for a fraction of a second before closing (failing). The target / partition claims to have ~760 MB of data, but I don't see anything there using nautilus.  

After the install progress windows disappears, a series of crash notices appear in the notification area. The crash reports  mention the program names, but no other details of the error. After 10-20 of these, i can restart the install process, but it always ends up failing at the same place.

So what can I do to fix the problem? Is there somewhere I can look for more details on the reason for the crash? Is this a known problem?

---

### Post by Borzo on 2007-05-22
try the alternate installation CD

---

### Post by yababom on 2007-05-22
Is that the only option? I mean, I can give it a try, but I'd also like to know what is going wrong...

---

### Post by louieb on 2007-05-23
if you ran the media check and it was ok then you can look here [Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu")

---

