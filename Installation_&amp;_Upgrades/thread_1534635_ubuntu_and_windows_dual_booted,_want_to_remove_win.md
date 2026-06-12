---
title: "ubuntu and windows dual booted, want to remove windows"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by themordy on 2010-07-19
I used wubi to install ubuntu 10.04 alongside windows. my windows has issues and rarely boots up properly. so i have decided that i want to remove it all together so i can have the disk space back. my question is, how do i remove windows? so i have to completely do a fresh install of ubuntu? i have the disk, but i don't want to end up with yet another partition. i also have about 1000 songs that i have already transfered from window to ubuntu that i don't want to have to replace. so, is it possible just to dump windows after installing ubuntu using wubi? if so, what is the easiest way to do it and get my disk space back?

---

### Post by dv3500ea on 2010-07-19
Wubi installs ubuntu inside of Windows so you will have to install from scratch.

---

### Post by themordy on 2010-07-19
sad days. alright, thanks for the info.

---

### Post by kennedyvelez on 2010-07-19
ayt. Install from scratch. Linux format really formats your drive while windows hide some files when you do the format thing. Do it with no regrets.

---

### Post by bcbc on 2010-07-19
I wrote up a [method]("http://ubuntuforums.org/showpost.php?p=9570445&postcount=12") to convert a wubi install direct to partition using just the root.disk file and a live CD. It's very hands-on and requires that the root.disk be moved to an another partition or external drive first (so you can format the partition it is currently installed on).

If you are going to back up all your data anyway and doing a format and fresh install, it shouldn't hurt to try this first. (But definitely back up before trying the manual migration).

There is also an [automated wubi migration script]("http://ubuntuforums.org/showthread.php?t=1519354") but this has to be to run from the booted wubi - therefore it can't overwrite the partition that wubi is currently installed on.

Whether or not this is a practical solution for you - you can decide.

---

