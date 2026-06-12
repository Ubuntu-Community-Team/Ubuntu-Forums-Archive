---
title: "Can't get higer than 640X480"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by bjk03 on 2007-07-20
I got 7.04 installed on our Gateway E-9425 server, but I can't get any higher screen resolution than 640X480. The video card is an integrated Matrox G200 with 2.25 MB memory. The monitor is an Acer AL1716. I tried to use ```
sudo dpkg-reconfigure xserver-xorg
``` and killed X. :( So now I have no GUI.

I booted off the 7.04 LiveCD and I still only have 640X480 as my only resoultion option.

---

### Post by reckless2k2 on 2007-07-20
do you know your video card manufacturer by chance?

when i 1st started with linux, all i did was blow up X all the time. haha...very discouraging. hahaha.

---

### Post by bjk03 on 2007-07-20
All I know is its an **integrated Matrox G200**. I think its an Intel Motherboard.

---

### Post by try2lickurelbo on 2007-07-20
I had this problem on a laptop of mine.  There is a workaround, try adding

HorizSync       36-52
VertRefresh     36-60

to your /etc/X11/xorg.conf file, worth a try ;)

remember to comment out the default refresh rates.  It is in the Moniter section if i can remember correctly.

---

### Post by bjk03 on 2007-07-20
I found a way that works for me. I had Ubuntu installed on another machine and used it to login remotely and it allows me to have higher resolutions.

---

