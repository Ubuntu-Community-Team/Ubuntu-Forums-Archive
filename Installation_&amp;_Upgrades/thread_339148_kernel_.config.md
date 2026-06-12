---
title: "kernel .config"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by offbyte on 2007-01-15
hi, i'm not sure this is the right place... but here it goes

How can I k now wheres my corent .config from the kernel i'm using right now?


i've been using ubuntu for some time and all my hardware worked fine ... but now i'm trying  to compile my own kernel from scratch, if I could know my current .config it could be a good orientation =) for me and for any newbie

---

### Post by DoctorMO on 2007-01-15
Use 'make oldconfig'

This will create a configuration based on your current kernel but will only ask your questions which are new in the release you have.

Hope this helps.

---

### Post by hal10000 on 2007-01-15
copy the kernel configuration file from your current running kernel from /boot/config-2.6.17-10-generic (assumed you current kernel is 2.6.10-generic) to /usr/src/linux/.config then [COLOR="Red"]make oldconfig[/COLOR] or make xconfig (in case you want to change settings).

---

### Post by offbyte on 2007-01-16
thanks for the quick answer now i have a litle "compass" to "guide" myself in the asdventure of compiling my own kernel.

---

