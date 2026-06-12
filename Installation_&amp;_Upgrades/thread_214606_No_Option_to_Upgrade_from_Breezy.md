---
title: "No Option to Upgrade from Breezy"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by billinja on 2006-07-12
I really hope this is a newbie problem, but my Desktop computer was running Breezy, and upgraded with no (yes, that's Zero) problems to the new Dapper version.

My laptop on the other hand, I installed with Breezy with the intention of just using the upgrade option in the "Software Updates" program.  Unfortunately, instead of the "upgrade" button I get a pop-up that says:

"There is a new release of Ubuntu available!" - and then it proceeds to tell me to go to [www.ubuntulinux.org](www.ubuntulinux.org) for upgrade instructions.  Suffice it to say there are no upgrade instructions on the main page, and upon searching I have found nothing in the way of actual upgrade instrctions (besides download the ISO and burn it to CD).  I would prefer to do the upgrade the same way as I did for my desktop.  

Is this possible or was I just lucky with my other computer?

Thanks for reading, and hope to hear back soon!

---

### Post by fredinator on 2006-07-12
Edit your /etc/apt/sources.list with ```
sudo gedit /etc/apt/sources.list
``` and change all the places that it says "breezy" to "dapper". Then run ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` when this has finished restart and voila you now have dapper

---

### Post by billinja on 2006-07-12
Excellent!  Thank you so much.  I knew it was a newbie thing!

---

### Post by billinja on 2006-07-12
> **billinja said:**
> Excellent!  Thank you so much.  I knew it was a newbie thing!

In response to my own problem, I decided it would most likely be easier (after all this) to do a full install.  Seeing as my laptop has no floppy and no cdrom (yes.. sad isn't it?) - I ended up setting up DHCP/PXE-TFTPD and am doing a network install.

I found this website that walked me through both configuring DHCP and configuring a PXE Boot server:

[http://myy.helia.fi/~karte/ubuntu_pxe.html](http://myy.helia.fi/~karte/ubuntu_pxe.html)

Props to site author on this one!

---

