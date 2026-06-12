---
title: "Dual Boot ubuntu 13.04 with windows 8 installation problem (Bluetooth fails to load)"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by qed1999 on 2013-07-07
Hi to all

  I am trying to configure Ubuntu 13.04  in a new Toshiba Satellite L850-1MK computer. Windows 8 are pre installed already. 
  After many trials, I managed to install it in a separate partition, using USB bootable disk and the nomodeset option and disabling Faststartup and Secure boot from the BIOS.
   
  I have never managed to see Grub loader, the system loads directly to windows 8.
   
  When I tried to use the Boot repair disk or the “Try Ubuntu without installing” option from the bootable usb, I can not enter Ubuntu desktop environment, it crashes and I am getting the following message:

  Bluetooth: error in firmware loading 
  Bluetooth: loading sysconfig file failed
   
  And the command line interface only appears.
   
  In case it helps my network card is:

  Qualcomm Atheros AR9485WB-EG Wireless Network Adapter

  Any help would be much appreciated

---

### Post by Penguenci on 2013-07-07
The latter does sound like a hardware (including hardware compatibility) problem indeed. The former, however, could happen merely by installing GRUB on the Linux partition itself instead of the MBR. For the MBR issue, the fantabulous Boot Repair CD should suffice to make you a happy person again :-)

Another thing you need to bear in mind is that, you're using a branded laptop, and those happen to have very specific settings for certain things to keep them "original". Especially Toshiba and HP have been known to overdo that kind of stuff. The problem could be as simple as that, in which case you'd need support from Toshiba unless you can figure out how the specific configuration works and why it's causing the issue.

---

### Post by qed1999 on 2013-07-08
> **Penguenci said:**
> The latter does sound like a hardware (including hardware compatibility) problem indeed. The former, however, could happen merely by installing GRUB on the Linux partition itself instead of the MBR. For the MBR issue, the fantabulous Boot Repair CD should suffice to make you a happy person again :-)

Another thing you need to bear in mind is that, you're using a branded laptop, and those happen to have very specific settings for certain things to keep them "original". Especially Toshiba and HP have been known to overdo that kind of stuff. The problem could be as simple as that, in which case you'd need support from Toshiba unless you can figure out how the specific configuration works and why it's causing the issue.

Thank you for the answer

As I said I can not enter the Ubuntu desktop environment. Can I bypass the bluetooth somehow on startup and enter the desktop environment?
Bluetooth is not so important to me at this point anyway.

To use the Boot repair cd and the Boot repair Tool and install grub on Linux partition I need to enter the desktop environment.
Can I do it directly by using the command line interface? How?

---

