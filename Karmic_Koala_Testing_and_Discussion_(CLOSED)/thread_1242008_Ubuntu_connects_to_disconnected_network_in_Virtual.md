---
title: "Ubuntu connects to disconnected network in VirtualBox"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-16
VirtualBox OSE - Jaunty host - Karmic Guest

Has anyone noticed this? Ubuntu as guest can access the network even though VirtualBox says it's disconnected. This doesn't happen with all the Windows guests.

I couldn't see anything on Launchpad, although it was only a brief look as I'm tired and need sleep.

---

### Post by vishalrao on 2009-08-16
I couldn't find anything/ any bug on this either. I get this problem too (but only occasionally) with VBox 3.0.4 on Arch Linux host with Karmic guest :) I was testing the "installer delay at 82%" issue... I did notice though that if you enable/disable the network multiple times finally ending up unchecking the adapter then it does in fact get disabled, so I'm thinking its more of a vbox issue?

---

### Post by psyke83 on 2009-08-16
> **phenest said:**
> VirtualBox OSE - Jaunty host - Karmic Guest

Has anyone noticed this? Ubuntu as guest can access the network even though VirtualBox says it's disconnected. This doesn't happen with all the Windows guests.

I couldn't see anything on Launchpad, although it was only a brief look as I'm tired and need sleep.

Maybe try upstream instead: [http://www.virtualbox.org/wiki/Bugtracker](http://www.virtualbox.org/wiki/Bugtracker)

---

