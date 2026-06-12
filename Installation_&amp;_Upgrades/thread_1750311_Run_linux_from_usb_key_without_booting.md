---
title: "Run linux from usb key without booting"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by supershin on 2011-05-05
Hi, I'm looking to run linux from a usb key without booting from it. Just plug it in and it starts from windows. 

I seem to recall something like this but can't find it. I found portable apps and portable ubuntu(site seems down) but nothing like I described.

Perhaps someone can point me in the right direction?

---

### Post by Joe of loath on 2011-05-05
Portable Virtualbox/Qemu??

Bear in mind you need admin privileges on Windows to use Virtualbox.

---

### Post by supershin on 2011-05-08
The solution I saw didn't require admin privileges. I guess I must've mixed up installing Linux on usb and running portable apps. Though I swore there was a linux on usb that didn't need editing bios to boot from usb.

---

### Post by ottosykora on 2011-05-08
the point is to install drivers, so this is what you need the admin rights under windows for. 
Even for things like Quemu you will have to install drivers, in fact strictly spoken you do not need them, but then it will be no fun as start up of the linux distro will take some 30minutes or  more without the accelerator.

Other solution is colinux.
Yes this will run kind of within windows, if you have lot of time (it will be slow)
[http://www.ubuntugeek.com/portable-ubuntu-ubuntu-system-running-as-a-windows-application.html](http://www.ubuntugeek.com/portable-ubuntu-ubuntu-system-running-as-a-windows-application.html)

google for pubuntu
(stands for portable ubuntu)

but also this will definitely need some 4 drivers to be installed, so also here admin rights are must, no way around that.

---

### Post by Joe of loath on 2011-05-08
I have used DSL inside Qemu on Windows without being admin, but DSL sucks.

---

