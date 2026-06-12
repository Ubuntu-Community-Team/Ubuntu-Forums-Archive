---
title: "[SOLVED] How to load md into kernel?"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by whoismoses on 2008-06-10
Ok, like most people here I am new to Ubuntu (well linux in general).  So far I have done pretty well for myself so far.  

My problem is I have setup a raid mirror on my system using mdadm.  That was pretty easy.  However apparently md is not automatically loaded into the kernel so when I reboot I have to do a 

```
modprobe md
```

then I can mount my disk.

Does anyone know how to do this?  I have done some searching there and on google and can't find much help, I don't know if I am searching for the wrong thing or if its just that difficult.

---

### Post by whoismoses on 2008-06-13
Ok, not sure if I posted this in the wrong forums or not, but looks like I didn't get any responses... Strange.

Anyways I figured it out enough to get it working.

In the mdadm script in my /etc/init.d I added the line...

```
modprobe md
```

right after the variable declarations.  I then created a link to this in the /etc/rcS.d folder with a level of 10...

Rebooted and it worked.

---

