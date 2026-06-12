---
title: "converting systempartition from dynamic to basic"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by cjmyl on 2010-11-23
From a friend I received a cdrom with Ubuntu 8.10 and recently I tried to install it on my laptop. The installation failed and moreover the volumetypes of the partitions, including the system partition, on my disc have been changed from "basic" to "dynamic" which is very annoying because now I cannot restore my backup. I have now spend a couple of days trying to restore my disc back to its original state but to no avail. Can anyone tell me how to change the volumetype of the systempartition (which cannot be deleted !!!) from "dynamic" back to "basic".
My PC is a Dell Vostro 1720 with Windows 7.

---

### Post by dino99 on 2010-11-23
run a formatting tool to see your partitions (dont format, only see the whole image)

then check them

---

### Post by srs5694 on 2010-11-24
It's very doubtful that an Ubuntu installer would change the partition types from "basic" to "dynamic," since the latter is a Microsoft-only partitioning system; AFAIK, no Linux tool can create or manipulate Microsoft dynamic partitions. To be sure of what you've got, I recommend booting the Ubuntu installer in "live CD" mode, opening a text-mode shell (Terminal), and typing "sudo fdisk -lu". This will show the partition table data. Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility, if you need help interpreting the data.

That said, the Windows [Partition Wizard](http://www.partitionwizard.com/) tool is supposed to be able to convert MS dynamic disks into basic disks. I've never used this tool, though, so I can't vouch for it; I'm just passing on a reference I came across some time ago.

---

