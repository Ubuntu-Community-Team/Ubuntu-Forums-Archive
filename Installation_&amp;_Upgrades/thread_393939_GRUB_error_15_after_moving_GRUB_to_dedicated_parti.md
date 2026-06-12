---
title: "GRUB error 15 after moving GRUB to dedicated partion"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by ernstblaauw on 2007-03-26
As I want to move my Linux partition to another hard drive, I first wanted to separate GRUB on a dedicated partition.
I followed [this guide](http://www.troubleshooters.com/linux/grub/grubpartition.htm). I made a partition for GRUB (at my fourth hard drive, the second partition) and copied the necessary files, including my existing menu.lst, to the partition. After that, I typed in a terminal:
```
# sudo grub
grub> root (hd3,1)
grub> setup (hd0)
grub> quit
# reboot
```
That went al ok. The computer restarted and the GRUB menu came up. However, if I select my Ubuntu or Windows XP installation, I got the error:
> Error 15: File not found
I searched using Google and found out, that usual, the error is caused by a missing kernel (pointing to the faulty one). But when I entered the GRUB command line, GRUB automatically entered the name (by using the tab). So, I guess the file is there (and that is logically, as my Ubuntu installation did not move).

As my linux installation is at sda6 (hd1,5), I repointed the MBR to that entry. As expected, the 'old' GRUB just works. However, I still want to install GRUB on a dedicated partition. Am I missing something? How can I solve the error 15?

---

### Post by saphil on 2007-03-27
You might want to look at 
[http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656)

I got it from googling grub error 15.  Without knowing what partitions you have, I would guess that the "grub counts from zero" is involved. "hd0,5" ???

---

### Post by ernstblaauw on 2007-03-28
> **saphil said:**
> You might want to look at 
[http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656)

I got it from googling grub error 15.  Without knowing what partitions you have, I would guess that the "grub counts from zero" is involved. "hd0,5" ???

No, I don;t thin counting is the problem: I have a PATA drive as /hdc, which is (hd0) in GRUB. I solved this by making a partition on my first hard drive. Now, everything works fine.

---

