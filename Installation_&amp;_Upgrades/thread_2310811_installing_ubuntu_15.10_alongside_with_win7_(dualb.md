---
title: "installing ubuntu 15.10 alongside with win7 (dualboot)"
date: 2016-01-22
forum: Installation &amp; Upgrades
---

### Post by nick239 on 2016-01-22
Hello guys, i'm pretty new to ubuntu world and I want to learn more about it, having it installed as win7 rather than using livecd or so. I got 4 NTFS windows partitions and about 400gb unallocated space. Is it possible to perform clean install of ubuntu 15.10 on this unallocated space (with making linux partitions) and not to "disturb" windows partitions with all data there?
Recently an idea came to me to install ubuntu through wubi, it would save me from all the mess with partitions, but forum posts say that it is no longer supported since 2014 or so, I decided not even to try using older builds. I don't want to install linux as the only OS mainly because working on pc for me means using many windows-only programs (and games, sometimes), not sure about stability if run with wine.
Thanks.

---

### Post by Dreamer Fithp Apprentice on 2016-01-22
Sure, that'll work. Just boot from the live disk. Pay attention to the instructions/questions that come up and think before you click and you'll be fine. Be especially careful when you come to the partitioning part. The defaults there suck. Choose "I want to do something else" or some choice with a label like that. Then choose the unallocated space, being careful you don't choose some other partition, select to be used as an ext4 filesystem, to be mounted as /, to be formatted. If you have more than 2 gb of RAM, I wouldn't assign any drive space to swap. From there on out it is all pretty intuitive. There are other approaches, but that works.

---

### Post by nick239 on 2016-01-22
I guess Ubuntu considers partition "borders" differenty from win7, in win7 I got 409gb unallocated but in ubuntu I got 439gb.
I got 439624mb "free space" at partitioning step, I try to create logical partition at the beginning of this space in ext4 mounted as /, but at the field "size" i got preset 439625mb, this 1mb difference confuses me, do I need to leave it as it is? I guess I set other settings correctly.

UPD. Now I see that if u didnt press "Install", all changes would be reversible, so it's all ok.
UPD2. Where should I install loader? To /dev/sda?
UPD3. Discovered that GRUB2 should be installed to MBR if I havent mistaken, so I think I made the right choice.

Seems that all went better than expected, and I've managed to make it through. GRUB2 functions well and both Ubuntu and Win7 boot and work. Thanks a lot. This is where I start :D

---

### Post by Dreamer Fithp Apprentice on 2016-01-22
Congrats. It would be good if you'd mark your thread "solved" in the thread tools menu.

---

