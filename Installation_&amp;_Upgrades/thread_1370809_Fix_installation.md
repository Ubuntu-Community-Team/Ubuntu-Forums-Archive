---
title: "Fix installation"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by ZeldeR on 2010-01-02
Hello community, I have a dual-boot installation of Ubuntu /Windows Xp and my Windows is death (bluescreen :lolflag:). How can I reinstall (not recover) Windows without loose of Ubuntu - it's my primary OS?

Thx very much!

---

### Post by ZeldeR on 2010-01-03
It was very simple, I thought it is very tricky and was a little bit afraid.

my solution, maybe it could be helpful for somebody :) :

[PHP]
sudo mkdir /mnt/sda1
mount /dev/hda1 /mnt/sda1
grub-install --recheck --root-directory=/mnt/hda1 /dev/hda [/PHP]

---

