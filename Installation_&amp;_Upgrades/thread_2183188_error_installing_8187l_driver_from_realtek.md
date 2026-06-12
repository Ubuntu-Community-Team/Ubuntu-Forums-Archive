---
title: "error installing 8187l driver from realtek"
date: 2013-10-23
forum: Installation &amp; Upgrades
---

### Post by weblink2 on 2013-10-23
[B]hello

i download the right driver from realtek website but
when i try to install it i get this error[/B] **:**

reda36@reda36-virtual-machine:~$ [COLOR=#ff0000]ls[/COLOR]
Desktop    Music     rtl8187L_linux_26.1040.0820.2010.release.tar.gz
Documents  Pictures  Templates
Downloads  Public    Videos
reda36@reda36-virtual-machine:~$ [COLOR=#ff0000]tar zxvf rtl8187L_linux_26.1040.0820.2010.release.tar.gz[/COLOR]
rtl8187L_linux_26.1040.0820.2010.release/
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/scatterwalk.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/rtl_crypto.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/cipher.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/compress.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_wx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/kmap_types.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/Makefile
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/digest.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_tkip.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_wep.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_softmac.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/scatterwalk.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/license
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_module.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/tags
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/readme
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_softmac_wx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/api.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_crypt_ccmp.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/michael_mic.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/internal.h
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/proc.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/aes.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/arc4.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_tx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/ieee80211_rx.c
rtl8187L_linux_26.1040.0820.2010.release/ieee80211/autoload.c
rtl8187L_linux_26.1040.0820.2010.release/Makefile
rtl8187L_linux_26.1040.0820.2010.release/wlan0down
rtl8187L_linux_26.1040.0820.2010.release/RadioPower.sh
rtl8187L_linux_26.1040.0820.2010.release/ReadMe
rtl8187L_linux_26.1040.0820.2010.release/wlan0up
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/changes
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/install
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/Makefile
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_dm.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/license
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_hw.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_core.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/readme
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_wx.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/copying
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225z2.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/authors
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8187_led.c
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_pm.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_93cx6.h
rtl8187L_linux_26.1040.0820.2010.release/rtl8187/r8180_rtl8225.h
rtl8187L_linux_26.1040.0820.2010.release/release_note
rtl8187L_linux_26.1040.0820.2010.release/wlan0dhcp
rtl8187L_linux_26.1040.0820.2010.release/wpa1.conf
rtl8187L_linux_26.1040.0820.2010.release/wpa_supplicant-0.5.5.zip
rtl8187L_linux_26.1040.0820.2010.release/ifcfg-wlan0
reda36@reda36-virtual-machine:~$ cd rtl8187L_linux_26.1040.0820.2010.release
[COLOR=#000000]reda36@reda36-virtual-machine:~/rtl8187L_linux_26.1040.0820.2010.release$[/COLOR][COLOR=#ff0000]make[/COLOR][COLOR=#0000ff]
make: *** /lib/modules/3.8.0-32-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2[/COLOR]

---

### Post by weblink2 on 2013-10-24
**any one who could help ?**

---

