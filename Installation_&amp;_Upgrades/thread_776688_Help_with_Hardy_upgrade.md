---
title: "Help with Hardy upgrade"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by bruceb85 on 2008-04-30
After a great experiance with Gusty(7.10)dual boot with XP, I decided to try to upgrade to Hardy. After upgrade everything apeared ok but I had no sound. After checking the obvious things,muted channels and the like still no go. Read many threads about sound problems but no help. I even installed Kubuntu programs with no success. I even had it crash on me which never happened before. So now what I would like to know is what is the best way to remove that install and reinstall from a CD without messing with my XP side? Besides the partition that Hardy is installed on, what do I do with the swap partition and also GRUB? Thanks in advance.

bruceb

---

### Post by Pumalite on 2008-04-30
You can install the new Hardy over the old one. Go Manual and choose the old partitions. Ignore /swap. The installer will do the rest. You will have a new Grub with dual boot.

---

### Post by bruceb85 on 2008-04-30
Thanks, I'll give it a shot.

---

### Post by Pumalite on 2008-04-30
Good luck.

---

### Post by bruceb85 on 2008-04-30
In Edit partition, I chose to use my sda3 ext3 partition. I guess I need to choose to use as ext3 journaling file system, format the partition then mount point /. Am I correct?

---

### Post by Pumalite on 2008-04-30
Yes.

---

### Post by bruceb85 on 2008-05-01
The fresh install went very well except still no sound with Rythembox and videos. When I do the Hardware testing I hear sound. When I do the testing in ALSA, I hear nothing. I need sound for online videos and CD's. With Gustsy, I had no problems with this. What could they have changed to mess that up? If I can't solve this soon I may try to go back to Gutsy.

---

### Post by bruceb85 on 2008-05-07
Looks like I found a fix for may sound problems. It actually affected Rhythm box, and other players. I uninstalled anything pulse audio. Now everything works now.

---

### Post by Pumalite on 2008-05-07
Good for you!

---

