---
title: "bootable SD card?"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by makuab on 2010-07-21
Im wondering If there is a program that can take a windows 7 ISO and create an installation drive out of an SD card.

---

### Post by makuab on 2010-07-21
bump

---

### Post by snowpine on 2010-07-21
You are asking in the wrong forum; this is the forum for discussing Ubuntu. Try a Windows support forum. :)

As far as I know (and I am not a Windows expert) the recommended procedure for installing Windows is to boot from your legally-purchased Windows install DVD-ROM.

Ubuntu can easily be installed from an SD card; let me know if you want to learn how. ;)

---

### Post by makuab on 2010-07-21
> **snowpine said:**
> You are asking in the wrong forum; this is the forum for discussing Ubuntu. Try a Windows support forum. :)

As far as I know (and I am not a Windows expert) the recommended procedure for installing Windows is to boot from your legally-purchased Windows install DVD-ROM.

Ubuntu can easily be installed from an SD card; let me know if you want to learn how. ;)

no no, Im wondering if there is a program in ubuntu, I want to dual boot (currently have ubuntu)  but I dont have a CD drive.

---

### Post by makuab on 2010-07-21
bump

---

### Post by snowpine on 2010-07-21
> **makuab said:**
> no no, Im wondering if there is a program in ubuntu, I want to dual boot (currently have ubuntu)  but I dont have a CD drive.

Ubuntu does not have a "Windows installer" program as far as I know.

It is possible Microsoft has a utility to legally copy their install ISO to an SD or USB device, but I don't think you're asking in the right place.

---

### Post by makuab on 2010-07-21
> **snowpine said:**
> Ubuntu does not have a "Windows installer" program as far as I know.

It is possible Microsoft has a utility to legally copy their install ISO to an SD or USB device, but I don't think you're asking in the right place.

Sigh... 

I just need a program like UNetBootin but instead of only ubuntu ISOs one that works with all ISOs

---

### Post by makuab on 2010-07-21
thanks for the help btw.

---

### Post by oldfred on 2010-07-21
I have not used plop but they say the next version will allow booting PCMCIA devices. Most computers will not boot them.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Create Windows 7 USB 
[http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb](http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb)
[http://www.boot-land.net/forums/index.php?showtopic=8944](http://www.boot-land.net/forums/index.php?showtopic=8944)

---

### Post by C.S.Cameron on 2010-07-21
1)Format SD card to NTFS using gparted.
2)Add boot flag using gparted.
3)Extract Win7 iso to card using Archive Manager, or (copy CD contents to card).
4)Install on poor unsuspecting computer.

---

