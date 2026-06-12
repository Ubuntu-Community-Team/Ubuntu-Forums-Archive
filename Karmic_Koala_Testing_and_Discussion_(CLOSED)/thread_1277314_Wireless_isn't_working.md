---
title: "Wireless isn't working"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wedderburn on 2009-09-28
ok so wireless isn't working at startup so i do a 

```
sudo modprob iwl3945
```

and get a > FATAL: Error inserting iwl3945 (/lib/modules/2.6.31-11-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)

the device is called "PRO/Wireless 3945ABG [Golan] Network Connection "
with a product id of 16930 (0x4222)

also in the system logs theres this > [   23.199942] iwl3945: Unknown parameter `hwcrypto'

basically the drivers not getting loaded on start up and no wireless

anyone else having issues or anyone have a fix? thanks :)

oh and my kernel version is
2.6.31-11-generic (#36-Ubuntu SMP Fri Sep 25 06:37:51 UTC 2009)

---

### Post by MacUntu on 2009-09-28
Does```
grep "hwcrypto" /etc/modprobe.d/*
```return a file? If so, open that file and remove the hwcrypto part of it.

---

### Post by wedderburn on 2009-09-28
> **MacUntu said:**
> Does```
grep "hwcrypto" /etc/modprobe.d/*
```return a file? If so, open that file and remove the hwcrypto part of it.

thanks, the file was from 2007, so it had been lurking there through a fair few releases

---

