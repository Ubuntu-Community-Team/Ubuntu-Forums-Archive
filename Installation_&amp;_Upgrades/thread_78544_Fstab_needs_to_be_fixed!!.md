---
title: "Fstab needs to be fixed!!"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by CastleKingSide on 2005-10-18
I wanted more space for ubuntu so I deleted another partition (hda3) and resized hda2 (where ubuntu lies), I did that on a Live cd, when I rebooted ubuntu seems unhappy, This is not a huge problem, I know there is a way to have my fstab rebuit using only apt-get something and a command...does any one can help me?
Thanks a lot!!!

---

### Post by mlomker on 2005-10-18
I don't know any simple commands, but I'm sure there are some.

**sudo fdisk -l** will give you a list of partitions and you could use **sudo nano /etc/fstab** to edit them.

---

### Post by CastleKingSide on 2005-10-19
Hey thanks that worked just fine! 
but I am curious to use the package to do this, does any one knows that???

---

