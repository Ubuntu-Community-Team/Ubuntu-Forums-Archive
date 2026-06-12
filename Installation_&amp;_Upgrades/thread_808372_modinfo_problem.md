---
title: "modinfo problem"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by spd106 on 2008-05-26
I upgraded to 8.04 from the beta.

I have a broadcom wireless card that uses the b43 driver and it works fine. However it doesn't show up in Hardware Drivers (Jockey) and I think that I've traced the problem down to modinfo i.e. when I run modinfo b43 it says this
```
$ modinfo b43
modinfo: could not open b43: No such device

```

However when I specify the full path to the driver it says differently.
```
~$ modinfo /lib/modules/`uname -r`/kernel/drivers/net/wireless/b43/b43.ko
filename:       /lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless/b43/b43.ko
license:        GPL
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     D291278BDAFD171BF373380
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        mac80211,ssb,input-polldev,led-class,rfkill
vermagic:       2.6.24-16-generic SMP mod_unload 586 
```


I've booted a live CD and it works ok, but I don't really want to re-install again.

Thanks

---

