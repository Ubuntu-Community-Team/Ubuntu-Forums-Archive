---
title: "File not found at boot, when using live USB error is &quot;Missing Operatoring System&quot;"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by joshdb666 on 2010-06-13
So I'm usin Ubuntu 9.10 and installed it a couple of months ago. I was trying to figure out how to use Synaptic to fix some dependancy errors I was getting, and set it to remove a certain package. It said it had to remove other packages as well to do this, well that ended up being Gnome and a whole bunch of other stuff. Silly me.
So I was alright without having Gnome and went back to writing simple c++ from this book. I wrote a program to output a range of numbers and ran it but had written it wrong, so it would have ran on for hours. So I just killed the power and tried to start the comp again.

This time after the Dell boot screen it would tell me my system battery was low and strike F1 to continue or F2 to enter setup. Hit F1 and Im told that a file wasnt found and then it goes to the Ubuntu loading screen (The logo and some dots underneath) and then a black screen. Nothing else.
I figured I needed to reintall and dont have any CDs so tried to make a live CD and this time when I try to boot from USB device get a "Missing Operating System" error.
Its set to boot from USB device before harddrive. Need to know what to do to install again/recover old install.

Thanks.

---

### Post by darkod on 2010-06-13
Are you trying to boot from usb stick or usb cd-rom? What has creating liveCD has to do with booting from usb device?

The missing OS error would usually only be there if you are booting from the hdd, not the cd or usb stick. Either you don't have the boot devices order set properly or the usb stick is not bootable so it continues trying to boot from hdd.

---

### Post by joshdb666 on 2010-06-13
Yeah ,live CD was a typo, meant USB.

I think the USB stick may not be bootable, because when I downloaded the .iso it was actually a jzip archive. I did the process described here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) exactly to create the stick. Are there any other steps I need ot take to make it functional?

---

### Post by darkod on 2010-06-13
So, you did the Universal USB Installer procedure right?

And what do you mean by the ISO being jzip archive? An ISO file is an ISO file, it should have the .iso extension. I haven't seen otherwise, not for ubuntu ISOs.

Maybe that was the problem. Otherwise, I haven't tried the universal usb installer version but the ubuntu website seems to recommend it for creating usb stick in windows.

---

