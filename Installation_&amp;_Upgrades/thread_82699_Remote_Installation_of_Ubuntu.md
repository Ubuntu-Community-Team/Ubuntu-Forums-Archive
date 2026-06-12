---
title: "Remote Installation of Ubuntu ?"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by lcdguy on 2005-10-27
hi, i am realtively new to ubuntu. and i was wondering if it were possible say remotely install ubuntu on a local network using just a boot cd or a network boot on the computer instead of neading a cdrom (i don't have any blank cd's right now)

I quite familiar with setting things up like ftp, samba (SMB), or NFS shares if that helps in anyway.

What i have seen so far from the little time i have played with ubuntu is quite pleasing since it work with my soundcard almost right from the get go, which impressed me as i have yet to come across another distro to do that :).

---

### Post by stuporglue on 2005-10-27
You're looking for PXE. 

PXE lets you boot a comptuer over the network. You need a server offering the PXE boot, and a client that has 1) a BIOS that can do it, and 2) An ethernet card that can do it. 

You'll need DHCP and TFTP working, and maybe NFS.  

Searching the Ubuntu wiki for "PXE" and "Netboot" should point you in the right direction.

---

