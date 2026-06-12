---
title: "Problem with installing ubuntu on usb"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Gizmou on 2011-03-04
Hello there. Currently I am using network's pc where I am only a user (on windows xp) therefore I can't run programms which require administrator rights to run them e.g. pen drive linux to install ubuntu onto my usb.
 
I tried installing ubuntu unto my flash using Unetbootin but without any succes as it showed that there's no OS in the usb when I tried to boot from it.
 
The usb-creator which comes in the ubuntu iso seems to fail as well - when I choose my iso in -other- and try to actually open it - it just doesn't show it in the image section of the program. 
 
I would be very thankful if anybody could point me in the wright way to install ubuntu 10.10 onto a usb flash as I am very keen on starting to use ubuntu.
 
 
Thank you.

---

### Post by sikander3786 on 2011-03-04
Using UNetbootin, you can create a Live Ubuntu USB that won't save any changes between reboots.

Linux Live USB Creator is a much better choice for tasks like this.

[http://ubuntu4beginners.blogspot.com/2011/02/portable-ubuntu-persistent-usb-using.html](http://ubuntu4beginners.blogspot.com/2011/02/portable-ubuntu-persistent-usb-using.html)

---

### Post by C.S.Cameron on 2011-03-04
Have you checked your iso using MD5SUM?

Have you considered doing a full install to your pendrive?
Iinstall as you would to internal HDD, use manual partitioning and make sure the bootloader gets installed to the pendrive.

---

### Post by Gizmou on 2011-03-05
Thanks for replies.Seems it was Unetbootin corrupt install or possibly restriction on the pc I used to install the iso on usb. Using linux pen drive booting program solved the problem and worked like a charm.

Thanks,Solved.

---

