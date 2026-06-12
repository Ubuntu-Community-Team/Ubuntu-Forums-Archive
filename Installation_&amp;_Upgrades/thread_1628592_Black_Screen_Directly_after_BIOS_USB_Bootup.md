---
title: "Black Screen Directly after BIOS USB Bootup"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by theBackup on 2010-11-22
Hello, I've been trying to test/install Ubuntu on my HP DM3 laptop for some time now and I have run into some serious troubles. My laptop is running Windows 7 currently and has an AMD processor. As my laptop doesnt have a disk drive the only option has been to use a USB drive but unfortunently directly after BIOS the screen turns black with the backlight. Even if I try to change the bootorder when the USB is in it appears to overide BIOS and doesnt let me get to the that BIOS screen. I have attempted downloading multiple times and have had good MD5's. I have tried both the 10.04-64bit and 10.10-64 bit with the same results.
Could anyone help me out?

---

### Post by Quackers on 2010-11-22
Welcome to UF :-)
Can you boot from the usb and select "try ubuntu"? Does that load the Live desktop?

---

### Post by sikander3786 on 2010-11-23
Welcome to Ubuntu :-)

How was the USB prepared? Here are some options.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

If the USB drive has been prepared properly, Bios should not ignore it unless it doesn't find anything bootable on the drive.

Try with some other USB creation software and if that doesn't help, try with some other USB flash drive.

> Even if I try to change the bootorder when the USB is in it appears to overide BIOS and doesnt let me get to the that BIOS screen. 

You mean you are unable to enter the Bios menu or it just ignores your settings?

Sometimes USB drives appear unded HDD menu and you need to change boot priority there.

---

### Post by theBackup on 2010-11-23
I have tried both different USB installers with different downloads of the same Ubuntu version same thing happens both times. I cannot even get to the live screen and cannot choose boot from Ubuntu. 

"Even if I try to change the bootorder when the USB is in it appears to  overide BIOS and doesnt let me get to the that BIOS screen. 			 		"

By this I mean the USB overrides all BIOS functions and I cannot even attempt to change the boot order as it will go straight to black screen even if i try

---

### Post by adrien214 on 2011-02-13
Try looking [here]("http://ubuntuforums.org/showthread.php?t=1329909").

It think it's insane PC manufacturers are coming up with ways of making it harder to make a clean linux install on their MS machines.

---

