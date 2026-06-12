---
title: "4 gig ram in 7.04"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by travisch on 2007-04-23
How do I get 7.04 to see 4 gig ram in 7.04 (32 bit)?

---

### Post by pking on 2007-08-28
Don't know if this will help anyone but I had tons of trouble getting the 32 bit version of Feisty to see all my 4 gigs of ram(forget about the 64 bit edition folks! It can't even recognize my network card!!).

After tons of research here's what worked for me:

1- Default install of Feisty 32 bit desktop edition

2- Blacklisted the "intel_agp" in /dev/modprobe.d/blacklist because I got a PCI express card and otherwise  wouldn't boot.

3- Installed the "server" version of the kernel from Synaptic

4- Reboot

5- Done!

Of course for those who have an Asus P5B-E like me have to enable the "memory remapping" of the north bridge or else you'll only see 3 gigs of ram.

Hope that will help a few.

pking

---

