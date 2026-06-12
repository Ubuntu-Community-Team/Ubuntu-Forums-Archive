---
title: "Apps not compiling"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by ninocass on 2007-04-19
Im following a guide to enable IPW2200 monitor mode

It involved insttall ieee80211

However im recieving the following errors:

```

Checking in /lib/modules/2.6.20-15-386 for ieee80211 components...
make -C /lib/modules/2.6.20-15-386/build M=/home/nino/wifi/ieee80211-1.2.15 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-386'
  CC [M]  /home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.o
/home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.c: In function ‘prism2_wep_encrypt’:
/home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.c:169: error: invalid use of undefined type ‘struct page’
/home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.c:170: warning: implicit declaration of function ‘offset_in_page’
/home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.c:172: warning: ‘crypto_cipher_encrypt’ is deprecated (declared at include/linux/crypto.h:820)
/home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.c: In function ‘prism2_wep_decrypt’:
/home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.c:212: error: invalid use of undefined type ‘struct page’
/home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.c:215: warning: ‘crypto_cipher_decrypt’ is deprecated (declared at include/linux/crypto.h:846)
make[2]: *** [/home/nino/wifi/ieee80211-1.2.15/ieee80211_crypt_wep.o] Error 1
make[1]: *** [_module_/home/nino/wifi/ieee80211-1.2.15] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-386'
make: *** [modules] Error 2

```

If anyone would shed some light or how i would go about trouble shooting this i would be very greatful

Many thanks

---

### Post by beerorkid on 2007-04-19
well that all looks like gobblity goop to me but I know you will prob have to install build-essential to compile stuff.
```
sudo apt-get install build-essential
```

---

