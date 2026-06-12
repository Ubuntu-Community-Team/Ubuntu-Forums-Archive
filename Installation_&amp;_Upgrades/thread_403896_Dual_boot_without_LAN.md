---
title: "Dual boot without LAN"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by griz on 2007-04-07
Hi all,
I've just bought a Presario B1900 notebook pre loaded with XP Pro.    It has a Broadcom 802.11 a/b/g WLAN.  I managed to load Edgy and there didn't appear to be any problems except with the WLAN, no wifi connection. When I removed Edgy though, I had to restore XP.  

Ok, now for the questions:  Is it possible to install Edgy with wifi enabled?  Or will Feisty be my best bet?  If I have a Fat32 partition setup, can that be used as the /home directory and will that have any impact on full access from XP?  What is the best partition setup for this (ie, can you direct me to a good howto please)?

Griz.

---

### Post by ndube on 2007-04-07
Edgy is pretty good at detecting supported wireless cards at install. If you don't have a wireless device listed in System > Administration > Networking, your wireless card is more-than-likely not supported. 

However, you could try using ndiswrapper. Here is a good how-to.

[http://ubuntuforums.org/showthread.php?p=2200725](http://ubuntuforums.org/showthread.php?p=2200725)

Obviously use the drivers for YOUR wlan card.

It is possible to use a FAT32 partition for your /home and be able to access it from both windows and ubuntu. However, I believe the installer would format your FAT32, so do be sure to backup your files.

---

### Post by ndube on 2007-06-20
I suggest starting from scratch. Here is a good walkthrough. 

[http://ubuntuforums.org/showthread.php?p=2200725](http://ubuntuforums.org/showthread.php?p=2200725)

If you continue to have problems, post exactly what you did and I'll go over it.

---

### Post by ndube on 2007-06-20
> **ndube said:**
> I suggest starting from scratch. Here is a good walkthrough. 

[http://ubuntuforums.org/showthread.php?p=2200725](http://ubuntuforums.org/showthread.php?p=2200725)

If you continue to have problems, post exactly what you did and I'll go over it.

sorry, replied on the wrong thread.

---

