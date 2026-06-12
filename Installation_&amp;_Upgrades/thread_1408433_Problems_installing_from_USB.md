---
title: "Problems installing from USB"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by sticksnleaves on 2010-02-16
I'm trying to install Ubuntu Server from a USB drive. I can boot into the drive but when I'm trying to do an install I get a "can't detect CD-ROM" error. Does anyone know how I can get past this?

---

### Post by phillw on 2010-02-16
Hi and welcome to the forums

I'm not sure what method you used to create the usb image, but if it is not working , I'd suggest heading over here --> [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

That has the steps required, depending if you have Ubuntu / Win etc on the computer you're creating the usb-stick from.

The section I believe you need is > If you get "Incorrect CD-ROM detected" error on  detection stage, reboot, press F6 and then ESC to go to manual boot line  editing, and add the option 'cdrom-detect/try-usb=true'. On Ubuntu 9.10  server edition the install menu will be shown right after reboot. Chose  "Help" and then press F6. At the boot prompt type "install  cdrom-detect/try-usb=true" and hit enter. 
 



Regards,

Phill.

---

### Post by sticksnleaves on 2010-02-16
I've been staring that the Installation/FromUSBStick page for hours now. Unfortunately it doesn't seem to have any insight.

I did try the detect-cdrom thing without any luck.

I installed the image onto the drive using the pendrivelinux stuff from Windows. Specifically [http://www.pendrivelinux.com/run-ubuntu-9-10-server-edition-installer-from-usb/]("http://www.pendrivelinux.com/run-ubuntu-9-10-server-edition-installer-from-usb/")

---

### Post by phillw on 2010-02-16
> **sticksnleaves said:**
> I've been staring that the Installation/FromUSBStick page for hours now. Unfortunately it doesn't seem to have any insight.

I did try the detect-cdrom thing without any luck.

I installed the image onto the drive using the pendrivelinux stuff from Windows. Specifically [http://www.pendrivelinux.com/run-ubuntu-9-10-server-edition-installer-from-usb/](http://www.pendrivelinux.com/run-ubuntu-9-10-server-edition-installer-from-usb/)


Hmm, most odd - pendrive linuxes' instructions just 'work' - I always send people over to them. I'm a bit stuck. 

Try re-creating it using their instructions - If you've still no joy, then you can use unetbootin to achieve the same ends --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

That is a method some use & I know it works (but, so does the pendrive linux one)

Sorry I can't help you more :-\

Regards,

Phill.

---

### Post by sticksnleaves on 2010-02-17
I finally got this working last night. I used the usb-creator on my UNR netbook and it worked fine. The pendrive and Unetbootin Windows methods didn't work for me. Thanks for your help

---

