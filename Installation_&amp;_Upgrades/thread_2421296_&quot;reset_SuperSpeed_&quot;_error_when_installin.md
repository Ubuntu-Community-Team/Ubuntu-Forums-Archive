---
title: "&quot;reset SuperSpeed &quot; error when installing ubuntu"
date: 2019-06-19
forum: Installation &amp; Upgrades
---

### Post by firefox1616 on 2019-06-19
[COLOR=#878A8C][FONT=IBMPlexSans][COLOR=#1A1A1B][FONT=inherit]Hello everyone, sorry to bother.[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#878A8C][FONT=IBMPlexSans][COLOR=#1A1A1B][FONT=&quot]I am trying to install Ubuntu on a external SSD with a Sata-USB adapter. Of course i want to dual boot with Windows 10 when the ssd is connected.
The problem is that when i finish the installation and have to reboot the system to make it effective, i got stuck to the error: "reset SuperSpeed gen 1 usb device number 2 using xhci_hcd".
I have searched online but can't find out what is the problem. Can someone help me?
Additional info: Ubuntu 18.04 LTS
SSD Drevo x1 120 GB
HP OMEN with windows 10 (Notebook)
[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by TheFu on 2019-06-20
Try a different USB cable and if the USB device supports power, connect a power supply.

---

### Post by firefox1616 on 2019-06-20
I tried both things, but nothing changed

---

### Post by TheFu on 2019-06-20
Appears that some USB controllers don't play nice with some USB devices.  There was a kernel patch in 2014 to address it for USB controllers at the time.  I would look at the USB controller and the USB devices to see if any are still having issues with the kernel version you have.  Often, different USB controllers are used in the northbridge and the southbridge on motherboards, to connecting to the opposite one you are using can be helpful.

Also, if there is a USB hub involved, try testing without the hub in the middle.

---

### Post by firefox1616 on 2019-06-25
I tried with power supply, but nothing changed. I searched for issues with kernel, but i didn't found some. But i'm possibly wrong. 
I have both: jmicron tech scsi disk device and ASMT 2115 USB Device. 
Can i ask once again for your help?

---

### Post by him610 on 2019-06-27
Many others with issues on similar/same device [https://www.google.com/search?q=ASMT+2115+USB+Device+specs&rlz=1CAASUL_enUS825&oq=ASMT+2115+USB+Device+specs&aqs=chrome..69i57.5921j0j8&sourceid=chrome&ie=UTF-8]("https://www.google.com/search?q=ASMT+2115+USB+Device+specs&rlz=1CAASUL_enUS825&oq=ASMT+2115+USB+Device+specs&aqs=chrome..69i57.5921j0j8&sourceid=chrome&ie=UTF-8")

---

### Post by firefox1616 on 2019-07-01
> **him610 said:**
> Many others with issues on similar/same device [https://www.google.com/search?q=ASMT+2115+USB+Device+specs&rlz=1CAASUL_enUS825&oq=ASMT+2115+USB+Device+specs&aqs=chrome..69i57.5921j0j8&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=ASMT+2115+USB+Device+specs&rlz=1CAASUL_enUS825&oq=ASMT+2115+USB+Device+specs&aqs=chrome..69i57.5921j0j8&sourceid=chrome&ie=UTF-8)

Yes, other issue but not the one i have. I recognize the disk i got no problem with it. And also the same thing happens with two different adapters, so i don't think that this is the problem. Am i right?

---

