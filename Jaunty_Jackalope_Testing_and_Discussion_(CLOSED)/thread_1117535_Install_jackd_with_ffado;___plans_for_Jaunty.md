---
title: "Install jackd with ffado;   plans for Jaunty"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sumpm1 on 2009-04-06
Hey guys. I have tried Jaunty briefly and am impressed with some new features, including support for the ext4 partition format. I plan to do a clean install when Jaunty comes out on my own system, and need support for ffado and jackd for my Firepod firewire audio interface.

My question: What will I have to do in order to get ffado installed with jackd in Jaunty? 

I know it is tricky to install on 8.10, my current setup...

Thanks

---

### Post by k-o-x on 2009-04-07
I just tried installing jackd on Jaunty beta. libffado installs automatically with it, and you can install additional packages manually if needed (ffado-tools, ffado-mixer, ffado-dbus-server).

Don't forget you'll also have to get a -rt kernel, set udev options to give you permissions on /dev/raw1394 and edit /etc/security/limits.conf to be able to run jackd with RT scheduling. Google has plenty of results about these topics, but I guess you already passed these steps with your current installation :)

---

