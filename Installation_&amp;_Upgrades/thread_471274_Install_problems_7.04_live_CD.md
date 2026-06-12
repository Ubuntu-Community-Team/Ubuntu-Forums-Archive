---
title: "Install problems 7.04 live CD"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by NCAANFI on 2007-06-11
Hi I'm trying to do a clean install on a PC I just built

Specs
CPU: AMD X2 3600+
Mobo: Asus M2n8 vmx
Video: ECS 256 nvdia 7300gt
Wireless card: Asus WL138G
LG SATA Dual layer burner
WD SATA 250gig HDD
Ram 1 gig

I boot up using the burned  ISO CD. I get to the menu asking me what I'd like to do. I select option 1 but the following errors come up

18.239616 MP-Bios bug 8234 timer not connected to io apic
18.418467 Kernel Panc - not syncing 10 apic +timer doesn't work boot wth apic = debugand send report. 

Err I really don't know what that means and what I have to do to remedy this. 

Thanks for any help or suggestions.

---

### Post by merlinus on 2007-06-11
IIRC, press F6 at the startup screen and add noapic to the boot parameters.  Or try F2.

hth...

-merlin

---

