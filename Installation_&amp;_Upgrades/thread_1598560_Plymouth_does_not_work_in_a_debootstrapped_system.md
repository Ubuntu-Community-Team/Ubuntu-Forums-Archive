---
title: "Plymouth does not work in a debootstrapped system"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by GeoMX on 2010-10-16
I've created a custom Lucid installation using debootstrap, it works nice but have some problems, one of them is plymouth: it does not show the splash screen, when booting, I can only see a black screen, suddenly a green one and again black, when it is about to boot, some text messages appear and then the system starts.
I'm only using X, no window manager, so I edited /etc/init/plymouth.conf and changed the start instruction from:
```
start on (starting mountall
          or (runlevel [016]
              and (stopped gdm
                   or stopped kdm
                   or stopped xdm
                   or stopped lxdm)))
```
to:
```
start on (runlevel [016])
```
But it remains the same, Plymouth does not show the splash screen.

Any advice is welcome, thanks.

---

### Post by GeoMX on 2010-10-17
I found the problem: a Plymouth theme was not automatically configured just by installing the plymouth package :p, I had to add it manually. After doing so, the modification to plymouth.conf worked fine.

---

### Post by dino99 on 2010-10-17
then change your thread to [SOLVED] por favor

---

### Post by GeoMX on 2010-10-19
It was already marked as solved before your post...

---

