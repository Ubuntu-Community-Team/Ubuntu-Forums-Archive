---
title: "bigger swap"
date: 2023-05-25
forum: Installation &amp; Upgrades
---

### Post by ksso on 2023-05-25
[COLOR=#000000]Suggestion or question[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]is there a way to install luks (*encrypted*) with more swap (min. 8-10 gb) or to manually increase it?, because right now this installation freezes the laptop once the ram (and assigned swap I guess) is used (by the way this also happens with the standard installation without manual partition for bigger swap)[/COLOR]
[COLOR=#000000](HP Laptop 15-ef2xxx (612B7LA#ABM) AMD Ryzen 5 5500U with Radeon Graphics ddr 4gb)[/COLOR]
[COLOR=#000000]Thank you[/COLOR]

---

### Post by TheFu on 2023-05-26
No easy way, but if you install using LUKS, you will get LVM2 objects to hold all the stuff inside the encrypted container.

Immediately after the fresh install, you should reduce the LV used for the root file system - 35GB is what I use.  

Then manually create some LVs for /var, /home, and swap of the size you think you'll need for the next 90 days.  Don't allocate any more storage, just 90 days worth.  This will let your system and through LVM be resized up where and when needed.  For an SSD system, try to never use more than 80% of the storage to drastically extend the SSD lifespan.  Some of the most powerful aspects of having LVM is the ability to create snapshots for a number of reasons.  That means leaving empty space in a VG, so it can be used in a temporary way for snapshots.  Mainly snapshots are used for getting perfect, uncorrupted, backups, but there are other uses.

For nearly every system, 4.1GB is the "correct" answer for how large swap should be.  RAM is relatively cheap, so it is not hard to put 64GB of RAM into almost every system these days.  The only people needing that amount of RAM are java programmers and deep learning people.  Certainly nobody using a laptop.

There is a problem with having too much swap.  Best to read up on swap and how it actually gets used.

---

