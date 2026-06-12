---
title: "Hang During Dual Boot Installation"
date: 2017-12-20
forum: Installation &amp; Upgrades
---

### Post by Robk29 on 2017-12-20
I have Ubuntu operating via a USB and have attempted to do a dual boot set-up with Win 10. 

During the installation process I elect to download updates and install third party software and drivers. I also enter a password to disable secure boot and proceed. It hangs after a few moments and requires a manual shut-down and reboot.

I am using a low end Acer which I purchased earlier this year for this purpose, I assume it has enough horsepower especially as it runs with (that resource hog) Windows 10.

Any ideas? :confused:

---

### Post by yancek on 2017-12-20
Windows 10 is probably installed with UEFI so you need to boot and install Ubuntu UEFI also or you will have problems booting.  The link below is to the official Ubuntu documentation on dual-booting using UEFI so give that a read.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-12-20
Is Windows fast start up or hibernation off?
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

And Acer has a unique requirement of "trust". Once installed you have to have UEFI Secure Boot on, set a UEFI password, and enable trust on Ubuntu/grub /.efi boot files from within UEFI.
You also need to have updated UEFI to newest version, some older threads mention downgrading UEFI, but newer threads have you upgrading to newest UEFI from Acer.

       
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by Robk29 on 2017-12-22
Thanks for the response, I am working my way through the potential issues highlighted.

---

