---
title: "Unable to find Biostar Drivers"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by summersyn on 2008-07-12
I am very interested in installing Ubuntu to get away from the hassles of Windows XP, even tho I will be dual booting.  Either way, I (thankfully) decided to make sure all of my hardware would be compatible with Ubuntu.  I was able to find my Video Drivers without fail, however I could not find full support for my Motherboard.  I have a Biostar NF4 Ultra-A9A.  I was able to find ethernet drivers, however I also need to use the onboard audio drivers, as well as the USB 2.0.  I searched all I could, to no avail.  If anyone can assist, that would be greatly appreciated.

 Thank you...

---

### Post by overdrank on 2008-07-12
> **summersyn said:**
> I am very interested in installing Ubuntu to get away from the hassles of Windows XP, even tho I will be dual booting.  Either way, I (thankfully) decided to make sure all of my hardware would be compatible with Ubuntu.  I was able to find my Video Drivers without fail, however I could not find full support for my Motherboard.  I have a Biostar NF4 Ultra-A9A.  I was able to find ethernet drivers, however I also need to use the onboard audio drivers, as well as the USB 2.0.  I searched all I could, to no avail.  If anyone can assist, that would be greatly appreciated.

 Thank you...

Hi and welcome, I take it that the sound and usb are not working? You could use the command in the terminal ```
lspci
``` and this will identify your hardware and you can search for solutions then.

---

### Post by werries on 2008-07-12
I take it you havent installed. Try to see if you hardware works out of the box.
Have you tried booting a LiveCD?

---

### Post by logos34 on 2008-07-12
It'll work out of the box.  I have a TForce with same Realtek LAN and audio

---

