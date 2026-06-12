---
title: "2 Entries for windows 7 in GRUB"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by anantanni on 2012-06-28
One is on sda0 and the second is on sda1(which is where Windows is installed)
How do I remove the sda0 entry?
Also, while I was installing Ubuntu, it said I had multiple operating systems on my machine, even though I only had Windows. 
I'm thinking I might have 2 bootloaders for Windows, is there any way to remove one of them?

EDIT: I'm using Ubuntu 12.04 LTS

---

### Post by darkod on 2012-06-28
Are you sure it says sda0? The number is the number of a partition and it starts counting partitions from 1 so I have never seen sda0.

Otherwise, having 2 win7 entries is not rare. The restore partition also has boot files which get detected and a second entry is created. So one is for the win7 OS, the other is for the restore partition.

If you want more details you can use boot-repair and create the boot info results which will show more details. You can post the link it gives you if you have questions.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by anantanni on 2012-06-28
Ah, yes it was sda1 and sda2, sorry for the mistake.

---

### Post by Mark Phelps on 2012-06-29
If your machine came preloaded with Win7 -- then it actually is in TWO partitions.  The first partition contains the Win7 boot loader components; the second contains the Win7 OS and the rest of the files and directories.

The OS_Prober routine that builds the GRUB menu sees both sets of components, so it puts two entries in the menu.  IF you remove the WRONG entry, you will not be able to boot Win7.

---

### Post by darkod on 2012-06-29
> **Mark Phelps said:**
> If your machine came preloaded with Win7 -- then it actually is in TWO partitions.  The first partition contains the Win7 boot loader components; the second contains the Win7 OS and the rest of the files and directories.

The OS_Prober routine that builds the GRUB menu sees both sets of components, so it puts two entries in the menu.  IF you remove the WRONG entry, you will not be able to boot Win7.

This is not entirely true Mark.

It only detects the boot files, so it will make only one entry in the boot menu.

Usually the second entry is the restore (recovery) partition because it also has boot files present on it.

I have win7 with the small System Reserved partition on my netbook and I have only one entry for win7 detected by os-prober. I always had only one entry.

---

