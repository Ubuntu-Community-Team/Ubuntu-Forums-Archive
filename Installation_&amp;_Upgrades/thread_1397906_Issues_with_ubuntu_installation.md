---
title: "Issues with ubuntu installation"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by preit on 2010-02-03
Ok, i am having a huge issue here.  lets just say I have two laptops and one internet connection.  I will give you the specs of both computers and then the issue
 
Computer A (CA)
-HP Pavalion tx1000cto running crappy windows vista (32bit) SP2
-2GB RAM
-AMD Turion 64X2 TL-60 @ 2.00GHz
 
Computer B (CB)
-Acer Eee PC 1005HAB with Windows XP
-2GB RAM
-Intel Atom N270 @ 1.60GHz
-NO optical drive what-so-ever
 
Two USB devices (i will refer to them collectively as "USB" as during my trouble-shooting I have done all steps on both in case there is a malfunction with one) both are 4GB each
 
Ok, so CB had windows XP and got massively infected with a bunch of random malware.  My Soldier needs this laptop for the training we are attending.  I have no optical drive or Windows recovery disc (plus, there is info on the thing that can't be replaced).  When turning on the computer, when trying to load windows, it goes into an infinite-boot (a BSOD shows for about 1/4th of a second...not long enough to get any info).  It will not boot into any safe-mode or anything for that matter.  I have read that linux is a better option for any netbook, so I decided to throw Ubuntu onto CB.  So...
I get onto CA to do some research (since CA can turn on and boot).  I come to the website [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) and follow those instructions (btw, i do have the .iso of ubuntu 9.10 installed already).  I get the ISO downloaded (which took 4 hours due to slow internet connection) and get the USB set up to be able to boot from.  When I boot CB with USB put in (i have put USB in all three USB-ports on CB) I keep receiving error:
 
Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key
 
I get the same issue with CA as well when trying to boot from USB.  While logged into windows on CA, I am able to put USB into drive and install Ubuntu.  When I do this, I am able to plug USB into CA, reboot, and load into Ubuntu and have full access.  So there doesn't seem to be an issue with a corruption in the .iso I downloaded.  The issue instead seems to be with the ability to boot from the usb.
 
-also, I have used unetbootin program to make the USB boot device, and receive the same issue.  Please, keep in mind that I am only able to login to any OS with CA (either windows or Ubuntu) and CB is just hardware for all purposes.
 
Thank you for your assistance.

---

### Post by stlsaint on 2010-02-03
Soldier?? (Army?) With CB being a netbook you will probably want to use a distro thats tailored primarily for the netbooks. Now there is [UNR]("https://wiki.ubuntu.com/UNR") you can try or since it is a Acer EEE consider [eeebuntu]("http://eeebuntu.org/wiki/index.php/Welcome#What_is_Eeebuntu.3F").
Also ensure that your bios settings are correct to allow booting from usb.

---

