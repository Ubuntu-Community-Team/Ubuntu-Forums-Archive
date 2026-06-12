---
title: "Startup disk creator problem"
date: 2011-11-01
forum: Installation &amp; Upgrades
---

### Post by hsweet on 2011-11-01
I've tried 2x with 2 images.  MD5check is ok, and a burned Cd works.

On trying to boot from USB I get following errors.

```
"Unknown keyword in configuration file: gfxboot"
```and
```
vesamenu.c32 not a com32R image
```

gfxboot text below..
```
label normal=Normal
append normal=
label driverupdates=Use driver update disc
append driverupdates=debian-installer/driver-update=true
applies driverupdates=live live-install
label oem=OEM install (for manufacturers)
append oem=oem-config/enable=true
applies oem=live live-install install
```

Anybody know what is going on or having this problem?

thanks

---

### Post by raja.genupula on 2011-11-01
Hi man its a BUG actually .But have you tried by creating another new USB.

---

### Post by hsweet on 2011-11-04
Thanks.  It looked like a bug.

Same thing happened twice so far, with 2 different images.

---

### Post by raja.genupula on 2011-11-04
> **hsweet said:**
> Thanks.  It looked like a bug.

Same thing happened twice so far, with 2 different images.


If you have Cd-ROM then you can try from there. actually what you wanna do , i mean upgrade or new install ?

---

### Post by hsweet on 2011-11-04
Cd works ok.  Turns out it also worked with a different flash drive.  thanks, case closed:P

---

