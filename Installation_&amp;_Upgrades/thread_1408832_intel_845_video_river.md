---
title: "intel 845 video river"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by ozzfest96 on 2010-02-16
i installed Ubuntu 9.10 on my ibm netvista with intel integrated 845 graphics and the only 2 resolutions its offers 800x600 and 640x400. I think i need to install a driver but i cant find it and even if i did i dont know how on Ubuntu can someone please help me

---

### Post by efflandt on 2010-02-16
I don't think you need a driver.  It is just that with a VGA connection, X cannot always determine optimum or native resolution.  See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Note that your video outputs could have different names than shown there, but **xrandr** should tell you what they are called (and which resolutions are active).

Look through /var/log/Xorg.0.log to see what resolutions X finds.  Sometimes it thinks it cannot use certain resolutions, even if they would work.  Sometimes **cvt** does not come up with optimum timings, but once you get something close, and set it with **xrandr**, you could try fine tuning with **xvidtune**.

What is the native resolution of your monitor?

---

### Post by ozzfest96 on 2010-02-17
i think 1024x768 but im not sure its an older microtouch monitor given to me for free but it didnt come with any papers or labels.

---

