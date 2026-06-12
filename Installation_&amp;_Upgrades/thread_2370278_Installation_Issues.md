---
title: "Installation Issues"
date: 2017-09-01
forum: Installation &amp; Upgrades
---

### Post by hmkurrelmeier on 2017-09-01
I have been unable to boot and install Ubuntu onto my computer from a USB stick. I have an ASUS G75VW. It runs windows 10. I downloaded Ubuntu and used Rufus to put it on a USB as a bootable USB. The problem is when I restart my computer and go to the UEFI/BIOS, there is no option to boot from the USB.

---

### Post by Bucky Ball on 2017-09-01
Welcome. Which release of Ubuntu are you trying to install? Sounds strange, but give this a try. It worked for me a few years ago. When the machine boots, you should be able to hit F12 to get to a boot device list. Does the USB show there with the UEFI option? Have you got Windows installed in UEFI?

If Win 10 was pre-installed, it will be in UEFI mode. If you or someone else installed manually, it may not be and that may be why Ubuntu USB is not giving that option. Does the USB appear as a boot option without the UEFI option in BIOS?

---

### Post by oldfred on 2017-09-01
If newer UEFI system, you probably need to turn off UEFI Secure boot and may have to turn on a setting somewhere that says allow USB boot. 

Is this an older system like these? Which are early UEFI. If so make sure you have newest UEFI from Asus.
       Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)

this is now old, 12.04 not supported anymore:
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)

---

### Post by hmkurrelmeier on 2017-09-01
It's the newest LTS offered on the Ubuntu website. Win 10 was not pre-installed, the computer originally came with Win 7. The USB does not appear as a boot option in the BIOS.

---

### Post by oldfred on 2017-09-01
Either a setting in UEFI/BIOS that needs to be turned on to allow USB boot or flash drive not correctly configured.

Did you verify that download of ISO was correct?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Some just have issues with one type of installer (Rufus normally works), or one type of flash drive or even one port on system where different ones work.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

