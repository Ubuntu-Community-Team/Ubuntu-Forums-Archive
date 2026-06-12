---
title: "[SOLVED] No space to upgrade to Intrepid"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by alexmoon on 2008-11-06
I can only upgrade through update manager, because my CD drive is broken and my (very old) laptop can't boot from USB. 

However, whenever I try it tells me that I need a few more K of space on /

I've tried:
* deleting old linux-images through synaptic [[any of you having the same problem who find this thread, that can be achieved by opening synaptic, searching for 'linux-image', then removing all but the latest (and latest-bar-one for safety) images]],
* sudo apt-get autoremove
* sudo apt-get clean.

As I said, I only need a little more space, and I was wondering if there's anything else I can try. I have both linux-image-2.6.24-21-generic (which has 2.6.24-21.43 as the installed version) and linux-image-generic (installed version 2.6.24-21.23) - can I delete either of these? Is there anything else that I can try?

---

### Post by Super Jamie on 2008-12-01
try deborphan, it can find useless stuff that autoremove sometimes can't

```
sudo apt-get install deborphan
sudo apt-get purge `deborphan --guess-all`
```

you can run just ```
deborphan --guess-all
``` to see what it wants to remove, and can exempt a package from removal with ```
sudo deborphan -A packagename
```

you also may wish to have a look through baobab (Accessories -> Disk Use Analyzer) to see if anything's taking up an inappropriately large amount of space it shouldn't. perhaps you have a big heap of logfiles in /var/log which can be removed

does anyone know how much space is required to upgrade to intrepid from hardy?

give us the output of ```
sudo fdisk -l
``` (list all drives and partitions) and ```
df -h
``` (diskspace free, human-readable) to get a grasp of your partitioning scheme

if you have /home on the same partition as /, are you able to stick your personal stuff on a usb drive for the upgrade? or even look into cleaning out ~/.thumbnails/, which can take up alot of space if you play with pictures alot

---

### Post by alexmoon on 2008-12-03
Thanks Jamie - deborphan worked...Intrepid seems to be seriously misbehaving, but I'll have a look around the forums and see if I can sort it out.

---

