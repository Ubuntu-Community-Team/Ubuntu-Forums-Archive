---
title: "Xubuntu 7.04 (Feisty) installation on TP 390E hangs (often)"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by fiestaforever on 2007-05-03
After installing Xubuntu 7.04 on a Thinkpad 600E (succesfully, except for sound), I wanted to install it with the alternate install CD (text-based installer) on a [Thinkpad 390E]("http://www.thinkwiki.org/wiki/Category:390E") (PII-333, 192 MB). 

This laptop is connected to a DSL modem via an IBM "10/100 EtherJet PC Card CardBus Adapter" (= rebranded Xircom PC Card) with no other network connetion.

When trying to install it from the CD without additional boot options, it hangs at the "Detecting network hardware" stage with a blank screen. 

When booting with the options I used for the other Thinkpad (acpi=force pci=noacpi pnpbios=off pci=usepirqmask), it hangs at the DHCP configuration screen. When I remove the PC card, I get an error message, but I can continue with the installation. 

But it stalls again at "Installing the base system - 95% - Installing extra packages - retrieving and installing acpi...". No way to go from there.

Any ideas? 

TIA
Alex

---

### Post by grumpymole on 2007-05-04
Alex,

I have one with a Xircom card and if I use "pnpbios=off acpi=off" that gets my card working.

The sound is a classic problem, but is [solveable]("http://grumpymole.blogspot.com/2006/10/thinkpad-600e-sound-problem-still-not.html").  More detail is in the bug report mentioned in the post.

Regards

---

