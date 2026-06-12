---
title: "Feisty installer doesn't recognize my existing partitions"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by BruceBerry on 2007-04-21
I'm trying to install FF on a dell inspiron 6400 laptop. EE is already installed on it and works (almost) flawlessly. Since i had smooth install for EE i tought installing FF was going to be rather easy... well i've experienced a huge regression (by the way, i stumbled into a nasty bug which will prevent linux newbies having an ATI x1400 to install/use FF, nice...): when i have to configure my disk to choose where to install kubuntu, the installer doesn't recognize my existing partitions :-(
I should see/dev/sda with a few partitions (EE, EE spaw, windows NTFS, FAT32 "bridge", etc)... instead i only see an empty sda!
Thus, in order to install kubuntu i'd have to wipe out all my data! I just wanted to install FF on the partition where EE is (EE is a rather fresh install so i won't bother upgrading), but i really don't know how to do this...

---

### Post by carpex on 2007-04-21
Interestingly, I get the same problem with the same computer. I also had to cope with the annoying x1400 bug with xorg, what a pain!

I got not response in my thread on this...

[http://ubuntuforums.org/showthread.php?t=415274](http://ubuntuforums.org/showthread.php?t=415274)

My intuition is that it has something to do with the weird way Dell creates all the recovery and mediadirect partitions, and the way our original install of Edgy was done (I upgraded from Edgy to Feisty) I see that in my case sda4 and sda6 start at the same block, which doesn't seem to make sense...

Hope somebody can help...

GL

---

### Post by sigg.switz on 2007-04-21
I am also having this problem...It pretty annoying that it wont recognize my partitions...I wont install ubuntu if I cant dual boot to xp

---

### Post by BruceBerry on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/108562](https://bugs.launchpad.net/bugs/108562) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				here's my partition list:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14333       14594     2096128    c  W95 FAT32 (LBA)
/dev/sda2   *          12        1031     8193150    7  HPFS/NTFS
/dev/sda3            1032       14592   108928732+   f  W95 Ext'd (LBA)
/dev/sda5            1032        3581    20482843+   b  W95 FAT32
/dev/sda6            3582        3842     2096451   82  Linux swap / Solaris
/dev/sda7            3843       14592    86349343+  83  Linux

```

btw, i also opened a bug report:
[https://bugs.launchpad.net/bugs/108562]("https://bugs.launchpad.net/bugs/108562")
please let me know if you find a way to keep your partitions :-)

edit:
parted gives me this error when i try to list the partition table:
"Error: Can't have overlapping partitions."
Maybe there's a way to fix it? Partition Magic for Windows?

---

### Post by BruceBerry on 2007-04-21
partition table doctor did the trick. The computer doesn't boot anymore, but i guess i just need to rewrite the MBR... now partitions are shown in the installer!
I haven't really checked if my windows partition is fine tough...

---

