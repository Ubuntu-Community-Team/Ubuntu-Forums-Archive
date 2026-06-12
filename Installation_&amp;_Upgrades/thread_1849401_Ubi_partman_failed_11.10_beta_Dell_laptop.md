---
title: "Ubi partman failed 11.10 beta Dell laptop"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by arpit22x on 2011-09-24
Hello,

I am a big lover of Ubuntu, so I need to install ubuntu 11.10 beta on my Dell Inspiron Laptop.

When 11.10 Beta 1 came up, and now after beta 2, I tried to install 11.10 in a separated partition where 10.10 in already (temporarily) installed. BUT it is giving the error 'ubi partman failed with exit code 141' while installation. and installation fails down.

Is it a bug in 11.10 or I have to wait for final version of 11.10? I googled this problem but seems that nobody is facing this problem in installing 11.10. Please suggest.

Arpit

---

### Post by dino99 on 2011-09-24
still in beta state but usable. If you want to replace natty by oneiric:

sudo gedit /etc/apt/sources.list

there, change natty by oneiric, and comment "third paty repo" if any. close and update, then you are ready to upgrade.

If you want natty+oneiric, then create its partition (/) as you can share both swap and /home partitions (dont format them of course as you have your data & settings there)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

note: always do partitioning after booting on a livecd

---

### Post by Blasphemist on 2011-09-24
What choices did you make on the disk allocation screen? I'd choose to manually choose the partition, and edit the partition to tell it to use EXT4 and set the mount point as / and I would choose to format the partition.

---

### Post by arpit22x on 2011-09-24
Yeah! Me also choosing the same thing manually. I have a live cd of 10.10 so I installed that by doing this (choosing manually and making ext4) only and it didn't create any problem but this is not the things for 11.10 beta1 or 2.

---

### Post by Blasphemist on 2011-09-24
> **arpit22x said:**
> Yeah! Me also choosing the same thing manually. I have a live cd of 10.10 so I installed that by doing this (choosing manually and making ext4) only and it didn't create any problem but this is not the things for 11.10 beta1 or 2.

Hmmm, what are you saying? You can do the same things from the disk allocation screen in 11.10.

---

