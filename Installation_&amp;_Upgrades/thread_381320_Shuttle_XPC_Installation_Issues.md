---
title: "Shuttle XPC Installation Issues"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by pmgeahan on 2007-03-10
Folks - 

Just picked myself up a new Shuttle XPC box.  Nice. machine.  Most of the hardware is onboard.  

Problem:  Ubuntu does not like either the network adapter or the SATA controller.  Sort of makes it hard to install an O/S.  The machine came preinstalled with Vista, so I know the hardware functions.

The hardware is all SiS onboard stuff.  lspci identifies:

```

Host bridge: SiS unknown device 0662
PCI bridge: SiS AGP port
ISA bridge: SiS Unknown device 0966(rev 59)
IDE interface: SiS 5513 [IDE]
Ethernet controller: SiS Unknown device 0190
IDE interface: SiS Unknown device 1183


```

The module for the sis190 ethernet controller installs fine, and actually recognizes the interface.  However, it won't pass or accept traffic.  Even when set with a static IP it does nothing(and the switch lights don't blink).  I checked with a known-good cable, as well.

The hard drives are more perplexing, as I can always slap a cheap ethernet card in to get networking.  Dmesg shows the following:

```

SIS5513: IDE controller at PCI slot 0000:00:02.5
SIS5513: chipset revision 1
SIS5513: not 100% native mode: will probe irqs later
SIS5513: probe of 0000:00:02.5 failed with error 01

```

This is with an Ubuntu install LiveCD for Edgy.

Does anyone have any pointers for me?  I've yet to have an Ubuntu install fail on me and I'd hate to start now.  

Thanks!

---

### Post by nitsnipe on 2007-04-15
****, i got exactly the same problem.   It did not work with either Edgy or Feisty.

I can't even get the PC to recognize the network adapter.

---

