---
title: "how insstall wi-fi driver"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by venio on 2010-06-29
Hello! im new in this forum:) and im am happy to become like member in Ubuntu! I have a truble whit my wirless cart. I have Level one werless card with chip Realtek 8185 ,but mi problem is that i can't install the drivers from the site aircrack-ng for monitoring! there the errors i get:

root@venio-desktop:/home/venio/rtl8180-0.21# tar -xvzf rtl8180-0.21.tar.gz
rtl8180-0.21/
rtl8180-0.21/Makefile
rtl8180-0.21/AUTHORS
rtl8180-0.21/CHANGES
rtl8180-0.21/COPYING
rtl8180-0.21/INSTALL
rtl8180-0.21/LICENSE
rtl8180-0.21/Makefile26
rtl8180-0.21/README
rtl8180-0.21/README.adhoc
rtl8180-0.21/compat24.h
rtl8180-0.21/ieee80211.h
rtl8180-0.21/ieee80211_crypt.c
rtl8180-0.21/ieee80211_crypt.h
rtl8180-0.21/ieee80211_crypt_wep.c
rtl8180-0.21/ieee80211_module.c
rtl8180-0.21/ieee80211_rx.c
rtl8180-0.21/ieee80211_tx.c
rtl8180-0.21/ieee80211_wx.c
rtl8180-0.21/ieee802_11.h
rtl8180-0.21/module_load
rtl8180-0.21/module_load24
rtl8180-0.21/module_unload
rtl8180-0.21/module_unload24
rtl8180-0.21/r8180.h
rtl8180-0.21/r8180_93cx6.c
rtl8180-0.21/r8180_93cx6.h
rtl8180-0.21/r8180_core.c
rtl8180-0.21/r8180_gct.c
rtl8180-0.21/r8180_gct.h
rtl8180-0.21/r8180_hw.h
rtl8180-0.21/r8180_max2820.c
rtl8180-0.21/r8180_max2820.h
rtl8180-0.21/r8180_pm.c
rtl8180-0.21/r8180_pm.h
rtl8180-0.21/r8180_sa2400.c
rtl8180-0.21/r8180_sa2400.h
rtl8180-0.21/r8180_wx.c
rtl8180-0.21/r8180_wx.h
rtl8180-0.21/README.master
root@venio-desktop:/home/venio/rtl8180-0.21# cd rtl8180-0.21
root@venio-desktop:/home/venio/rtl8180-0.21/rtl8180-0.21# patch -Np1 -i ../rtl8180-0.21v2.patch
The program 'patch' is currently not installed.  You can install it by typing:
apt-get install patch
bash: patch: command not found
And i can't understand what it mean -  The program 'patch' is currently not installed.  You can install it by  typing:
apt-get install patch??? and here i give up! and if somebody can help me how to continue to install the drivers. Thank'you in advance and sorry for my bad English!

---

### Post by kalistona on 2010-06-29
a patch is a zip (something like that) where all is download in one time so you click twice and it is installed it means maybe you have downloaded one or two drivers and the machine says 'download the patch !)
it can be also another soft because it is working maybe only with another softs/os (backtrack i suppose)
have you download .deb ? bz2 ? is it a problem from the site ?, maybe, try in few hours. 
have you read[COLOR=Blue] README[/COLOR], and anther texte it is important you know ...?

ps : your bad english is not worst than mine ! do not worry for that !

---

