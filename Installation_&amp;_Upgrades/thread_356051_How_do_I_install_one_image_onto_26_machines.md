---
title: "How do I install one image onto 26 machines?"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by Chado on 2007-02-08
I'm working on a project at school with Xubuntu for my programming teacher. We just got new computers and he wants the image I created on them. However, he doesn't want to do it until I can install it over the network like Norton Ghost Multicast. He is kind of picky on difficulty so I was wondering if there is a straight forward easy way of broadcasting the one image I made to all 25 machines in the room at once or even if it was just a few at a time. Any help is appreciated. (Note: All drives have Windows on them already)

---

### Post by aysiu on 2007-02-08
PartImage?
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by Snowbat on 2007-02-08
PXE install?
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)

---

### Post by Chado on 2007-02-08
Getting warmer...
PartImage doesn't get it onto other machines from one machine.
PXE looks do-able but like a nightmare.
Thanks

---

### Post by Snowbat on 2007-02-08
Are you wanting to install regular Xubuntu, a custom Xubuntu, or a clone of an existing partition?

Ghost for Unix (G4U) is a suggested open source alternative for Norton Ghost but I don't know if it has the features you need.
[http://www.osalt.com/g4u](http://www.osalt.com/g4u)

For regular Xubuntu, what I would do in this situation is set up a machine on the LAN as an ftp server, make the full installer available via ftp, and then use mini.iso (an 8MB bootable image for ftp/network installs) on a few CDRs or USB keys to boot the clients and install via ftp.
[http://www.faqs.org/docs/Linux-HOWTO/Network-Install-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Network-Install-HOWTO.html)

---

### Post by Chado on 2007-02-08
Snowbat that is exactly what I'm looking for. I'll report back and let you know how it goes. Thank you so much. I was worried that my project was for nothing.

---

