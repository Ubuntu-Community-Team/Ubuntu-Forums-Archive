---
title: "Grub Rescue"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by henrik5 on 2014-04-17
Hi, I'm trying to reinstall Ubuntu on my server, So what I have done is i took the disc out and formated it and put it back in. 
But whan I try to boot it with an ubuntu boot usb i get this anoying grun rescue, and cant boot from the usb. Does anyone have any idea of what I should do?
Everything has been going perfect until now..

---

### Post by grahammechanical on 2014-04-17
What you have done is removed Ubuntu by doing that re-format but Grub is still installed into the MBR and it cannot find its configuration files or a Linux image to load. The problem is the failure to boot from the USB memory stick. Have you set the USB port to have boot priority over the hard disk? It seems to me that the BIOS is still looking first for an OS on the hard disk. It finds the Grub boot loader and runs that. You need to point the BIOS to look for an OS first on a USB port and then on to the hard disk.

Regards.

---

### Post by henrik5 on 2014-04-17
Problem is: When i go into BIOS it doesn't find the usb on the boot list, but i can boot from it in an other option.. But when I try so it says I have to take out the boot device and try again.. Whan I do so it goes to grub rescue[COLOR=#000000]. So what do I do..?[/COLOR]

---

