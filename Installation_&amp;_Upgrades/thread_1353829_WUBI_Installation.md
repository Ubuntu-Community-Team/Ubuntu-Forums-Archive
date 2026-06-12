---
title: "WUBI Installation"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2009-12-13
I am trying to install  UBUNTU inside windows XP - using WUBI - however I keep getting  an error message from my COMMODO Anti Virus/ Firewall that a virus has been detected.
It seems that whatever I try to do - UBUNTU will not install. On one ocasion I by passed the error, but Ubuntu would not run after the install At the opening screen everything froze and I could do nothing-. Guidance please.

---

### Post by phillw on 2009-12-13
> **Dyffo said:**
> I am trying to install  UBUNTU inside windows XP - using WUBI - however I keep getting  an error message from my COMMODO Anti Virus/ Firewall that a virus has been detected.
It seems that whatever I try to do - UBUNTU will not install. On one ocasion I by passed the error, but Ubuntu would not run after the install At the opening screen everything froze and I could do nothing-. Guidance please.

It has been reported that some AV doesn't like Wubi. The safest way is to disconnect from the internet, turn your AV off, reboot with it off, install Wubi, turn the AV back on & reboot. You can then re-connect to the internet.

Regards,

Phill.

---

### Post by Dyffo on 2009-12-14
> **phillw said:**
> It has been reported that some AV doesn't like Wubi. The safest way is to disconnect from the internet, turn your AV off, reboot with it off, install Wubi, turn the AV back on & reboot. You can then re-connect to the internet.

Regards,

Phill.

Hi Phill - I have  tried to install as you suggested. Problem was that the download took 5 hours, so I set this up to run overnight.This morning the download completed but the error message that permission to install had been denied. So basically nothing happened. However I notice hat in my C Drive there is a folder for Ubuntu. If I open this I have Disks,Install, Winboot. If I open Install I have Ubuntu Desktop as a zip. Can I write this or open this in some way to install "within" windows. I do not want a dual boot with having to repartition.

---

### Post by darkod on 2009-12-14
Unfortunately it sounds like the files were copied but it failed at the last step, modifying the windows boot loader. Often the windows bootloader is defensive and makes problems to be changed by an application (wubi.exe), this is sort of protection too.
With XP using boot.ini in C: it's easier to modify manually than vista/7 but I don't use wubi and can't give you the exact command to enter.
Try google with something like "adding wubi entry to boot.ini". Also, in case you don't know, you will have to enable seeing hidden files to show boot.ini in XP. Be careful if modifying it, doing it wrongly can make your XP not boot either.

---

### Post by Dyffo on 2009-12-14
> **darkod said:**
> Unfortunately it sounds like the files were copied but it failed at the last step, modifying the windows boot loader. Often the windows bootloader is defensive and makes problems to be changed by an application (wubi.exe), this is sort of protection too.
With XP using boot.ini in C: it's easier to modify manually than vista/7 but I don't use wubi and can't give you the exact command to enter.
Try google with something like "adding wubi entry to boot.ini". Also, in case you don't know, you will have to enable seeing hidden files to show boot.ini in XP. Be careful if modifying it, doing it wrongly can make your XP not boot either.

I have solved the problem. I scrapped the UBUNTU idea, downloaded Linux Mint 7 and ran the " Install inside Windows Pack". ALL works perfectly

---

