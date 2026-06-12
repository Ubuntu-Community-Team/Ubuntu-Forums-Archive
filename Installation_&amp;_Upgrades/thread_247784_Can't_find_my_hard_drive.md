---
title: "Can't find my hard drive"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by fk4n on 2006-08-31
I'm new in ubuntu linux. I was using windows before. I had three partitions.  One of them is 18G unformat partition. I tried format it in windows but it didnt work. So I decided install ubuntu linux and eras everything else. When i install linux. It didnt find the 18G hard drive. Now i have one big 41G hard drive. But i lost the 18G. Is there a way to find the lost space and merge it in. Many thanks :confused:

---

### Post by zxee on 2006-08-31
Provided you don't need to save anything on the drive you could use cfdisk from a terminal. Check out man cfdisk.
Do > sudo cfdisk /dev/hda from the terminal to open that disk/partiton tool. You can delete all partitions you have and start over again. Hope that helps.

---

