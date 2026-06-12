---
title: "install fails on medion erazer x7815"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by medionX7815 on 2012-11-28
Hi,

I am trying to install Ubuntu 12-10 on a medion erazer x7815 md 98013 but it does not seem to be that easy.

The installation does not start unless I select noacpi, nolapi. But then when install has finished and the laptop reboots, it hangs, black screen...

I got the same thing more or less with opensuse linux version, it hangs at 40 percent of install...

Note that i got an old SATA hard disk installed with Ubuntu 10-10 and this disk boots successfully if connected with USB/SATA adapter on a USB port. 
It fails to boot when connected through the same USB/SATA adapter on USB3 port. 
It also fails to boot when connected to any of internal SATA ports.

The laptop works fine with its original windows7 SSD disk.

There is not much setting in BIOS, for SATA there is just RAID/ACPI/IDE... i checked using IDE or ACPI it does not fix the problem.

I am stuck, and will be very happy to get help on this.

Thanks

---

### Post by 2F4U on 2012-11-28
Can you please provide your hardware specs? A black screen is often the result of a graphics problem, but in your case I am not too sure. Did you add the parameters noacpi/nolapic to your grub configuration? If not, you can try to boot into recovery mode and modify the grub configuration.

[http://xtrabuntu.blogspot.de/2012/09/ubuntu-1210-simplifies-grub-boot-menu.html](http://xtrabuntu.blogspot.de/2012/09/ubuntu-1210-simplifies-grub-boot-menu.html)

---

### Post by medionX7815 on 2012-12-07
Great.... you are right, it was a video card problem.
The system was refusing to boot normally, blank screen.
But it was possible to boot into recovery mode, and then install Nvidia driver.
Problem solved.
Thank you

---

