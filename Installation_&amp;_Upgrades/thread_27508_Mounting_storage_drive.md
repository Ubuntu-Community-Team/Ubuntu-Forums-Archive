---
title: "Mounting storage drive"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by eqisow on 2005-04-16
OK, recently got Ububtu installed, and it's going pretty well so far... except for the fact that I can't seem to mount my storage drive. I have 2 disk drives, the first is a sata drive (sda) and has a linux and windows partition on it. I was able to mount the windows partition as sda2, no problem. However, I'm being told my storage drive (hda1) does not exist when i try to mount it... it mounts under Knoppix no problem. Any suggestions? :\

---

### Post by bored2k on 2005-04-16
[QUOTE=eqisow]OK, recently got Ububtu installed, and it's going pretty well so far... except for the fact that I can't seem to mount my storage drive. I have 2 disk drives, the first is a sata drive (sda) and has a linux and windows partition on it. I was able to mount the windows partition as sda2, no problem. However, I'm being told my storage drive (hda1) does not exist when i try to mount it... it mounts under Knoppix no problem. Any suggestions? :\[/QUOTE]
 > sudo fdisk -l

What is the output ?

---

