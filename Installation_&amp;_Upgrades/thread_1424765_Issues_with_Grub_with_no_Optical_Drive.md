---
title: "Issues with Grub with no Optical Drive"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by esa.attia on 2010-03-08
Hi,

I recently installed Karmic Koala (Desktop x86 version) on an IDE SSD drive (Brand name Solidata) via the live CD.  The installation went well and I got Ubuntu up and running very easily.

The problem I am having is that when I disconnect the CD-ROM drive. Grub has issues loading Ubuntu. I just get the Msg "Grub loading" then after 20 seconds it says "Grub loadingRead error".
Initially I thought this may be a grub2 issue so I got rid of it and installed the older version of Grub.
I still get the same issues except now it says "Grub loading stage1.5Read error" when i disconnect the optical drive. The problem goes away once the CD drive is connected to the IDE bus. 

My SSD is setup to be the Master while my optical drive is the slave. This issue only happens when I disconnect the optical drive or when I change the boot order in my BIOS (although boot order shouldn't really matter if the optical drive is not connected ). In any case the boot order for my IDE drive is set to the first position to boot. 

At the moment my machine is a PC104 form factor to be used on a robotics platform. Having the CD-ROM connected to my system is not an option. Any help would be very much appreciated. 

Cheers

---

### Post by JayLFC on 2010-03-08
You could try changing the sata port that your SSD is connected to if possible, if not the quickest and easiest way I guess would be to install from a usb pen drive. Good luck!

---

### Post by esa.attia on 2010-03-08
> **JayLFC said:**
> You could try changing the sata port that your SSD is connected to if possible, if not the quickest and easiest way I guess would be to install from a usb pen drive. Good luck!

Hi,

atm I'm using the IDE bus not SATA.  I have considered the USB  pen drive installation method but I would really like to know why this method on half works .

Cheers

---

### Post by esa.attia on 2010-03-10
I took the SSD disk and plugged it into a PC104 made by diamond systems and Ubuntu booted up beautifully. Seems like there is some weird GRub / Bios interaction that is buggy. I dunno what else to do. Is there some bios configuration I may have overlooked ?

---

