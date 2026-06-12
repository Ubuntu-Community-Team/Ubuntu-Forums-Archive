---
title: "Installation without a CD"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by iakudi on 2005-03-09
hi,

I was wondering if anyone can help me, I have an old laptop and a xircom 10/100 PCMCIA LAN card, I want to install Ubuntu on this (I have tried to understand the Debian Woody stuff but it's too technical and i got lost very quickly), so I can give it to my nephew to use for his homework - a nice (and cheap) change from Mr Gates.

I have access to a broadband connection.

My simplistic view is, can I make a bootable floppy that I can use to start up the laptop, install a minimal kernel (is this correct to say??) and then download/install over the internet?

As my previous posts have shown I'm not the most technically gifted person with Linux,  in fact I will be honest - i'm plain cr@p !!

All help will be most welcome.

Ismail


I also face a bigger challenge, I have another very old laptop with a CD drive only, the bios only allows me to boot from rthe HD or a floppy and it does not have any USB either....BUT this is for another day I guess.

---

### Post by bodyhead on 2005-04-07
I also would like to see a minimal boot floppy that I could use to install over the internet.  If anyone has any information involving this... Please instruct.

Thanks

---

### Post by Leif on 2005-04-07
I don't think there's an ubuntu install floppy, but you can do it by installing debian from floppy first :

[http://www.debian.org/distrib/floppyinst](http://www.debian.org/distrib/floppyinst)

[http://linux.simple.be/debian/floppy](http://linux.simple.be/debian/floppy)

Once that's done, change your sources and you've got ubuntu.

---

### Post by bodyhead on 2005-04-11
[QUOTE=Leif]I don't think there's an ubuntu install floppy, but you can do it by installing debian from floppy first :

[http://www.debian.org/distrib/floppyinst](http://www.debian.org/distrib/floppyinst)

[http://linux.simple.be/debian/floppy](http://linux.simple.be/debian/floppy)

Once that's done, change your sources and you've got ubuntu.[/QUOTE]

Change my sources then update?  or would the dist-upgrade command work? like going from warty to hoary?

---

### Post by Leif on 2005-04-12
You definitely need to change your sources, then update, then dist-upgrade.

---

### Post by bodyhead on 2005-04-19
Here is what I've done and the system is very unsatisfactory.  I installed a base Debian system from the floppies across the Internet.  Then I changed the sources in sources.list to hoary.  Then I did a dist-upgrade.  Now I have a system that will not shut down.  It just runs through some things stopping and starting then returns me to the login prompt.

There are also some other small problems.

---

