---
title: "dapper: where is hotplug directory?"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by roots on 2006-05-31
hi, 

i just installed dapper and now i'm trying to get my ipw2200 wlan working with wpa. i d/led all ipw2200 and ieee80211 drivers plus ipw firmware.

install went fine so far except one weird thing:
i can't find any hotplug/firmware directory!?!?! 

it used to be ```
/usr/lib/hotplug/firmware
``` to copy the ipw2200 firmware files to, but there's not even a ```
/usr/lib/hotplug
```  ?!

should i call an emergency psychiatrist? or can someone tell me what this means?


cheers,
roots

---

### Post by tkjacobsen on 2006-05-31
maybe you can use /etc/hotplug

---

### Post by roots on 2006-06-01
nope, as i've learnt, the hotplugging concept of ubuntu has completely changed with dapper, for more info just check the forums.

however, the firmware directory i was looking for is

/lib/firmware

any manually added firmware has to be copied directly into THIS directory, NOT into the kernel-version subdirectory. the latter seems to be reserved for firmware managed natively by the system.


cheers,
roots

---

