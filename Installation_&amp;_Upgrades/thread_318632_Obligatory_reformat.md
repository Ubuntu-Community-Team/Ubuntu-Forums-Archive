---
title: "Obligatory reformat"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by smartov on 2006-12-14
I was very confused that ubuntu installation forces me to reformat partition I want to use as root partition... It has a lot of important data and I have no other option where to put it.
This is very strange and bad style. :-? 
Why Ubuntu wants to reformat it?! :confused:  It has ext3 filesystem, everything is correct but anyway I need to reformat. :mad: 
I can't install ubuntu in such conditions. This is really stupid... 
FC doesn't do that. Will have to install it.

---

### Post by doobit on 2006-12-14
> **smartov said:**
> I was very confused that ubuntu installation forces me to reformat partition I want to use as root partition... It has a lot of important data and I have no other option where to put it.
This is very strange and bad style. :-? 
Why Ubuntu wants to reformat it?! :confused:  It has ext3 filesystem, everything is correct but anyway I need to reformat. :mad: 
I can't install ubuntu in such conditions. This is really stupid... 
FC doesn't do that. Will have to install it.

I'm not sure why you think that. Ubuntu doesn't force you to do anything. If you use the last choice in the partition manager of manually setting up your partitions, then you can choose to format, or to keep the data on the partition. Each of the things in the list for each partitions has options. 
You really should create another partition for /home anyway. Then you will never lose your settings, and you can put stuff that you download on that partition and not loose it if you change your root partition.
You can do all of that with the partition manager if you choose to edit the partitions manually. This also lets you make a swap partition, so you can run bigger programs faster on less RAM.

---

### Post by rexa on 2006-12-14
not true, just ran into that myself, the installer forces you to reformat the designated / partition

---

### Post by K.Mandla on 2006-12-15
I believe on the alternate (installation) CD, you have the option to disable reformatting. I usually set up partitions with ext3 and the dir_index option, and when the partitioner detects a preformatted partition, it automatically defaults to no-format. (You can reformat it, if you like.) Swap seems to be the exception there.

I don't use the live CD often enough to remember if that option is there.

---

