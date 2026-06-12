---
title: "i just reinstalled ubuntu 7.04 and the resolution is a bit off"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by jacob01 on 2007-09-19
i just reinstalled ubuntu in about 20 min and i was surprised how smooth it went. but the only problem i have is that i think my screen resolution is wrong. i am using the res that takes up the whole screen but the menu bars are really small. is there a way to fix this.  before i used i think like 1024x768 but it was at 75 hertz and now my only option is 85hertz is there a way to fix this? like try to force 5 hertz. teh only differance between me old xorg and this current xorg is that the old one used the intel ones and now im using a generic vesa driver

---

### Post by Pumalite on 2007-09-19
Install proprietary drivers:
sudo apt-get install nvidia-glx, or
sudo apt-get install nvidia-glx-new, or
ENVY, or
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Wim Sturkenboom on 2007-09-19
If I understand TS correctly, he has an Intel card.

You can edit /etc/X11/xorg.conf to edit the refresh rates in the monitor section (and change the driver to i810 in the device section to i810 if you want).

---

### Post by Pumalite on 2007-09-19
You are right. Missed that. Sorry.

---

### Post by notwen on 2007-09-19
You may wish to try th new Intel driver, there is a how-to thread located [here]("http://ubuntuforums.org/showthread.php?t=494943").  Works great on my Intel X3100 chipset. =]

---

### Post by jacob01 on 2007-09-19
yea ill like to try them new drivers out i have not been able to play games verry good(you might have seen my postslike i launch css and it locks up my system

---

### Post by jacob01 on 2007-09-19
ok i tried the new driver but i dont have the correct resolution set or refress rate. how would i go about doing that?

from switching from the vesa intel driver to the one you provided i got a bit of a fps improvement in glxgears :)

---

### Post by jacob01 on 2007-09-19
thanks for the help every one i finally figured it out it wouldn't let me use the 1024x768 because the refresh rate limit was to low to allow it to use the resolution i wanted so i changed  
HorizSync	50-96
VertRefresh	60-160 
and it works great.   if you care to see what it looks like click here (i am pretty sure it will work).[ATTACH]43870[/ATTACH]

---

### Post by Pumalite on 2007-09-19
Good for you! You worked it out yourself.

---

### Post by notwen on 2007-09-20
Glad you got everything worked out. =]

---

