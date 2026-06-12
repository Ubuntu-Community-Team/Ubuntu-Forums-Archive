---
title: "Can not get Ubuntu to install"
date: 2013-07-03
forum: Installation &amp; Upgrades
---

### Post by SRK123 on 2013-07-03
Hi Everyone, I have been trying my darn hard to get this OS to install on my PC but so far its been "mission impossible". Here are the steps I have taken so far (1) Cut CD and USB from ISO file. Checked to make sure all files in place (2) Made sure BIOS setting for boot order set to CDROM or USB first. Ubuntu would not load in either case. Instead it simply started Windows 8. (3) Used Wubi from within Windows to install CD boot helper. Again this failed and presented the following error message:  "could not retrieve the required installation files, etc". My system is a HP Envy 15 with Windows 8 installed. This is really undermining my confidence as I'm normally good with IT matters even though I'm not an expert. Any suggestions as I'm out of ideas here.

---

### Post by arpanaut on 2013-07-03
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

The information in that thread should get you started; installing Ubuntu on pre-installed Win8 systems can be tricky.

---

### Post by grahammechanical on 2013-07-04
I wonder what you mean by this

> [COLOR=#000000](1) Cut CD and USB from ISO file.[/COLOR]

Did you copy the files? Or burn the ISO image to the DVD/USB stick? If the USB stick has boot priority then something will load, even if the live session does not get very far. It should not load into Windows. The fact that the machine does load into Windows tells me 1) The hard disk has boot priority over the CD/USB. 2) The ISO image has not been burned to the CD/USB. The machine is switching the boot to the hard disk because it cannot find an operating system on the DVD/USB. 

Please confirm that the ISO image was burned or written to disk and not copied over.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Regards.

---

