---
title: "Boot usb-stick from floppy &gt; how to make boot floppy inside Windows"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by MacG10 on 2008-09-01
I have stripped an old laptop to the motherboard and screen that I want to turn into a photoframe. 

When I first started this project I was going to install Ubuntu on the harddrive, but I have decided to go away from this original plan as the harddrive is too loud when not inside a laptop casing (not very nice to have a loud photo-frame...) 

I have been google-ing a lot on the topic of making a boot-floppy so I can run an USB-stick with Ubuntu, but have come across the following problem:
I cannot seem to find a site that shows how to make a boot-floppy inside Windows that will enable USB. All sites seem to already have Ubuntu running on a computer to make a floppy from there. I only have one laptop that has a floppy-drive > the one I am currently working on. This laptop currently has Windows on the harddisk and this is where I need to 'make' the boot-floppy. Once I have this floppy I can discard the harddrive and run the floppy/usb combo.

Any help is appreciated, since I am currently stuck and really want to continue this project.

---

### Post by adewale on 2008-09-01
You have several options. 
1. Take a look at Unetbootin. Its has a windows exe that would enable you to install to your usb drive. 
2. I think ubuntu should be able to install directly to your usb drive. 
3. Superfloppy mode. I came across this when i used puppy linux. It had a simple program for installing to usb drives. So it gave the option of superfloppy for motherboards that can't boot directly from a usb device.

I'd say go for unetbootin

---

### Post by MacG10 on 2008-09-01
I should add that my BIOS does not support direct boot from USB, so that's why I need the floppy boot disk that will enable USB so it can then start up Ubuntu from stick...

---

### Post by adewale on 2008-09-01
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

This should do the trick.

---

