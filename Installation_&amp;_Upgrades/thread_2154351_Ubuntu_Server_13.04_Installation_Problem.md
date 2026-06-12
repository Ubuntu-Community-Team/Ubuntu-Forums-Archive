---
title: "Ubuntu Server 13.04 Installation Problem"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by hughra on 2013-06-14
I am attempting to install ubuntu server 13.4 on my HP Pavilion  p7-1451. I am booting from a USB device which works fine. When I get to the GRUB menu and select an option I get a blank screen. I have attempted this with the prior version as well. I am lost and looking to build a local dev environment but cannot seem to get this to work. Any help is much appreciated

The computer came preinstalled with windows 8, I am trying to over it.

---

### Post by hughra on 2013-06-14
i believe I was able to fix the problem, in my bios i enabled legacy support and booted the usb in legacy mode. Also disabled fastboot and secure boot.

---

### Post by gordintoronto on 2013-06-14
I'm puzzled about why you installed Ubuntu Server. You have a pretty heavy-duty machine, you won't notice the overhead of running Ubuntu Desktop. (Or Xubuntu, if you are not a fan of Unity.) Desktop can do everything Server can do, and the admin tools have much less learning curve.

Secure boot should be OK, but according to what I have read, you can't boot from USB with fastboot enabled.

---

