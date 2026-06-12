---
title: "HP6735s Ubuntu Karmic (9.10) and non working wireless"
date: 2009-08-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kerubu on 2009-08-21
Hello,

I recently bought an HP 6735s as it was listed on the UbuntuLaptopTesting pages as working ok under 8.10. This indeed was true, wireless worked ok and sound did too with a minor tweak as described on the above wiki. However, there is a problem with the video driver/X server under 8.10 when closing and opening the lid; it results in considerable and unacceptable screen flicker. Instead of trying to fiddle with configs etc I thought I'd try the pre release of 9.10.

This did solve my screen flicker problems but now the wireless doesn't work !

I believe the wireless is a broadcom 4311 and the only modules loaded were b43 and ssb, not wl. I downloaded the broadcom driver source from here :
[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

and followed the readme instructions but the build fails :

1) It appears that the build is sensitive to where I un-tar the file. if I put it in ~/HP\ 6735s/Wireless/ compiling fails :
> make: Entering directory `/usr/src/linux-headers-2.6.31-5-generic'
make: *** No rule to make target `6735s/Wireless/w32'. Stop.
make: Leaving directory `/usr/src/linux-headers-2.6.31-5-generic'


Moving it higher up toward my home directory does result in the build beginning but a load of errors :

> make -C /lib/modules/2.6.31-5-generic/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.31-5-generic'
  LD      /home/kerubu/wl/w32/built-in.o
  CC [M]  /home/kerubu/wl/w32/src/wl/sys/wl_linux.o
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:57:27: error: net/ieee80211.h: No such file or directory
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_if_setup’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:220: error: ‘struct net_device’ has no member named ‘open’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:221: error: ‘struct net_device’ has no member named ‘stop’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:222: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:223: error: ‘struct net_device’ has no member named ‘get_stats’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:224: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:225: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:226: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_attach’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:362: error: implicit declaration of function ‘ieee80211_get_crypto_ops’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:362: warning: assignment makes pointer from integer without a cast
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:365: warning: assignment makes pointer from integer without a cast
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_free’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:634: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:669: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:685: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:689: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_open’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:714: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_close’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:742: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_start’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:765: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_alloc_if’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:850: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_get_driver_info’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1030: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_ioctl’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1118: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1119: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_get_stats’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1204: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_get_wireless_stats’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1236: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1237: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_set_mac_address’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1304: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1312: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘_wl_set_multicast_list’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1335: error: ‘struct net_device’ has no member named ‘priv’
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_tkip_miccheck’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1726: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1729: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_tkip_micadd’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1748: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_tkip_encrypt’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1768: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_tkip_decrypt’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1790: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1792: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_tkip_keyset’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1834: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1844: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1851: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1861: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1871: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1878: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c: In function ‘wl_tkip_printstats’:
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1897: error: dereferencing pointer to incomplete type
/home/kerubu/wl/w32/src/wl/sys/wl_linux.c:1899: error: dereferencing pointer to incomplete type
make[1]: *** [/home/kerubu/wl/w32/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/kerubu/wl/w32] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-5-generic'


Am I doing something wrong while trying to build these drivers or is it failing because I am using to new a kernel ? 2.6.31-5

---

### Post by lwhitmore on 2009-10-23
Hi - did you manage to sort this problem out?  I've got the same issue.
[B]
** I sorted out the problem by following the advice in [this thread]("http://ubuntuforums.org/showthread.php?t=1285828") (needed to apply a patch to the driver I was compiling, due to 2.6.31 kernel not supporting &#8216;struct net_device' **[/B]

---

