---
title: "Cannot install Ubuntu 6.06 with Volari V3 Video Card"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by firefoxu on 2006-09-07
I have P4 2 GHz dell desktop with Windows XP Home. I installed a 80 GB second hard drive and tried installing Ubuntu 6.06 on it but when I boot from the CD and chose to install all I get is a blank screen with very small text somewhere on top of monitor which is not readable. I tried changing the resolution before installation from the options at the bottom of the screen on the install option screen. I am not sure how to get around this issue while installig Ubuntu.

I had an old video card and replaced my Volari V3 with it and tried to install CD and everything was fine. I like Volari V3 video card as it has a DVI output which I can plug it to my LCD monitor. 

Is there any other way to get around this issue? Why can't Ubuntu install on a computer with Volari V3?

Thanks in advance.

---

### Post by zxee on 2006-09-07
It looks like there are some drivers here: [http://www.opendrivers.com/categorycompany/12/1142/display-and-video-xgi-free-driver-download.html](http://www.opendrivers.com/categorycompany/12/1142/display-and-video-xgi-free-driver-download.html) 
Or do a search on that video card with linux. Getting the driver loaded though will require some commandline use and probably a usb flash drive.
As to why it's not supported-I suspect like most open source compatibility issues the manufacturer of the device has little or no interest.
I hope you don't read that as an "attitude" it's just that open source develpers do find ways to make many devices work-mostly without help from device makers and the card you have is either a specialty item, rare or both.

You could also install ubuntu with the video card that works get the driver for the card you're having problems getting recognized, and then shutdown replace the card and reboot.

---

