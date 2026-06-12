---
title: "Networking problem in Ubuntu 8.10 (did not exist in 8.04)"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by BYOCOM on 2008-11-12
I've got a PC with an Asus A8N-SLI Deluxe motherboard (we'll call it PC A) and another with an Asus A8N-SLI (non-deluxe) motherboard (let's call him PC B).

PC A has been running Ubuntu 8.04 since release day with no problems.  8.04 has been run on PC B from time to time as well also without problems.

Before installing 8.10, I removed the hard drive and replaced it with another (just in case something went wrong so I could quickly revert to my working system).

I did a fresh install of 8.10 on PC A using the new hard drive and it does not receive an IP address.  I tried both of the on-board NICs and received the same problem.  I booted the 8.10 live CD and get the same behavior.  I run the disc verification on the live CD and it comes back fine.  I re-download the 8.10 ISO and burn another copy just in case.  I get the same behavior with this new CD.

On PC B, I use a PCI NIC instead of the onboard NIC (the non-deluxe model has only 1 onboard NIC).  I boot PC B from the 8.10 live CD. When connected to the onboard NIC, I observe the same behavior as on PC A, when connected to the PCI NIC it works!
I tried both NICs on PC B a few times and observed the same behavior:  onboard nForce4 NIC does not work, PCI NIC does work.

So it looks like there is an incompatibility of some sort which is new with 8.10 (8.04 worked like a champ).  Any ideas on how to fix this?

---

