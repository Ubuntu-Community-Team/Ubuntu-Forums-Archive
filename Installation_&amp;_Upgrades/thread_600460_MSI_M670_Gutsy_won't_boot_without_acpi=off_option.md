---
title: "MSI M670 Gutsy won't boot without acpi=off option"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by patreides on 2007-11-02
Hi,

I'm the happy owner of a MSI M670 laptop (sempron 1.8 MHz). It worked just fine with Feisty Fawn (7.04). Unfortunately, since I upgraded to Gutsy Gibbon (7.10), my laptop don't boot without acpi=off boot option.

No ACPI with a laptop causes different issues : no power management, no automatic shutdown...

I've tried many boot options (noapic, nolapic, pci=noacpi, acpi=force, irqpoll, pci=nomsi etc.) but without success.

I've also updated my bios with the firmware from MSI. But it don't solve my problem...

May any Linux Gurus on Ubuntu forum help me ?

Thanks in advance...

---

### Post by patreides on 2007-11-03
Hi,

I've found an approximate solution to my problem with these boot options :

noapic nosmp nomce

With these parameters, Gutsy does boot and functions without any problem... but no hibernate nor sleep possible : just black screen and hang !

So it's a partial solution to a real regression from Feisty Fawn !!!

---

### Post by espi3d on 2008-01-06
I have the same MSI M670 and therefore the same problem you have. Did you solve it yet? How?
Or we have to wait for hardy release?

---

