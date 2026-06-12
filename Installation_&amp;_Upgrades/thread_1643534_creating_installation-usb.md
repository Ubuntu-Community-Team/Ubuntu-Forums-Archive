---
title: "creating installation-usb"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by prudra on 2010-12-12
I have 32-bit Intel Atom (HongKong based) OEM  Netbook a linux/gui OS(not Ubuntu)where I want to install Ubuntu-10.10 and I am now downloading ubuntu-10.10-netbook-i386.iso.
In the present case I created the installation-usb by running the terminal command
#dd if=XXXXx.iso of-/dev/sdb b=4M
Will the ame command on this non-ubuntu platform create the installation-usb? Your Homepage gives the procedure only on windows/mac/ubuntu platform.

Thanks.
P.Rudra.

---

### Post by dandnsmith on 2010-12-12
I think that, if you check, you'll find that it wasn't an iso file with which you performed the dd (rather it was an image file, created to be loaded that way).

With an iso file you have to create a usb installation with a suitable sequence to create the necessary file structure and files on the usbstick (not just copying it with the dd).

[www.pendrivelinux.com](www.pendrivelinux.com) contains the necessary instructions for both linux and Windows installation on such a stick - look near the bottom of the page.

---

### Post by sikander3786 on 2010-12-12
Welcome to the forums :-)

In addition to above post, these links might also help.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

