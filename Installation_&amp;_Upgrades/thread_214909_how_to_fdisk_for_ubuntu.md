---
title: "how to fdisk for ubuntu?"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by LinuxDeaf on 2006-07-13
i used my pc ubuntu. i want remove harddisk from ubuntu after i want install ubuntu.. can use fdisk? or not? let me know.... HELP

Thanks

LinuxDeaf

---

### Post by Radioactive Fellow on 2006-07-13
Correct me if I am wrong, what you are trying to do is to set up the partitions [COLOR="DarkRed"]before[/COLOR] you install Ubuntu?

If that is what you want, then you can do it without using fdisk.
While installing Ubuntu you will have to set up the partitions you want, there you can remove all existent partitions or the chosen ones, create some new, etc.

Using fdisk can get tricky since you can erase things you dont want but anyway:

1. Use Ubuntu/Kubuntu live to boot
2. fdisk /dev/hda

On the screen pres m for help with the commands.

Again, you can do it using ubuntu instalation

I hope this was what you were looking for

---

