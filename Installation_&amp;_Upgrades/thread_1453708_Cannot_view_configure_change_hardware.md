---
title: "Cannot view configure change hardware?"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by skikir on 2010-04-13
OK I am windows 7 user trying to update my old Dell M65 (more for  educational purposes than anything else) I have tried several flavors of  Linux.  I've tried PCLinux OS and was OK but would not boot 30% of the  time and had an edgy feel to it.  So now I'm trying Ubuntu.   I down  loaded and boot to the CD.  Nice.  No network.  No wireless.  Could not  find any kind of "Control Panel" to view system settings or hardware or  add hardware.  Found "Hardware Driver" and clicked wireless card driver  and got to the internet.  OK! Looks good, feels good, let's try it.

I installed it to the hard drive and seemed OK but no net work again.   Went to "Hardware Driver" and no drivers are listed.  Now what I do.   I'm sure the driver is on the CD but how do I install it?  I can't even  tell Umbuntu I have a problem.

---

### Post by skikir on 2010-04-13
OK, so I reboot to CD.  loaded the driver the wireless and THEN  reinstalled Ubuntu.  Now the "Hardware Driver" had the wireless driver  there but when I tried to activate it, it asked for a password.  I put  in my password but it would not activate.  Tried root password and nada.   Is there another authentication password out there that I'm  miraculously supposed to know?

---

### Post by ajgreeny on 2010-04-13
Gnome control panel is still in the menu, but not actually enabled to show by default, but you can still use it with Alt+F2 and entering ```
gnome-control-panel
```
However it has nothing extra compared with the items already available in the System part of your menubar.

As to your wireless problem, I'm confused; you say you now have a wireless connection and it asks for a password.  If it is not your user password, perhaps it is the password or key for the encrypted (WEP or WPA) connection that you have found.  Assuming it is your own wireless network you are trying to connect to, you must have a password set, and hopefully remembered somewhere.

---

### Post by skikir on 2010-04-13
When trying to install the wireless driver in  "Hardware Driver" utility, when I try to activate the driver, it asks for a password.   I put in my sign on password and authenticat and then it looks like it's trying to do something/install but the driver does not activate even after rebooting.  So, I can install the driver and connect to the internet while booted to the Live CD but when installed and booting from the hard drive I cannot install the driver.  I can select and activate but has no effect.

I might add that in  "Hardware Driver" it also shows Nvidia drivers but when I try to activate them they return an error  "cannot fetch" from the web.

---

### Post by skikir on 2010-04-13
P/S  Thanks for the Alt+F2 trick.

---

### Post by pastalavista on 2010-04-13
Put your live CD in the drive, open System/Administration/Software Sources and check the box to enable a CD rom as a repository. Then run the Hardware Drivers tool again.

---

### Post by skikir on 2010-04-13
OK, tried that.  Still no go. It's like pulling the trigger on an empty chamber, nothing happens. 

How do I get to ndiswrapper?

 Thanks Pastalavista.

---

### Post by skikir on 2010-04-19
OK, figured it out.  The driver was not the right one.  Figured out how to install ndiswraper and loaded the Windows driver.  I don't understand why that driver shown would activate the wireless while booted to the Live CD but not after installation to the HD.

---

