---
title: "Headphones not working"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by chetkgp on 2010-11-07
Hi All, 

I recently installed Ubuntu 10.10 on my Lenovo-G460 laptop.
The audio works fine when the laptop's speakers are used,
but headphones don't work.

No sound comes from the headphones, and even the laptop's
speakers continue to function when the headphone's jack 
is inserted.

I've checked on the Windows-7 installation on the machine
and everything is fine there.

Is there something that needs to be enabled in Ubuntu to
get the headphones to function.

Chet

---

### Post by finlost on 2010-11-07
Type alsamixer at a terminal prompt.  Check the headphone volume.

---

### Post by chetkgp on 2010-11-07
alsamixer does not show headphones
I've checked all the tabs

The details of my device are :
Card : HDA Intel
Chip :  Intel IbexPeak HDMI

---

### Post by dotsha on 2010-12-24
I found that appending to /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=thinkpad

... worked for me on Ubuntu 10.10 on G460.

I got the answer from "fabrizzio" at [http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-G460-Linux-driver/m-p/307728](http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-G460-Linux-driver/m-p/307728)

---

