---
title: "install on a partition"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by Brizlitman on 2011-09-10
i just made a 15gig partition using windows on which i wish to install ubuntu 11.04 via the cd. Which mount point should i use

---

### Post by JRV on 2011-09-10
You can't create a Linux partition in Windows.
Are you trying to do a WUBI install?

If yes: Sorry I don't know WUBI enough to help.

If you are trying to do a full installation:

Delete the 15gig partition 
Run the Ubuntu installer and choose the option to install to the largest unused space.

Your main system mount point must be /, but the installer will do that for you.

---

### Post by srs5694 on 2011-09-12
Be aware that many Windows pre-installations consume all four primary partitions available on the Master Boot Record (MBR) partitioning system. If your computer was one of these, then when you created another partition for Linux, the Windows partitioner will have converted the disk to use Windows' own [Logical Disk Manager (LDM)](http://en.wikipedia.org/wiki/Logical_Disk_Manager) system. I don't know if it's possible to install Linux to an LDM disk. If it is possible, it would involve some extra hoops through which to jump. If you've done this conversion, your best bet is to reverse it, but the standard Windows tools won't do the trick. The [EaseUS Partition Master](http://www.partition-tool.com/personal.htm) and [Partition Wizard](http://www.partitionwizard.com) Windows programs can supposedly do the conversion, but I've never used either of them, so I can't promise they'll work.

If you're lucky, though, you'll have started with just two or three partitions and gone to three or four, in which case you won't run into these problems.

If you're uncertain of what happened, you should boot the Ubuntu installer into its "try it now" mode, launch a Terminal program, and type:

```

sudo fdisk -lu

```

Post the results here, either as an attachment or between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

---

