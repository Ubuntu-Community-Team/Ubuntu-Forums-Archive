---
title: "Prefix is not set"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by NobodyIIX on 2011-12-02
Hey,i am new to the forums and i just tried to install ubuntu on my PC.
I tried too many times to count them,using a USB,a CD/DVD,and Daemon tools to burn the ISO.I failed.Every time i get the error:
Try (hd0,0):NTFS5:error:"prefix" is not set
After 1 min i get to a screen where...ehm...there is a damaged image with burned-like pixels and my pc stucks there.Can someone help me?

Useful info:1)My windows are at D: not C: (teehee)
2)The first time,while i was download the ISO i was playing minecraft and when i got into ubuntu AFTER i rebooted my pc there was a screenshot of minecraft main menu kinda ruined and the rest of my screen had that burned like pixels.I thought the data was going to RAM and after i reboot my pc everything in RAM dissappears.
3)I like pie.

---

### Post by oldos2er on 2011-12-02
What are your hardware specs? Did you burn the ISO according to [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and check the md5sum? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by NobodyIIX on 2011-12-02
> **oldos2er said:**
> What are your hardware specs? Did you burn the ISO according to [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and check the md5sum? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2 GB ram
Intel Pentium duo 2.8
and Nvidia Geforce 8600 GT

---

### Post by NobodyIIX on 2011-12-02
Also i tried without using wubi,using the CD i burned with the ubuntu in it.It seems that the problems are in the graphics.Why?I don't get it,i have a good system and i have a small laptop that has windows XP AND ubuntu but an older version of them.I did it once using the low-graphics option and then i went to take a shower,once i got out i was on windows :S and i when i rebooted windows was the only option i had.<What> is going on?

---

### Post by Rubi1200 on 2011-12-04
Hi and welcome to the forums NobodyIIX :)

You can try using nomodeset:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I would also check the integrity of the image:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You can also try downloading the wubi.exe and relevant Desktop ISO, place them in the same folder, and then run the executable.

---

