---
title: "Create Network Repo Mirror Using Alternate CD"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by firefly2442 on 2008-07-30
Hello all.

I'm trying to install Ubuntu on my new Asus eee PC.  Since it doesn't have a hard drive I've been trying both USB and network installs.  The USB drive worked fine except I want the alternate CD for HD encryption and wasn't able to mount the USB drive and make it think it was the CDROM.  Anyway, I tried a network install and so far it's been flawless.  I got tftp and dhcp setup and have been able to successfully boot my machine.  The part where I'm getting stuck is specifying the network repository.  Since I don't have internet access I would like to copy the packages from my alternate CD to apache to do the network install.  I tried this but didn't have any luck.  I also tried apt-mirror but that didn't seem to work either.  Shouldn't I just be able to copy the entire directory from the CD to my apache server and point to that?  

Thanks in advance for the help. :)

---

### Post by firefly2442 on 2008-07-30
Hmm, well it seems that the ethernet driver doesn't seem to be supported.  I guess I could try adding the driver in but maybe I'll just give the regular desktop version a shot through USB.  I guess I could always add in additional packages later.

---

