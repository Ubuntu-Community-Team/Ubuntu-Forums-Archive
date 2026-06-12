---
title: "installation screw up, grub not working &amp; not finding partitions"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by raul on 2006-06-04
So here's the story:

I had dual boot with breezy and windows xp, and attempted to do a fresh install of dapper. I first encountered this problem with the dapper live cd: [http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115). I was finally able to run the live CD, but then at the middle of the installation there was a pop-up about some error in one my disks. I was prompted to quit or proceed, and I decided to quit. When I rebooted, grub was not working (it displayed 'error 15'). And I couldn't run the dapper live cd; it kept coming back to the original error: [http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115).

I haven't been able to repair grub or to make the dapper live cd work. To repair grub, I tried the following: I went onto a terminal with the knoppix live cd and entered this (my breezy partition was hda3, i believe):

```
grub
root (hd0,2)
```

I got back the following:

```
Error 21: Selected disk does not exist
```

I've also tried with (hd0,0) and (hd0,1), but I get the same error. On the other hand, I haven't been able to run the dapper live cd. 

Any help on getting back grub (so that I can at least access windows!) or on how to make the dapper live cd work would be greatly appreciated.

---

### Post by r4ik on 2006-06-04
Please read Herman's post here,

[http://www.ubuntuforums.org/showthread.php?t=187153&highlight=restore+grub](http://www.ubuntuforums.org/showthread.php?t=187153&highlight=restore+grub)

Hope it helps.

Good luck.

---

### Post by raul on 2006-06-04
thanks. i ended up reinstalling breezy, and that restored GRUB.

---

