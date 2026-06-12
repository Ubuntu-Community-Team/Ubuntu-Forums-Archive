---
title: "Bootup delay"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by peyre on 2012-06-17
I just reinstalled Xubuntu 12.04 from scratch.  Now, on each bootup, it shows a list of choices of operating system versions (current version of Ubuntu, repair version, etc.).  It's set to count down from 6 seconds or so.  How do I set it to skip that (or zero out the time)?

---

### Post by peyre on 2012-06-17
I've attached a quick screenshot.

---

### Post by ajgreeny on 2012-06-17
It looks as though you reinstalled the OS, but did not overwrite the old installation, so now probably have both the old version and the new on the machine.

Can you show the output of ```
sudo fdisk -l
``` in terminal please.

---

### Post by peyre on 2012-06-17
Ah, you might be on to something there!  Actually, what I did was I bought myself an SSD, then installed the OS on there, with the old mechanical disk there for bulk storage--but I haven't erased it, so it must be that it sees both boot loaders or whatever and is offering me a choice.

Once I have everything well established I was planning to wipe everything on the mechanical drive except my old home folder, where my big folders (videos, music, etc.) are.  So I guess this is a temporary condition that will be fixed once I delete stuff from the mechanical drive?  Or is there something extra I'll need to do?  I have a feeling a simple deletion of stuff on the disk might not change that Ubuntu sees it as a bootable disk, causing it to offer me the choice.

```
Disk /dev/sdb: 90.0 GB, 90027220480 bytes
255 heads, 63 sectors/track, 10945 cylinders, total 175834415 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002006b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   167448575    83723264   83  Linux
/dev/sdb2       167450622   175833087     4191233    5  Extended
/dev/sdb5       167450624   175833087     4191232   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c50e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   972582911   486290432   83  Linux
/dev/sdc2       972584958   976771071     2093057    5  Extended
/dev/sdc5       972584960   976771071     2093056   82  Linux swap / Solaris

```

---

### Post by ajgreeny on 2012-06-17
For as long as the old system still sits on sdc grub will continue to show it along with the grub menu at boot time.

If you delete the old system files and leave your old home data folders, then run ```
sudo update-grub
``` it should stop the grub menu appearing in future.

Try it out and then if needed we can discuss moving all the files from the folder on that partition to the root of the partition, so they will not be on for example /media/disk/username/foldername but just /media/disk/foldername.

---

### Post by peyre on 2012-06-17
> **ajgreeny said:**
> For as long as the old system still sits on sdc grub will continue to show it along with the grub menu at boot time.

If you delete the old system files and leave your old home data folders, then run ```
sudo update-grub
``` it should stop the grub menu appearing in future.

Try it out and then if needed we can discuss moving all the files from the folder on that partition to the root of the partition, so they will not be on for example /media/disk/username/foldername but just /media/disk/foldername.

Ok, thanks!  Now is there anything I need to do besides just deleting files on the root of the drive?  Is there super-secret stuff hidden there that doesn't appear even when I have Thunar display hidden files?

---

### Post by ajgreeny on 2012-06-18
Not that I can think of, but whatever you do, make sure you have backups of all your files before you delete anything permanently, just in case.

---

