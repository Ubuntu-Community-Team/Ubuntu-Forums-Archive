---
title: "cannot install Ubuntu Server 10.10 from USB"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by mr_arc on 2011-04-16
Hi all

I have a [Proliant Microserver](http://h18004.www1.hp.com/products/quickspecs/13716_na/13716_na.html) and am attempting to install Ubuntu Server 10.10 on it. The server has no optical drives so I am using a USB stick.

I am using the ISO from here;

[http://www.ubuntu.com/business/get-ubuntu/download](http://www.ubuntu.com/business/get-ubuntu/download) (64bit) and have verified the download with the MD5 checksum.

and I am using the instructions on that page to create the installer (from Windows 7)

Which involves using

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

I have created the installer on multiple different media types, and also tried creating it on another machine. The creation goes fine, the problems arise when I try and install on the server.

It boots fine, begins going through the process of install and then gets to a point where it is Loading Installer Components from the CD.

It does around 30% of them and then throws an error saying it cannot read a file, and to try again - if it keeps failing then test the integrity of the CD.

There is no CD though.. and despite re-creating the installer on different media and different machines.. it crashes out at the same point each time,.

I have tried backing up and letting it test the integrity of the 'CD' but as it isn't a CD.. it gets confused and asks for a driver so it can access it properly.. which I don't know what to enter there..

Halp!

---

### Post by dino99 on 2011-04-16
unetbootin might work

[http://techie-buzz.com/foss/create-bootable-ubuntu-10-04-installation-disk-with-unetbootin.html](http://techie-buzz.com/foss/create-bootable-ubuntu-10-04-installation-disk-with-unetbootin.html)

---

### Post by mr_arc on 2011-04-16
thanks for the reply. I have also tried that method, and that doesn't work either. If I install it on the USB stick as a 'Live' install (and give it 4gb for persistance) than it boots - gives me the option to run/install etc but none of them work. They just flash off the menu and then back again.

If I install it as 'Server Installation' then it gets me to the same point as the method I outlined in the opening post.

I've got a for a Net install (booted from USB) and it seems to have gone through and past that stage. Just running the rest of the install now.

I'd like to work out what was causing the problem earlier though

---

