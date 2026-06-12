---
title: "Uninstall Ubuntu - HOW?"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by Schalken on 2007-01-02
I need to uninstall Ubuntu from a friends laptop that currently dual boots Windows XP Home and Ubunut 6.06 Dapper Drake (in that order on the hard drive).

The problem is after I delete the Ubuntu and swap partitions I cannot resize Windows to occupy the empty space. It simple says 'Error resizing /dev/hda1. This may affect other changes in the list.' I need a sure-fire way to resize the Windows parition to occupy all space on the hard drive.

Another problem is, after removing Ubuntu, how do I restore Windows' bootloader (NTLDR) to the MBR? I had the same problem on another friend's computer and he decided to just give Ubuntu the smallest space possible, however, I can't even do that because I can't enlarge the Windows partition.

---

### Post by d3v1ant_0n3 on 2007-01-02
Boot up the Ubuntu live cd, remove Ubuntu partitions. 
Resize ntfs partition to use empty space. (you might need to reboot to do this, I forget)

Reboot computer with Windows cd in, boot to recovery console.

Run this command at prompt: ```
FIXMBR
```

All should be well with the world.

---

### Post by Schalken on 2007-01-10
Okay. The GParted LiveCD saved the day with regards to the partitioning, however "FIXMBR" was the same thing I told the aforementioned friend to do, and he said it "didn't do anything." Can you be sure that "FIXMBR", by itself, works? Have you tried it yourself?

---

