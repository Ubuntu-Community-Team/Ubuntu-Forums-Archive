---
title: "After upgrade to 13.10 desktop doesn't come up but system boots fine"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by deltas2 on 2013-10-27
I installed on the same laptop (Aspire 5100) Kubuntu x86_64 and Xubuntu i686, complete Desktops and LAMP, since some time ago (you probably guessed why). I've been keeping up with the updates/upgrades and recently I got them both on 13.10. Xubuntu (i686) works great without any hick-ups. 
Kubuntu (64b) does not display the Desktop, freezes the keyboard and mouse but everything else works fine (logging in from another laptop). After probing, I concluded that the ATI Radeon does not get started properly (initialization stops just before the KMSsettings) and the xserver quits.
I've checked the installation and on-line for solutions but no luck. I attach the Xorg.log files from both systems which appear identical except that one does not complete the device configuration: Xorg0Klog.txt (Kubuntu) and Xorg0X1log.txt and Xorg0X2log.txt (for Xubuntu, had to split it to get over the upload limit). 
Any suggestions, welcome.

After some more probing, turns out that the wrong libraries for libdrm were left behind. After re+re, everything worked. The clue was given in kdm.log as:
/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers/radeon_drv.so: undefined symbol: drmGetCap

---

