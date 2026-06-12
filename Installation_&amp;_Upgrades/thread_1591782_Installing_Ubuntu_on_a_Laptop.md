---
title: "Installing Ubuntu on a Laptop"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by jadarite on 2010-10-09
I am trying to find out how to install ubuntu on my laptop, it's NOT a netbook.

I downloaded the file, but I can only find USB boot options on desktop computers when installing from a USB stick. 

Also, Universal-USB-Installer-1.8.0.3 doesn't have a laptop version listed but it does have desktop listed.

Can someone clear up the confusion on these two things?  Am I limited to desktop only?

---

### Post by nlsthzn on 2010-10-09
Desktop version... laptop version... same thing :)

Download ISO... burn to CD (or on USB, then remember to set BIOS that you can boot from USB)...

Boot from media :D

---

### Post by jadarite on 2010-10-09
> or on USB

But in the Universal-USB-Installer-1.8.0.3.exe it only lists desktop.

When I go to BIOS on desktops, I see USB listed.
However, I don't see it on this laptop.

Also, it tries to download and won't install without internet connection.  So, it doesn't seem like it will work from BIOS even if it was listed.

I do use the USB stick for other stuff, so it's not a hardware issue.

---

### Post by nlsthzn on 2010-10-09
> **jadarite said:**
> But in the Universal-USB-Installer-1.8.0.3.exe it only lists desktop.

When I go to BIOS on desktops, I see USB listed.
However, I don't see it on this laptop.

Also, it tries to download and won't install without internet connection.  So, it doesn't seem like it will work from BIOS even if it was listed.

I do use the USB stick for other stuff, so it's not a hardware issue.

Well... if there is no option to boot from USB it is possible that the laptop does not have this feature :confused:

Follow the guide [here]("http://www.ubuntu.com/desktop/get-ubuntu/download") and use "Universal USB Installer" after downloading the desktop ISO... it will work fine on your laptop...

---

### Post by mikewhatever on 2010-10-09
If you laptop BIOS doesn't allow booting from USB, try upgrading the BIOS or boot from CD instead of USB.
There is no special laptop Ubuntu version. The desktop one is intended for both desktops and laptops.

---

### Post by lbrty on 2010-10-09
I would not recommend updating (also know as flashing) BIOS for this specific case as it can cause many other issues. BIOS updating/flashing is only recommended as an absolute last resort.

Keep it simple. 

Download Ubuntu by going [here]("http://www.ubuntu.com/desktop/get-ubuntu/download")
Burn the .iso to a CD
Insert the CD in the machine
Reboot the computer
Go into BIOS and change the boot order to boot from CD drive
Click Try Ubuntu
When you get to the Ubuntu desktop, goto System>Administration>System Testing and follow the prompts

---

### Post by kroq-gar78 on 2010-10-10
There are ways to boot from USB if you REALLY want to, but I think CD is more reliable (that's my own view, because CD boot is more widely used & supported). You can use CD or floppy boot mangers to boot from CD/ floppy then select USB, e.g. plob (the one I used on my 10 year old comp; [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)). Then burn plob to cd and put usb in (make sure no other USB storage devices are there; plug in after boot from usb); boot from plop cd. Then select the usb device from the menu and voila: you're done.

---

### Post by lbrty on 2010-10-10
> **kroq-gar78 said:**
> [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

Thank you for sharing this great tool! I will definitely be using it in the future.

---

