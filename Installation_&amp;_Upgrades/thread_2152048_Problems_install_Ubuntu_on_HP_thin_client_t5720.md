---
title: "Problems install Ubuntu on HP thin client t5720"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by gert3d on 2013-06-06
Although I am able to install a number of other distro's (Mint 13, but not 14, Puppy, Crunchbang, AntiX) Ubuntu install crashes when it seems to test video properties. Same for Lubuntu 13.04
I have 1Gb memory in the t5720, and a HD attached, both working properly.
Is there any hope?
thanks

---

### Post by Cvxcvgg on 2013-06-06
Can we have a bit more information on your hardware? Is there an error you saw?

---

### Post by gert3d on 2013-06-07
> **Cvxcvgg said:**
> Can we have a bit more information on your hardware? Is there an error you saw?

Processor: AMD Geode NX1500
Videochip: SiS741GX

The problems (endless loop) start after the message: "Starting LightDM Display Manager"
I installed the distro's from a USB key:
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by Cvxcvgg on 2013-06-08
Well, LightDM is, as stated, a display manager. It is the default program for displaying the desktop for Ubuntu after 11.10, so I'd say it's a pretty important program for Ubuntu's functionality. Have you tried using any other boot disk creators than YUMI? If it's a problem with the setup of the live disk, another tool might help. I used UNetBootin, personally, and it worked for me. Or, you could always go through a bit of formatting and partitioning the hard way, and then write the .iso to the flash drive. If you have Windows XP or later, I can give you instructions on that, using Disk Part.

---

### Post by gert3d on 2013-06-09
I have now been able to install the Alternate version of Ubuntu 12 using UNetBootin (default option here did not work the CDROM could not be found at some point during installation). The install-option causes the information to be retrieved from the internet instead of the .iso on the USB key. It comes without a desktop, so I decided to install XFCE desktop. The system now is kind of slow, but that may be due to limitations of the thin client hardware.

---

### Post by gert3d on 2013-06-23
Updating the Alternate version of Ubuntu 12.04 to 12.10 was not a good idea: I got entangled again with the Display Manager.

However, I found that Xubuntu LTS release: 12.04, Precise Pangolin 32-bit: Desktop version, installs just fine. I used YUMI, very convenient.
The Xubuntu installer looks very nice and it either it does not employ LightDM, or it uses another approach that does not cause hanging of the T5740 thin client. After updating some 144 items, I do not dare to move to any further version however ....

---

