---
title: "Failed to boot Live USB - scrambled screen."
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by Dexior on 2012-05-07
Hello!
I have problem with booting 12.04 Live USB on my PC:
Asus P5QL Pro
E5200
2GB DDR2
VTX Radeon 6790.
After choosing option to boot from USB I'm getting scrambled screen like this: [http://imgur.com/huYMD](http://imgur.com/huYMD) with various patterns, colours and text in the right corner. After few seconds screen turns black and monitor goes into power saving mode. There are no signs of booting into Ubuntu like login screen "chimes" and also I can't get into Terminal by Ctrl + Alt + F-keys. Tried with 2 different pendrives and creators (Universal Usb Installer, Untebootin) but with the same result. MD5 is fine.
Anyone can help me?

---

### Post by jadtech on 2012-05-07
make sure you have the right ISO for 32bit or 64 bit for that computer and you might need the alternate version of the ISO ..

---

### Post by Dexior on 2012-05-07
32 bit Alternative - don't even start booting, just "beep" from PC speaker and goes back to boot menu. Only recovery mode is working but can't install because it wants to read files from cd
64 bit desktop - same result as 32 bit desktop (not surprising)

---

### Post by Dexior on 2012-05-08
It looks like Ubuntu don't like my v-card. I burned a LiveCD and it boots to purple-keyboard-man screen, after a while it get scrambled like the one on pendrive. However, I turned nomodeset and it booted just fine (with 1 second of scrambled screen after Ubuntu loading screen). Is there any way to turn nomodeset on Live USB? After that I think I'll be able to download working drivers.

---

### Post by efflandt on 2012-05-08
Do you have access to an Ubuntu system to create the bootable iso on USB?  Or maybe you could do that using the live CD.  Then it should boot from USB just like from the CD and you should be able to set **nomodeset** the same way.

Apparently many people have problems with kernel mode setting in Ubuntu 11 and 12 versions.  I never had to use nomodeset for 10.10, but if I do not use it for 11.10 for an installed system with nvidia driver, my screen (HDTV) just says "no signal".  I forget if I had to do that for the iso on USB.  I am just downloading 64-bit 12.04 now.

---

### Post by wilee-nilee on 2012-05-08
+1 on the nomodeset.

Here is a link for using that option from a live cd or from a edit at the grub menu. These two methods are for a per-session use.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Dexior on 2012-05-09
Ye, I got to his by myself yesterday and than installed radeon drivers by terminal. The problem is I haven't got that purpleish grub menu but a bit different Universal USB Installer from which I couldn't set nomodeset. By hitting help, than going back to menu I managed to get into grub.

---

