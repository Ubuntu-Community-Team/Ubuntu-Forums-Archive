---
title: "Still attempting a clean load. 14 Sep 2014"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by Jack147 on 2014-09-14
I can't find my previous post.

Ubuntu-14.04-clean-load

 

 Attempting a clean load.  Presently have 11.04.
 I have Ubuntu 14.04 on a thumb drive.  Right click obtains this message, “This medium contains software intended to be automatically started. Would you like to run it?”
 When I click “Run” I get an error message “Cannot find the auto-run program”.
 

 What's wrong?  What's to be done?
 

 Albert J. Hoch Jr.

---

### Post by oldfred on 2014-09-14
You show no other posts under your user id.

An operating system is not like a program. You have to reboot and load it from BIOS or UEFI so it runs entire system. You cannot just click on it when in Windows (or Ubuntu).

You must have correctly installed it to DVD or flash drive not just copied it also. Or else it will not be bootable and then will not be seen as a bootable device when you reboot. 
Is your system newer and UEFI or older and just BIOS?

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

            How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

   Usb installer from Windows - pendrive
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

---

### Post by Jack147 on 2014-09-14
Ubuntu-14.04-clean-load

 

 Attempting a clean load.  Presently have  Ubuntu 11.04.
 I have Ubuntu 14.04 on a thumb drive.  Right click obtains this message, “This medium contains software intended to be automatically started. Would you like to run it?”
 When I click “Run” I get an error message “Cannot find the auto-run program”.
 

 What's wrong?  What's to be done?
 

 Albert J. Hoch Jr.
 

 09/14/14  8:50 PM
 
Attempting to follow oldfred's advice.

 I formatted my 4G USB (Universal Serial Bus) stick and loaded it with Ubuntu 14.04 using the “Startup Disk Creator” which I found on the dash.   Opening with the “auto-run prompt”, gave me the following message;

 -- This medium contains software intended to be automatically started. Would you like to run it?--The software will run directly from the medium "New Volume". You should never run software that you don't trust. 
  
 If in doubt, press Cancel.--
 

 When I clicked “Run” I got the error message “Cannot find the auto-run program”.
 

 My motherboard is an ASUS M2N SLI Deluxe.  Presently running Ubuntu 11.04 at 64 bits/   
 

 Is there an “Auto-run program” somewhere that should be loaded on my USB stick?

---

### Post by oldfred on 2014-09-15
Any auto run is a game or program you run inside your existing operating system. 

You may be seeing the wubi program which was for 12.04 and is essentially discontinued. It is not supported by Ubuntu, but a few users are trying to make that work. It was for new users but now is only for advanced users unless someone figures out details. 

You must reboot and choose the flash drive as the bootable device.

---

