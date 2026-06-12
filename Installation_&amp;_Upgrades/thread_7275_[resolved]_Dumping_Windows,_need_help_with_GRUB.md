---
title: "[resolved] Dumping Windows, need help with GRUB"
date: 2004-12-05
forum: Installation &amp; Upgrades
---

### Post by bazuka on 2004-12-05
My plan is to finally do away with Windows completely. To do this correctly, I will need to use Partition Magic to move my EXT3 FS to the beginning of the drive. Can I modify GRUB before I go out for the last time, then do my thing and come back without problems? My vision is to not lose everything, as I've put a good bit of work into this build.

Is the first partition on the drive going to be HDA1 or HDA0? I assume it will be hda1, but I want to make sure before I change it.

In any case, if I can't get it to boot, can I use the live CD as kind of a recovery console?

---

### Post by alekandr on 2004-12-05
the first partition on your drive is always hda1.

you MBR is hda // incase you were wondering where to install grub to, i cant offer any advice on grub as i use lilo and only that. ive never like grub, i currentyl have lilo booting my ubuntu os

and yes! any linux live-cd or install cd at that, can be used as a recovery console, not all though, but all LIVE-CD's will :D

---

### Post by bazuka on 2004-12-05
Whoops.

That didn't work the way I wanted it to. I thought Partition Magic said "Extended" when it actually said "Ext3."  I deleted the wrong partition.

---

### Post by az on 2004-12-05
You could have just used the Ubuntu installer to delete and move partitions around.  You could have also just booted and edited the grub menu(from within grub...) the first time around.  Then edited the menu.list

---

