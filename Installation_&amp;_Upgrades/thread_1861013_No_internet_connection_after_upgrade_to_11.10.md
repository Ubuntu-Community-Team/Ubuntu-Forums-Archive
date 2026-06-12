---
title: "No internet connection after upgrade to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by ithildraug on 2011-10-15
Hi guys,

it's my first message in the forum, I hope you'll be able to help. I've just upgraded to 11.10, during the installation I had two error messages about the packages firmware-b43-lpphy-installer and flashplugin-downloader. After reboot everything seems to be working, only it's unable to connect to my Huawei E220 (Vodafone) modem. What shall I do?


thanks, and sorry if it's been already asked. :-S

---

### Post by TouchuvGrey on 2011-10-15
Almost exactly the same situation here,
Two error messages during install and 
now wireless not working. Possible
wireless driver issue ?

---

### Post by dFlyer on 2011-10-15
If you can find a wired network connection you maybe able to find the correct drivers using additional drivers.

---

### Post by TouchuvGrey on 2011-10-15
"additional drivers" shows me that i already
have 

The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA 
supportand snd-intel8x0m module) which is sufficient for 
basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can 
build using the source fromthe sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.

   i'm guessing that there is a kernal driver
missiing or corrupted.

---

### Post by TouchuvGrey on 2011-10-21
Hooked up a wired connection, downloaded
latest updates, wireless working again.

---

