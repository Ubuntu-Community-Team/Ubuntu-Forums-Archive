---
title: "Attempting to install on Toshiba AC100, got stuck at repartitioning process"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by Iron_Mew on 2013-08-14
I was given an AC100 by a friend who didn't want it running on Android at all, with the task of wiping it and installing Ubuntu. Figuring I didn't need the Android partitions I followed to the letter [this guide](http://ac100.grandou.net/repartition_mmc) to get back the internal memory occupied by the unneeded partitions. I did make a full backup before this, according to [these instructions](http://ac100.grandou.net/backups); this includes the partition table (converted to cfg) and bct file.

Here is my repartition script, edited with the appropriate .cfg file name (the cfg is the same you find on the repartition guide, only there it's called part.cfg) and location of the nvflash and bin files: [http://pastebin.com/DLB8h6tC](http://pastebin.com/DLB8h6tC)

And here is the console output: [http://pastebin.com/5QyRfrjy](http://pastebin.com/5QyRfrjy)

At this point it dumps me back to the console. I tried uploading fastboot again manually to regain control of the AC100 and either resume the process or restore the full backup and start from scratch, but this happens: [http://pastebin.com/SjbffjCc](http://pastebin.com/SjbffjCc)

I can't figure out what caused the script to fail; from what I can see all the files are where they should be. What do I do now? How do I regain control of it so I can at least do a full backup?

---

### Post by Boab1993 on 2013-08-14
Sounds like a corrupt file?

Try redownloading the NVflash files and trying again.

I have no idea how you'd regain control as such. But im sure someone on here will help you

---

### Post by Iron_Mew on 2013-08-14
I tried reinstalling nvflash and its files. Didn't help.

---

### Post by Iron_Mew on 2013-08-24
Bumpty bump. I still haven't figured out how to fix it.

---

