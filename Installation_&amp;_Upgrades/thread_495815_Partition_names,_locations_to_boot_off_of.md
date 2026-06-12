---
title: "Partition names, locations to boot off of"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by XGC75 on 2007-07-08
Hey all,

I just upgraded to Feisty from Edgy, where I was using Grub to boot to my Linux/XP partitions. Having upgraded however, my menu.lst has been modified such that the XP partition is missing (and it deleted my menu.lst.backup:mad:)!! 

Well now I need the partition name (hd0,2 etc.) and the location of the kernal so I can write it back into menu.lst. I believe, since the XP partition is the original partition, that the location is hd0,0. I've tried to confirm this with GParted but didn't find the info I needed. So my question is: How can I find the name of the partition and the location of the kernal from which to boot?

Under any other circumstances I would not mind running Ubuntu for the rest of my life. Unfortunately for me I need to run some essential windows-based programs :sad:. How long do you all think it will take for Ubuntu to run mainstream? We already have Dell on our side ;)...

---

### Post by merlinus on 2007-07-08
You might try this in a terminal:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute your results for (hdx,x).

If this does not work, SuperGrub should:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

