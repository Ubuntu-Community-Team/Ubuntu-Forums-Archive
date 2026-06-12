---
title: "Problem Installing Netgear AC600 Dualband Wireless Adapter"
date: 2017-04-18
forum: MINT
---

### Post by brit27 on 2017-04-18
I bought a Wireless adapter from Walmart last night and am having trouble getting it to work.
Im currently running Mint 17.3 Cinnamon 32-bit [Cinnamon Version 2.8.6]


I've tried direction from here : [http://www.humans-enabled.com/2016/03/how-to-ubuntu-1604-gnu-linux-netgear.html](http://www.humans-enabled.com/2016/03/how-to-ubuntu-1604-gnu-linux-netgear.html)

But came up with this message:

```
~/wireless_driver/rtl8812au_rtl8821au $ make
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/3.19.0-32-generic/build M=/home/xol/wireless_driver/rtl8812au_rtl8821au  modules
make[1]: Entering directory `/usr/src/linux-headers-3.19.0-32-generic'
  CC [M]  /home/xol/wireless_driver/rtl8812au_rtl8821au/core/rtw_cmd.o
cc1: error: -Werror=incompatible-pointer-types: no option -Wincompatible-pointer-types
cc1: error: -Werror=date-time: no option -Wdate-time
make[2]: *** [/home/xol/wireless_driver/rtl8812au_rtl8821au/core/rtw_cmd.o] Error 1
make[1]: *** [_module_/home/xol/wireless_driver/rtl8812au_rtl8821au] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.19.0-32-generic'
make: *** [modules] Error 2
```

Which ended me at Step 5.

Anyone suggestions to get this thing going?
I'm not very familiar (at all...) with coding or Terminal lingo for linux in general.

I originally tried installing the disk with wine, it was working for a while then it stopped with an error.

---

### Post by howefield on 2017-04-18
Thread moved to the "*MINT*" forum.

---

