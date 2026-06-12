---
title: "BCM wireless driver problem"
date: 2012-02-11
forum: Installation &amp; Upgrades
---

### Post by gidak on 2012-02-11
Hi all,

I just upgraded from kernel 3.0 to 3.1.
After upgrade my wireless driver stopped working (no surprise their )
but when i go to the "additional drivers" and try to install my "Broadcom 802.11 Linux STA" wireless driver
it gives mt the message:
```
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log
```I have no idea what is the problem... 
never had it before,

here are the last few lines of the jockey.log file:

```


2012-02-12 02:16:39,240 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-02-12 02:16:42,526 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2012-02-12 02:16:42,526 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2012-02-12 02:16:42,602 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted

```please help, I'm stuck with a Ethernet cable like I'm still in <2000 ;)
Tn'x

---

### Post by gidak on 2012-02-11
Never mined,
I decided to just downgrade my kernel to 3.0 from 3.1...

---

