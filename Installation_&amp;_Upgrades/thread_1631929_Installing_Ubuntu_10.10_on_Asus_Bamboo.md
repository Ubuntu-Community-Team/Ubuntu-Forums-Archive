---
title: "Installing Ubuntu 10.10 on Asus Bamboo"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by lindoniel on 2010-11-27
Hi everyone,
I recently buied a new computer, an Asus Bamboo u33j with the following tecnical data:
- Intel Core i3, 2.26GHz
- nVIDIA GeForce 310M; 1Gb
- 4 Gb RAM
- 320 Gb HD
- Windows 7 home edition

I'd like to delete Win 7 and go with Ubuntu; I tried to make run the Ubuntu 10.10 CD already downloaded (AMD 64 bit) and after the purple screen with the points illumintaing I get this message:

```
BusyBox, v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system


```

What should I do?

Thanks already!

---

### Post by dino99 on 2010-11-27
you might have burn that cd  on a slower speed i suppose.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

digging around about the chipset builtin, it seems that you might have better chance with the latest kernel 2.6.37 (in natty)

[http://ubuntuforums.org/showthread.php?t=1393413&page=3](http://ubuntuforums.org/showthread.php?t=1393413&page=3)

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by richy2010 on 2011-01-04
Hi!
I am also thinking of buying this laptop:

Asus U33J 13.3 inch Notebook (Intel Core i5 460M 2.53GHz, 4GB, 500GB, DVDSM, WLAN, BT, Webcam, Windows 7 Home Premium 64-bit)

[http://www.amazon.co.uk/Asus-Notebook-2-53GHz-Windows-Premium/dp/B004AP9VU6](http://www.amazon.co.uk/Asus-Notebook-2-53GHz-Windows-Premium/dp/B004AP9VU6)

Could I ask if anyone has been able to get the Wireless working?

Also if the webcam and mic are working ok?

Thanks in advance for any info. richy

---

### Post by THAiSi on 2011-01-11
My girlfriend has bought this laptop (15" version). Wireless works fine, but somehow X will not run using the nvidia proprietary drivers. Therefore, desktop effects can not be enabled. I think that because everything is software rendering the battery is drained faster under ubuntu than under windows. I'm still figuring out to fix the driver problems of the video card. Webcam was working fine, I haven't tested the microphone.

---

### Post by milan.opa on 2011-11-13
I've tried Ubuntu 11.04, Fedora 15 & 16, latest KUBUTNU 11.10 and it looks like KUbuntu is currently the best solution. Though I never used KDE before it has far more options then GNOME3 at the moment, plus is free of bugs that annoy (screen brightness and volume not remembered on reboot etc.).

I couldn't resolve NVidia Optimus issues with neither Bumblebee nor IronHead so I switched it off.

Instructions for U36JC that can be found at [https://help.ubuntu.com/community/Asus_U36JC](https://help.ubuntu.com/community/Asus_U36JC) apply for U33J laptop as well.

If you follow every step described you will end up with 4.5h of battery life (Nvidia disabled) and suspend and hibernation working good (you must complete this step, otherwise laptop won't hibernate or suspend when optimus is disabled).

Good idea is to go to synaptics site and download multi-touch gestures for the touch-pad.

I found else to work out-of-box.

---

