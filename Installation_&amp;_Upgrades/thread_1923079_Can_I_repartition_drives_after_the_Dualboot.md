---
title: "Can I repartition drives after the Dualboot?"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by georgeqwu on 2012-02-09
Hello everyone, I just dualbooted Ubuntu 11.10 alongside Windows 7 and realized that i actually don't need that much room. Is there any way I can repartition the two drives and move over more space from the Ubuntu side to the Windows side without putting any files on either side at risk?

Thanks guys!

George

---

### Post by Mark Phelps on 2012-02-10
Don't have enough info to answer your question -- as dual booting can be accomplished in two very different ways:
1) Installing Ubuntu from INSIDE Windows -- using Wubi
2) Booting from CD/USB and installing Ubuntu directly to its own partition(s).

If you did 2), you're talking about resizing partitions -- and the awful truth is that ALWAYS involves risk of data loss.

To let us see what your drive formatting looks like, open a terminal in Ubuntu and enter "sudo fdisk -lu" (lowercase L, not a one), and post the results back here.

---

### Post by georgeqwu on 2012-02-10
Hey thanks so much for helping out. :-/ is there a clean way to do this? thanks!
[IMG]http://i287.photobucket.com/albums/ll153/macdrenalds/Screenshotat2012-02-10155231.png[/IMG]

---

### Post by darkod on 2012-02-10
As Mark already mentioned, resizing partition always carries some risk.

Besides, you have about 17GB for the ubuntu system partition (root) and you can't shrink too much from it without leaving it without space to work with.

It's probably not worth the risk resizing for the small gain you can get from it. If you are starting to run out of space, I would start considering buying a new hdd, internal or external. That will expand your storage.

---

### Post by cortman on 2012-02-10
You can safely resize Linux partitions using GParted, but like was said- it always carries risk of data loss. I can't overstate the importance of doing regular backups on any files you don't want to lose. Maybe you can use this to start a good backup habit.
I would not recommend realizing Windows partitions with Ubuntu though, as Windows tends to be very finicky about non-Windowa utilities messing with it's partitions. Resize Windows with Windows, Ubuntu with Ubuntu, and MAKE A BACKUP before you try either.

---

### Post by MAFoElffen on 2012-02-11
> **cortman said:**
> You can safely resize Linux partitions using GParted, but like was said- it always carries risk of data loss. I can't overstate the importance of doing regular backups on any files you don't want to lose. Maybe you can use this to start a good backup habit.
I would not recommend realizing Windows partitions with Ubuntu though, as Windows tends to be very finicky about non-Windowa utilities messing with it's partitions. Resize Windows with Windows, Ubuntu with Ubuntu, and MAKE A BACKUP before you try either.
All the above (especially Darko)...

You can resize NTFS with Windows.  If you do it with GParted, the next time you open Windows it will whine about broken indexes (can be repaired.) You can resized the other partitions with Gparted... 

Cautions- Any shrink-move-resize there is risk of data loss. Darko mentioned 17GB.  Yes you can install in under 10GB, but... My Linux sys partition is 130GB used.

---

