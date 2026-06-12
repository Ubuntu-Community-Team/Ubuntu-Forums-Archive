---
title: "Kubuntu live DVD install errors"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by donkey42 on 2006-08-09
booted the live DVD ok, and clicked "install" (on either desktop or kmenu)
all goes fine untill i manually edit partition table```
Critical error during ped_disk_new
``` when this happens the qtparted error appear twice and i can continue as normal and i allocate existing partitions as:
[LIST][*]hda6, 10Gb, /
[*]hda5, 1Gb, swap
[*]hda1, 6Gb, /home/
[/LIST]and install crashes usually, but this time it asked if i want to use full disk or manually edit partition table (again)

i would normally have installed on entire disk, but i've got a 20Gb partition containing .ISO images and stuff, i don't want to have to redownload them

---

### Post by donkey42 on 2006-08-10
sorted it, by deleting the existing partitions, i was trying to install to and installing kunbuntu to largest continous free space

---

