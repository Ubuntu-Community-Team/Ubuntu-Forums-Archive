---
title: "SOLVED: Ricoh SD Card R5C822"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by kishorebudha on 2007-12-19
For some reason the SD Card reader would not run properly (problems remounting if unmounted). Also, the cool SD Card Icon on the desktop had disappeared. The following worked for me:

in /etc/fstab add the following (for newbies like me: sudo gedit /etc/fstab)

```
/dev/mmcblk0p1  /media/mmcblk0p1   auto    defaults,sync,iocharset=utf8,user,noauto  0       0
```

Also add to /etc/modules (sudo gedit /etc/modules)

 ```
tifm_sd 
```

---

### Post by josin on 2007-12-29
Would you be kind enough to post the result from
```
lspci | grep Ricoh
```,please?
Thanks

---

### Post by kishorebudha on 2007-12-29
```
$ lspci | grep Ricoh
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)

```

---

### Post by DFalconX on 2008-04-22
and how Can I mount a MS or a MMS?? please I need Know how!!

---

