---
title: "BlueZ 5.12 Installation"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by sprite728 on 2013-12-12
I want to install the latest stable Bluez (5.12) on my Ubuntu machine. I manually build Bluez 5.12 from [http://www.bluez.org/](http://www.bluez.org/), the installation seems to be success but I don't know how to replace the older 4.1 bluez with the new version. I check `dpkg --status bluez` and the version is still 4.1.

---

### Post by tonysonney on 2014-02-18
Hi,
   Word of warning first :). It does not seem to be that easy to get blueZ removed and run it manually. BlueZ version 5.12 also needs a kernel higher than 3.4. If you still want to go ahead, here is what I did (I couldnt get it working completely yet).

I am assuming you have run the configuration file and then did 
make and 
make install

In the configuration file what was the PREFIX set?

To remove the existing BlueZ, I used synaptic packet manager and removed blueZ. (This is a bit more complicated if you are running Gnome classic).

Cheers,

---

