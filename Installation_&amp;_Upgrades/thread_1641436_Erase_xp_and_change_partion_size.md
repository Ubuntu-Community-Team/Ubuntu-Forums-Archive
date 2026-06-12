---
title: "Erase xp and change partion size"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by BadboyXD on 2010-12-09
[COLOR=Blue]Hey guys,

Have a question about partitioning,
I installed ubuntu from the live cd,
and I have xp on here to so I can boot on either one at startup.
Now I want to get rid of the xp partition and just have one big ubuntu partition.
Is there a way to do this?[/COLOR]

---

### Post by sikander3786 on 2010-12-09
You can just delete the Windows XP parition and run this command to get rid of Windows entry in Grub menu.

```
sudo update-grub
```

Instead of resizing the Ubuntu partition, I would suggest to create a new partition in the freed up space and mount that under Ubuntu.

Resizing the root partition is a bit risky and not recommended. If you decide to go that way, make sure you've got strong backups.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by BadboyXD on 2010-12-09
[COLOR=Blue]In your first suggestion is there a way for me to install my programs to the other partition?
Cause it always saves to the main one where Ubuntu is installed. 
This is the reason I wanted to merge partitions I was running out of space, installed alot
of programs.
If not guess I'll have to go with option b which seems like it might remove some of the settings and programs already installed lol.
Something I was trying to avoid, if all else failed I would have done a clean install, but then I would have to reconfigure and download so many things over again.[/COLOR]

---

