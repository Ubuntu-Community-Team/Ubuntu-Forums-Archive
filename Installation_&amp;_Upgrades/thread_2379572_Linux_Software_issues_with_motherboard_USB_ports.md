---
title: "Linux Software issues with motherboard USB ports?"
date: 2017-12-07
forum: Installation &amp; Upgrades
---

### Post by michael14 on 2017-12-07
On my motherboard i have 8 USB ports which 2 happens to be USB 3, I have tried Ubuntu on a live USB and a copy of Linux mint on the usb. Both of which isn't picking up any of my keyboards or mouses on the USB 2 ports. For whatever reason the only ports that is being detected for the keyboard and mouse is on the USB 3 ports.
My motherboard is the Gigabyte GA-970A-DS3P FX REV 2.1. I have the AMD FX 6300, With AMD RX 460 2gb OC video card with 8GB ddr3. Is this a issue that could be fixed in the live USB to test before installing the copy of Linux onto the Hard drive to dual boot with Windows 10? 

Edit: The keyboard does work tho on the option/boot menu of Ubuntu 17.10 operating system. It lets me select everything perfect. After that it stops.

---

### Post by QIII on 2017-12-07
Hello!

This is a longstanding issue with many Gigabyte motherboards.  [This thread]("https://ubuntuforums.org/showthread.php?t=2188370") is from 2014 and discusses your model of motherboard.  It has the fix you are looking for, but you can see how long Gigabyte has let this go on.

Cheers.

---

### Post by coffeecat on 2017-12-07
Hello, michael14. I too was plagued with this problem in a Gigabyte board a few years ago and wish I had noticed this fix then.

I'm just posting to comment on something in the thread that QIII has linked for you. The OP of that thread has committed the grievous error of running gedit with sudo in post #2. If you don't want to risk messing up the permissions in your home folder, run gedit with sudo -H, thus:

```
sudo -H gedit /etc/default/grub
```

Or simply use nano:

```
sudo nano /etc/default/grub
```

---

