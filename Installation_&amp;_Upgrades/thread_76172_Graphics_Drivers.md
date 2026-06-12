---
title: "Graphics Drivers"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by cherryos on 2005-10-14
hello, i'm a new linux user, and I had no problems with the installation until i booted into my linux partition. i got a bunch of error messages, and I think the main one is (EE) No devices detected. I tried doing X -configure, but it just loaded the black and white screen with the x pointer and i had to manually restart. Does anyone know how I can get it to detect my drivers?

---

### Post by egorgry on 2005-10-14
no space between x and configure you are just executing X.

---

### Post by egorgry on 2005-10-14
LOL! wait a minute I'm not sure there is an x-configure:confused: 

what you want is to get the refreash rate of your monitor and put them in teh xorg.conf file or run sudo dpkg-reconfigure xserver-xorg.

you tricked me ;)

---

