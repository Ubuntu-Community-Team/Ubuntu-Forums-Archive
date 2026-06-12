---
title: "can't  install 10.10 desktop vers"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by dmkotev on 2010-11-04
Hello everybody. 
 I'm trying to install the desktop version on my laptop but i'm having an issues. I wrote the .iso file on a CD and restart my pc to boot. So -> the pc founds the medium, i'm choosing the language, i'm choosing "Install ubuntu" and nothing happens. The dots srarts to blink and that's all. When i press anykey opens an cmd promt (something like that) and there's a lot of errors - for example: ... file failed to open due to unknown user id", some files are missing and so on. I tried "try ubuntu without installing" but the same thing. I hear a sound (i guess this the "srart sound" of ubuntu) and that's all. The orange screen, the icon in the middle and the blinking dots. 
 I made two CDs - one burned with win 7 integrated soft - right click and "burn disk image", and other burned with infra recorder. Nothing changes. Ideas?

---

### Post by wilee-nilee on 2010-11-04
> **dmkotev said:**
> Hello everybody. 
 I'm trying to install the desktop version on my laptop but i'm having an issues. I wrote the .iso file on a CD and restart my pc to boot. So -> the pc founds the medium, i'm choosing the language, i'm choosing "Install ubuntu" and nothing happens. The dots srarts to blink and that's all. When i press anykey opens an cmd promt (something like that) and there's a lot of errors - for example: ... file failed to open due to unknown user id", some files are missing and so on. I tried "try ubuntu without installing" but the same thing. I hear a sound (i guess this the "srart sound" of ubuntu) and that's all. The orange screen, the icon in the middle and the blinking dots. 
 I made two CDs - one burned with win 7 integrated soft - right click and "burn disk image", and other burned with infra recorder. Nothing changes. Ideas?

Check the md5sum of the ISO and cd. Also make sure you use the windows virtual partitioner disk manager if it is W7 to resize it.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also if you don't know how many partitions are on the computer and the limitations of the amount allowed, give us a screenshot of the disk manager or post the boot script in my signature in code tags, just to make sure your not heading into dangerous territory.

---

