---
title: "Used wrong hardware drivers how do I fix it?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by lawentzel on 2008-03-24
Installed the wrong drivers for a wireless network card.  How do I find what was selected, tell it to forget it, and then re-detect the device?  I know in a Windows environment I would go to Device Manager, pull the device and reboot.  Is there something similar that I am just missing?  Thanks!

---

### Post by Sam Lars on 2008-03-24
What device was this?

---

### Post by lawentzel on 2008-03-25
The drivers that got loaded are the Broad Corporation - BCM4306 802.11b/g Wireless LAN Controller.

The driver works but VERY VERY slowly.  If it matters this is on a Dell laptop and is a mini PCI wireless card originally from a Compaq.

Attached is the Advanced tab in Device Manager.

---

### Post by Sam Lars on 2008-03-25
Ah, yes, I have the same card.
Did you install the drivers through the Restricted Drivers manager?  You should be able to uncheck the box if that is the case.

---

### Post by lawentzel on 2008-03-26
That uninstalled it perfectly.  Is there a better driver that is going to run faster?  Or is that pretty much it?

---

### Post by Sam Lars on 2008-03-26
You could try installing ndisgtk, and using it in System > Administration > Windows Wireless Drivers to add the .inf file from the drivers [here]("ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe").

---

