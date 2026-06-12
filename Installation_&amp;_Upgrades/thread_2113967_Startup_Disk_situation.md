---
title: "Startup Disk situation"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by ivotkl on 2013-02-08
Hello. I'm trying to make a bootable Raspbian USB stick just to test the software on a regular non-Pi box. I just wanted to check if there's anything I'm doing wrong.
 
OS disk image has img extension and I am able to open it with Startup Disk Creator. File was originally a md5-verified iso, mounted as network, then copied and pasted. I am using a Kingston Data Traveler 108, of 8.0 GiB, formatted using Gparted and also with SDC.
 
Regardless which app I use to format it, I get "Installation error" when trying to do it. Is there any other way to make a bootable USB Stick using Ubuntu or any workaround to problem?
 
Thanks in advanced.

---

### Post by westie457 on 2013-02-08
Hi, you might have better luck using this, [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Also you might have to convert the .img file to a .iso. Take a look here for guidance, [http://www.mopedia.co.uk/2008/02/convert-img-to-iso-in-ubuntu.html](http://www.mopedia.co.uk/2008/02/convert-img-to-iso-in-ubuntu.html)

---

### Post by ivotkl on 2013-02-08
Thank you westie for the quick reply. I do have the ISO, but it was not being recognised by ubuntu disk creator. So, I turned it into an IMG file.

I used that pendrive linux (or similar, I think it was unetbootin), but on Windows some years ago.

---

### Post by Cheesemill on 2013-02-09
> **ivotkl said:**
> I just wanted  to check if there's anything I'm doing wrong.
What you're doing wrong is trying to run Rasbian on a normal PC. This will never work.

Rasbian is compiled for the ARM architecture but your PC uses either i386 or amd64, they are completely incompatible.

---

### Post by ivotkl on 2013-02-09
Cheesemill, then that may be the reason why I got an installation error code. I'll try a different distro then and wait until my Pi box comes (hopefully 2 weeks or so from now) to boot a Raspbian.

---

