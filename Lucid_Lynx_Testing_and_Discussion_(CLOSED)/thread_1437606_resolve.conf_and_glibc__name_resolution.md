---
title: "resolve.conf and glibc / name resolution"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wnelson on 2010-03-24
The latest .17 upgrade caused name resolution not to work, empty resolv.conf file. 
I found that /etc/resolvconf/resolv.conf.d/original contained my name server information. For a temporary fix I copied that file, original to /etc/resolv.conf. 
This provided a fix for name resolution in apps; ie. firefox, chrome, etc.

Walt

---

### Post by garvinrick4 on 2010-03-24
> **wnelson said:**
> The latest .17 upgrade caused name resolution not to work, empty resolv.conf file. 
I found that /etc/resolvconf/resolv.conf.d/original contained my name server information. For a temporary fix I copied that file, original to /etc/resolv.conf. 
This provided a fix for name resolution in apps; ie. firefox, chrome, etc.

Walt Are you using wifi connection? Mine is always empty until I have a connection. And if I am using the chroot command from another partition of Ubuntu
or a Live Cd I must. sudo cp /etc/resolv.conf /media/lucid/etc/resov.conf
to copy the domain into (this partition labeled lucid above) partition I which to
use a internet connection.

---

### Post by wnelson on 2010-03-24
Just a standard e100 10/100 ethernet connection.

---

### Post by wnelson on 2010-03-24
Just a standard e100 10/100 ethernet connection.

Only started after the recent dist-upgrade.

---

