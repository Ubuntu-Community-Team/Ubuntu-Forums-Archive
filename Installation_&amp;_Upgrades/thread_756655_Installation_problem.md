---
title: "Installation problem"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by rakeshkestwal on 2008-04-16
I have windows xp on my notebook compaq presario v2000. (40 GB Hard disk C drive 20 GB Half empty, 1.3 GHz Processor, 1.25 GB RAM). I tried to install Ubuntu linux for dual boot. On ubuntu webpage it is mentioned that for partitioning i will get 4 options of which i should select " [SIZE="5"]Guided resize and use free space[/SIZE]". But i got only three options in my cd. And the option I was suppose to use was missing, which was the most important and required for dual boot. 
So i had to abort my Ubuntu installation as using any other option could have effected my current xp installation or might have formated my whole notebook. So any comment why the dual boot partitioning option was absent in my ubuntu cd. Or there is some thing to be activated in my notebook setting to enable dual boot. Please help!!!

---

### Post by tommcd on 2008-04-16
> **rakeshkestwal said:**
> I have windows xp on my notebook compaq presario v2000. (40 GB Hard disk C drive 20 GB Half empty, 1.3 

Does this mean that the whole drive is formatted as NTFS and 20GB is unused, or that you have XP installed to a 20GB partition and the rest of the disk is unallocated. I assume it is the former, since most computers shipped with Windows have just one big NTFS partition, with perhaps a small recovery partition. If that is the case, select RESIZE, since you will want to shrink the XP partition to make room for Ubuntu. Be sure to defrag XP first.

---

### Post by erginemr on 2008-04-16
You have acted very wisely, as quite a few people had the misfortune of wiping their Windows partition accidentally this way. So, in addition to the above suggestion, which is %100 correct (and underlining the importance of defragmenting your hard drive first before the resizing from under Windows XP), I can suggest two more visual Ubuntu installation guides for you to review:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://mbalat.blogspot.com/2007/11/ubuntu-710-installation-walkthrough.html](http://mbalat.blogspot.com/2007/11/ubuntu-710-installation-walkthrough.html)

---

