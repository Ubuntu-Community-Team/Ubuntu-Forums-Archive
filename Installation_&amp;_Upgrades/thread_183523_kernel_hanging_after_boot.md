---
title: "kernel hanging after boot"
date: 2006-05-28
forum: Installation &amp; Upgrades
---

### Post by blackweaver on 2006-05-28
i just got ubuntu (breezy badger) and installed it on one of my harddrive partitions; however when i tried to boot it kept hanging, giving an unable to access partition ... error so i decided to try using another linux kernel that i have (2.4.29) that i know works and i was able to boot my os; however this also means that i cannot access any of my drivers since they are built around the 2.6.whatver kernel that comes with the ubuntu; i decided to check the kernel config.log (or whatever it is called - u know the part that shows the kernel config) and found out that support for my motherboard - via686 i think - is as a module; in short i have to get another kernel. Now my question is: is there somewhere i can get the exact kernel with support for my motherboard or if the source code is available on the cd and if it is which folder is it located? i have poor internet connection and i would really love not to have to download the source code from the web

---

### Post by R3linquish3r on 2006-05-28
If your feeling adventerous I would recommend building a kernel from source. It takes a good amount of time (roughly and hour or two) but you get exactly what you want out of your system. The current kernel should support your motherboard so just make the attempt at that one if you want. Do a search for "2.6.16 kernel" and you'll find the how-to easily.

---

