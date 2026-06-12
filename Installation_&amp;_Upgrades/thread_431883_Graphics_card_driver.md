---
title: "Graphics card driver"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by skymera on 2007-05-03
sorry if this is wrong section.

i have an intel g695 chipset and i need to install the driver in ububtu.
if i need the .INF file, i have it.

how do i install in ubuntu terminal???
thnaks, please help.

---

### Post by dannyboy79 on 2007-05-04
> **skymera said:**
> sorry if this is wrong section.

i have an intel g695 chipset and i need to install the driver in ububtu.
if i need the .INF file, i have it.

how do i install in ubuntu terminal???
thnaks, please help.

no, you can't use a windows driver for a linux xorg graphics driver. What is your problem? Can you boot into ubuntu and your x-server is fine? (meaning you have a gui? (not just a command line prompt)? is it that you want accelerated graphics? you're aren't very specific?

please provide me with more info so I can help. put this into a terminal and let me know what the output is

lspci -v

cat /etc/X11/xorg.conf | grep Driver


and then, if you don't have a gui, can you open this file and see if there is anything that sticks out, like the words Error or similar?

sudo nano /var/log/Xorg.0.log

let me know.

---

