---
title: "Double failure with installing 10.04LTS"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Siggehandf on 2010-04-30
Okay, I really had high hopes for this version. But both my laptop and workstation are doing lockup at login screen.

I have somewhat managed to fix the laptop, x100e, by not being on battery and installing the ATI driver. But then the wireless doesn't work, nor do the drivers I had working with 9.10 (RT8192SE). So, that's scrapped. A laptop without wireless is pretty useless.

Workstation does a complete lockup on login aswell. HasNvidia 9300 onboard card. But at this point, I don't want to find out what else is waiting when I fix that.

I was really expect a rock solid release since it was going to be LTS. But at the moment it's pretty useless to download and I have been using Ubuntu since 7.xx series.

---

### Post by eltonw on 2010-04-30
> **Siggehandf said:**
> Okay, I really had high hopes for this version. But both my laptop and workstation are doing lockup at login screen.

I have somewhat managed to fix the laptop, x100e, by not being on battery and installing the ATI driver. But then the wireless doesn't work, nor do the drivers I had working with 9.10 (RT8192SE). So, that's scrapped. A laptop without wireless is pretty useless.

Workstation does a complete lockup on login aswell. HasNvidia 9300 onboard card. But at this point, I don't want to find out what else is waiting when I fix that.

I was really expect a rock solid release since it was going to be LTS. But at the moment it's pretty useless to download and I have been using Ubuntu since 7.xx series.

There are known issues with wirless connections. (You haven't mentioned what wireless card is on your machine. However, there is a fix already out. You can install a patched kernel by downloading Ricardo Salveti's kernel image from:
[http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb]("http://rsalveti.net/pub/ubuntu/kernel/lucid/linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb")

---

### Post by sfdrew on 2010-05-04
If you are still using the 8191SE wireless card, the way I got mine to work was by removing network manager and using wicd. For some reason it didn't work with network manager. 

I have mine working on 10.04 x64 doing it that way.

---

