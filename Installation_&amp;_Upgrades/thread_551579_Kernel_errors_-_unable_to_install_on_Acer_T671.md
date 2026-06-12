---
title: "Kernel errors - unable to install on Acer T671"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by genbie on 2007-09-15
Hi,

Anyone got the Acer T671 working with Ubuntu please? I get the following message when trying to install Ubuntu:

[B]PCI: cannot allocate resource region 1 of device 0000:00:14.0
[/B]
and then the installation freezes! I tried to have APIC Mode disabled in Bios but then when I try to install, I get the following error:

[B]Kernel panic - not syncing: Attempted to kill init!
[/B]
********

Another Ubuntu CD gives me the following error:

[B]pcie_portdrv_probe ->Dev [7936:1002] has invalid IRQ. Check vendor BIOS.
assign_interrupt_mode Found MSI capability
isapnp: Scanning for PnP cards ...  [/B] (and then it freezes for ever!)


********

Any help is greatly appreciated!

---

### Post by Pumalite on 2007-09-15
Have you tried the Alternate CD?. How much memory do you have, what graphics? 
256 MB RAM>Xubuntu Alternate cd.

---

### Post by Pumalite on 2007-09-15
The Aspire T671 is designed from the bottom up to offer a competitive richly featured Vista Home Premium solution. Supporting CPUs from Intel Celeron up to Intel Core 2 Duo processors combined with an industry leading standard of integrated graphics as well as dual channel memory support, the T671 is a Premium winner.

The integrated graphics is probably your problem.

---

### Post by genbie on 2007-09-15
Hi,

Thanks for the reply. I think that the Acer T671 will work with Linux. See this link which confirms it. 

[http://www.linpus.com/xampp/webmaster/Certification/LL93/LL93Cert_Acer_Aspire.html](http://www.linpus.com/xampp/webmaster/Certification/LL93/LL93Cert_Acer_Aspire.html)

I  have 1 GB Ram and yes it has integrated graphics (ATI Radeon XPress X1250). The motherboard is MRS00M and the bios is Phoenix award  workstation v6.00PG

Any help anyone please? This is quite urgent! Many thanks.

---

### Post by Pumalite on 2007-09-15
With an ATI Radeon, your best bet is the Alternate CD.

---

### Post by genbie on 2007-09-15
Thanks for the quick reply. It also has Intel pentium 915 D, so should I get the ubuntu-7.04-alternate-amd64.iso installer?

---

### Post by Pumalite on 2007-09-15
More packages and less problems with the 32bit

---

### Post by genbie on 2007-09-17
Thanks Pumalite! You're a star! I am writing this from my new Acer computer ;-)

---

### Post by Pumalite on 2007-09-17
You are most welcomed. Glad you have it working. May the Ubuntu be with you!

---

