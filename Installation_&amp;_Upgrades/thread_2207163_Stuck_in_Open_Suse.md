---
title: "Stuck in Open Suse"
date: 2014-02-22
forum: Installation &amp; Upgrades
---

### Post by amilopowers on 2014-02-22
Hi 

I have Open Suse 12.3 on my Asus Zenbook and want to change to Ubuntu. 

Ubuntu is on a partitioned USB 3 Stick. I created it on my mac with the how to from ubuntu.

How can I boot from the USB? I have GRUB 2 on the Asus with Open Suse. I just figure out how to boot form this stick. 

Thanks in advance,
Ulrich

---

### Post by grahammechanical on 2014-02-22
How did you install OpenSuse? Was it pre-installed? If the machine fails to boot from the USB stick it usually means that the USB port does not have boot priority over the hard disk.

Regards.

---

### Post by arkanabar2 on 2014-02-22
grahammechanical is right.  You have to alter boot priority in your BIOS in order to boot from the USB stick.  Each model's BIOS tends to be just a little bit different, so you will have to consult your laptop's documentation.  If you can't find it, give us the exact model of your laptop and maybe somebody will be able to find it for you.

---

### Post by amilopowers on 2014-02-22
Okey, thanks!

I have a Zenbook UX31E. It came with Win 7. so i knew how to boot from USB when Windows was on it... Is the bluescreen menu the BIOS?

Sorry i am a Mac user...

---

### Post by amilopowers on 2014-02-23
I managed now to boot from the USB.

In the menu i can choose either "Install Ubuntu" or "Use Ubuntu without installing" and nothing happens. I see just a black, blank screen....

---

### Post by amilopowers on 2014-02-23
Guys i could install it! I mean 13.1. 

12.04 LTS just didn't work. I have no idea why.

---

### Post by mastablasta on 2014-02-24
try nomodeset boot option: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

