---
title: "swap partition in common between multiple ubuntu"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by tanoloco on 2011-10-25
Hello,

I have two different versions of ubuntu installed on the same machine sharing the swap partition.
I would like to know if this is a good idea or maybe it is better to create a swap partition for each primary ubuntu installation?

That's because I noticed that switching between ubuntu versions causes to get a "check" of disks on boot. I don't know if this is related to the common swap, all I know is that when I had only one ubuntu with its own swap this check appeared only from time to time and not so often.

Thanks for any advice

---

### Post by dino99 on 2011-10-25
working with a common swap partition is how most users do and is perfectly safe. Fsck is starting with a cronjob every 25/30 post, so you should not get one each time you boot. Have you done some tweakings like changing partitions/folders/files rights ?

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

