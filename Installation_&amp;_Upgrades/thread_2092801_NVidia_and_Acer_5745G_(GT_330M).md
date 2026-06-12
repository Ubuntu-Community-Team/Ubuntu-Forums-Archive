---
title: "NVidia and Acer 5745G (GT 330M)"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by jeepman32 on 2012-12-08
I am going to put as much information as I can here.
I tried to install the NVidia drivers to my machine, using the .run file NVidia provides. That installed, but it never switched to NVidia from Nouveau, instead it put my machine's monitor into 600*480, and I managed to attach the external monitor. So with that fail in mind, I went back to reinstall, and I installed the drivers from the additional drivers list, that worked flawlessly. I restarted lightdm, as instructed, and again, the same result. From this I have deduced that it is either the drivers not liking my machine or I am doing something wrong. (I also tried rebooting to no avail).
Thanks in advance,
jeepman32

---

### Post by tenmoi on 2012-12-09
Your laptop boasts NVIDIA's optimus technology:redface:, which requires at the moment that you install bumblebee. 

Google bumblebee ppa to learn how to install it.

---

### Post by jeepman32 on 2012-12-09
Thanks!

---

