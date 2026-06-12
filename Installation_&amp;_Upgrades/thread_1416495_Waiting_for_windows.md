---
title: "Waiting for /windows"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by illbashu on 2010-02-26
I upgraded to Ubuntu 10.04 from 9.10 and when I try to boot into ubuntu now it goes to a screen where it says "waiting for /windows" and even after the loading bar is fully loaded it stuck on that screen. 

BTW I don't know if this will help but when I restarted it wouldn't work because grub was broken and I booted it 9.10 live CD and reinstalled it.

---

### Post by illbashu on 2010-02-26
[http://img222.imageshack.us/img222/5006/dsc00288c.jpg](http://img222.imageshack.us/img222/5006/dsc00288c.jpg)

After spaming ctlr-alt-f2 a bunch of times along with other keys I eventually got a shell.
[http://img144.imageshack.us/img144/4070/dsc00291j.jpg](http://img144.imageshack.us/img144/4070/dsc00291j.jpg)

---

### Post by illbashu on 2010-02-26
I fixed it. I had to boot into a live CD and comment out /windows in fstab.

---

