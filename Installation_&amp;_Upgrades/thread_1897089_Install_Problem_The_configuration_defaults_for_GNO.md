---
title: "Install Problem The configuration defaults for GNOME Power Management"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by beanco on 2011-12-18
I was trying to install Meerkat as an upgrade from 10.04 yesterday...

I forgot to delete a bunch of stuff to ensure enough room...

I know having run df -h that the system is full...

So, 

1. how do I get in and delete stuff I do not need?

2. I assume doing 1. above will not actually let me log into the GUI, or will it?

If not, then i will retry to install Meerkat from the CLI... 


Thanks

Robi

---

### Post by ubix on 2011-12-18
Insert your installation Ubuntu CD, and start the Ubuntu from CD rather than from your HD. In order to do this you must make sure in BIOS, the boot order is set so that CD is searched for bootable media first. By booting from CD you will be running Ubuntu from CD rather than your hard drive. This means, after you start from CD you should not select **install**, but rather ***»Try Ubuntu«***, or something like that.

Once you are in CD version of Ubuntu, open terminal and _**mount**_ your hard drive. If you have trouble doing that before you ask for more help here please  check out the following web page: [http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)

---

### Post by beanco on 2011-12-19
Ubix,

I forgot to add that I do not have a CD.... I know, I know I hsould have created a live CD instead of doing it all from the CLI without the technical knowledge needed.....

I was able to get it taken care of... the sys-op where I work, a linux fan, did it for me.


Robi

---

