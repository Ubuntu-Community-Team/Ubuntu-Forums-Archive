---
title: "Disable network interfaces on boot?"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by ph8 on 2007-05-31
Hi all,

On my newly built system I can only boot to 'recovery mode' - at the moment my theory is that this is due to a problem with the network interfaces (which are disabled by default in recovery?) - is there a way to stop network interfaces being probed/configured by adding options to the standard (non-recovery) kernel in grub?

Thanks,

ph8

P.S. I'm using an Abit IN9 32X-Max with on board ethernet, lspci recognises the following:

Bridge: nvidia Corp. MCP55 Ethernet (rev a2) [Two of these]
Ethernet Controller: Atheros Communications INc. Unknown Device 001c (rev 01)

---

### Post by ratman99uk on 2007-05-31
Since you are only trying to work out what the problem is. Can you not simply disable the network cards in the BIOS. This would be much faster and easyer to achieve.

- Ratman99UK

---

