---
title: "Update Manager wants a command line verified"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by sls54 on 2010-08-27
I made a live USB memory stick / pendrive with Ubuntu netbook remix 10.04 using my desktop computer. I want to install / update my netbook that has no network function yet. I booted the desktop with the pendrive & ran update manager. I want to update the kernel so I will have the driver that will operate my netbook ethernet.
 
Acer AOD260 has Ethernet Controller: AR8151 v1.1 Fast Ethernet, Atheros Communications & Network Controller: Broadcom 4727 (rev 01)
and will not work from the current release of 10.04 (too new) but there are supposed to be drivers in the newer kernels.
 
Running Update Manager I get a box labeled "Debconf on ubuntu" & says "Configuring grub-pc". There is an entry box that says "linux command line:" & is empty. When I press the help button I get the message "The following Linux command line was extracted from /etc/default/grub of the 'kopt' parameter in GRUB Legacy's menu.lst. Please verify that is correct, and modify it if necessary.
 
The installer is hanging, Preconfiguring packages ..., probably waiting for a response, but I have no idea what to do.

---

### Post by mikewhatever on 2010-08-28
What makes you think updating the kernel will make networking work? Do you know what's the oldest kernel that will work? 
The kernel version of each Ubuntu release stays the same through the life cycle. Updating the kernel provides security and stability fixes, but not newer drivers. 
If you must run Linux on your netbook now, pick another distro with a newer kernel version. If you must have Ubuntu, 10.10 beta is scheduled for Sept 2.

---

### Post by sls54 on 2010-08-28
I have learned from other forums that kernel 2.6.34 has the updates for my hardware. 10.04 LTS has kernel 2.6.32. I am trying to update the kernel on the USB pendrive using my desktop in hopes that using that will allow me to intstall the ubuntu netbook remix onto my netbook will install the new kernel & get my networking / ethernet to work. Without the network I have not succeded updating from the netbook.
 
I don't think it matters that my netbook is dual boot with windows7. As I said I am trying to update the pendrive using the desktop so I can install the newest kernel to the netbook.  Otherwise, I expect when the new release happens in October, I can install ubuntu with no problems.

---

### Post by mikewhatever on 2010-08-28
As said above, kernels beyond 2.6.32 are not available for 10.04 from the repositories. You could add a ppa or another source, or compile your own kernel, but I rather doubt that can be done while running live from USB.

---

### Post by sls54 on 2010-08-29
Thanks, I guess I can wait a couple days for the 10.10 beta to come out. That will hopefully solve my problems.

---

