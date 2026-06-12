---
title: "[SOLVED] Read from another partition"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by emotionlovesyou on 2008-03-29
The only way i can get Ubuntu to run is from the live CD. It looks like I have to reinstall, but I want to backup all my files before anything else goes wrong. However I can't get to the partition where my previous installation is.

How do I browse other partitions from the Gutsty Live CD?

---

### Post by Pumalite on 2008-03-29
You have to mount them.
Post from your Live CD, at the Terminal:
sudo fdisk -lu

---

