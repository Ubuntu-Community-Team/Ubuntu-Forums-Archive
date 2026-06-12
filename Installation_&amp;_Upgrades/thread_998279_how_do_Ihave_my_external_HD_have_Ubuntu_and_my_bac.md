---
title: "how do Ihave my external HD have Ubuntu and my backup files?"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by glenboarder99 on 2008-11-30
HI,
I know everybody probly asks this question but how do I have my external HD have Ubuntu and my backup files that i do not want to lose??
 I have a 500 gb maxtor external hd.
Any help would be Great!
Glenboarder99

---

### Post by Pumalite on 2008-11-30
Use Gparted to partition your drive. Leave Ubuntu at the beginning of the drive.

---

### Post by glenboarder99 on 2008-12-07
Thank you.
I was a long process but I did it. I know I sound like a newb, but do you think you could give good detaialed insructions on how to install 8.10 on that partition only? I already have a live CD.

---

### Post by Pumalite on 2008-12-07
At installation; go 'Manual' and pick the partition. 
10 GB for '/'
The rest minus your RAM for /home
Your amount of RAM (or 1.4 RAM) for /swap

---

### Post by glenboarder99 on 2008-12-07
what? I am at the installation on manual and I cant tell which one is my external or even y partition? Im sorry please help!

---

### Post by Pumalite on 2008-12-07
If you have one drive; your external must be sdb; and so on. I imagine you save your space for Ubuntu in the second or third partition.
You can also find out with:
sudo fdisk -lu

---

