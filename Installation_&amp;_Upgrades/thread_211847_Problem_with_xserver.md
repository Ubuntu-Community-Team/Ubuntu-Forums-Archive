---
title: "Problem with xserver"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by raffytaffy on 2006-07-09
I instaled a custom kernel ..and now id like to install nvidia drivers..i have to install the once from their website..since its a custom kernel..thats fine..i cant seem to get xserver to stop..i try...ctrl +alt f1...then sudo init 3....try to install the drivers...says that im runing xserver???? what gives...how do u stop the xserver in ubuntu :(

---

### Post by woedend on 2006-07-09
sudo /etc/init.d/gdm stop
will do it.

btw tseliot's script works wonders for this.

---

### Post by raffytaffy on 2006-07-09
i thought id share my nvidia install story in here..since its relevant to the topic..i was trying to install nvidia in my new kernel...i did..but i got some xserver errors...so i booted into my old kernel and installed nvidia-glx...then rebooted..and now magically my new kernel works:)) im sitting here scratching my head...but it works

---

