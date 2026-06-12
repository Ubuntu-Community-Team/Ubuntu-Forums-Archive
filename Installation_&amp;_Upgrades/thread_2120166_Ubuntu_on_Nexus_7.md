---
title: "Ubuntu on Nexus 7"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by Gr33nGapion on 2013-02-25
I currently have the desktop version of Ubuntu on my Nexus 7, but I want to put the recently released tablet version on instead. I tried following the instructions on [OMGUbuntu]("http://www.omgubuntu.co.uk/2013/02/how-to-install-ubuntu-phone-tablet-preview-on-nexus-devices") but I can't get adb to recognize my device. I'm assuming this has something to do with the fact I can't enable "debugging mode" through Android. 

I'm kind of a noob with this tablet stuff, so any help is greatly appreciated :p

---

### Post by TCSnyder on 2013-02-25
You must return to stock android first.

[https://wiki.ubuntu.com/Nexus7/Installation#Returning_your_Nexus_7_to_Stock_Android](https://wiki.ubuntu.com/Nexus7/Installation#Returning_your_Nexus_7_to_Stock_Android)

The ubuntu desktop does not have adb (android debugging bridge). There is a longer process of manually using fastboot to flash files, but this is much easier.

Flash to stock and use the tool to flash Ubuntu Tablet

---

### Post by Gr33nGapion on 2013-03-04
That makes sense. I didn't exactly know what adb was to begin with. I'll try this weekend :p Thanks!

---

