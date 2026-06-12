---
title: "VMware Kickstart Install Boot Issues"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by photoadrian on 2011-08-23
I have set up an Ubuntu Server for unattended installs.  I've got the DHCP, TFTP, and Web Server, plus a basic kickstart file that reads:

install
url --url [http://installer/ubuntu](http://installer/ubuntu)

My client system is a VMware ESXi guest (2 proc, 2Gb memory, standard everything else for Ubuntu i386 32-bit system).  I'm walking through the process just as if I were booting from the CD.  (The intent is to eventually pull everything 

When my client system reboots, I get the purple square with "Ubuntu 11.04" on it, and then the screen goes blank and I get a flashing cursor (line) in the top left hand corner.  The system does not go any further.

Unfortunately, I cannot get the grub system to go into the break so I can modify things.  I'm fairly sure that it's a vga problem (although why the netinstall does it and the CD install doesn't is beyond me).

The question is - Is there something I can put in my kickstart file that installs a grub config that produces a menu with "local boot" as the default instead of the "kick straight into the OS"?

---

