---
title: "over-current change"
date: 2004-12-22
forum: Installation &amp; Upgrades
---

### Post by leclerc on 2004-12-22
Hello,

Long time linux user, first time with ubuntu...
I'm trying to set-up ubuntu on a Compaq Armada 100S laptop. CD starts up nicely and all but after the first reboot, getting to the configuration part where I'm supposed to add users and so on I start to get a constant scrolling message saying:

"hub 1-0:1-0: over-current change on port 2"

So far I haven't been able to get past this problem. Googling suggests that it could be a problem with the USB-port but all my usb-mouse is working perfectly!

Any ideas?

---

### Post by bendahara on 2005-02-03
I am new to Linux and Ubuntu.  I got an almost similar message "hub 1-0:1.0 over-current change on port 1". I am installing Ubuntu on a desktop, using a USB mouse, and a usb web-cam was connected to PCI USB 2 hub during installation. I also have a firewire PCI card connected. What could have caused the message to be displayed? 

Any one has any idea why I got the message?

Thanks.

---

### Post by jsien on 2005-04-12
Hi leclerc

I am also trying ubuntu (original CD 4.10) on a compaq armada 100s

Having overcome the random freeze problem (by disabling the apm in Bios) I am getting this same message "**hub 1-0:1-0: over-current change on port 2**" after the first reboot and it just keeps coming back so u can't do anything at all.  

I am new to linux and can't find much on google on this stuff yet.

I did try to re-install with option debian-installer/.../usb=off but it doesn't help

rgds
j

---

### Post by 20after4 on 2008-06-11
ran into this same problem today and found this on linuxquestions.org:

"The problem ended up being a power supply problem."  ([link]("http://www.linuxquestions.org/questions/linux-hardware-18/usb-over-current-change-killing-usb-ports-451561/"))

It turned out that the replacing the power supply fixed this issue for me so it might be worth looking into, especially if you have a spare power supply laying around that you could test out.

---

