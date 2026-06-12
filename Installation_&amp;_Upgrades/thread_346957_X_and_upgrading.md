---
title: "X and upgrading"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by yusufm on 2007-01-26
I started having this issue a while ago during some upgrade from dapper to edy, where X server does not start up. It says that theres some problem and just goes back to command line.

I followed the instruction on the ubuntu notes about the X problem and reinstalled xserver-xorg, and tried to reconfigure as well, using dpkg-reconfigure... But now it says that X cannot start up because no devices detected. I am using a laptop. I am not sure what else to do. Is there a way I can reset everything and have it automatically work like when I first installed ubuntu, without having to actually wipe the system?

Thanks.

---

### Post by PriceChild on 2007-01-26
```
sudo dpkg-reconfigure xserver-xorg -phigh
```*Should* reset your xserver to defaults.

Then just
```
sudo /etc/init.d/gdm restart
```

---

### Post by yusufm on 2007-01-27
no joy. It still says: 

no devices found.

fatal error:
 no screens found.

---

