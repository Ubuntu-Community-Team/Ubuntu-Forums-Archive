---
title: "Ubuntu 10.10 Fresh install not working"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by mymrhelpdesk on 2010-12-25
Hi all I have a 

System Information
Motherboard : Gigabyte GA-965G-DS3 
Hard drive : WD SATA 250GB
Memory : 6GB
Processor : Q6600 Quad Core 
Nvidia 9600 Video Card
SATA DVD Writer


I have booted from dvd rom system boots fine i'm booting a 10.10 DVD iso, I have had exact same result from Desktop Edition.

System boots fine but at installation won't see my sata harddrive to configure loader. I have chosen quit and gone to system and gparted and os see's drive. but will not let me install 10.10 to it drive is blank, no partitions at all I have also tried creating a partition but installer still won't see sda to continue installation. I'm giving up wow and dropping my windows environments for ubuntu any help would be appreciated.

P.S. i have gone in bios and tried enabeling acpi and sata native mode as well no help.

I'd appreciate any solutions that can be offered.

---

### Post by garvinrick4 on 2010-12-25
Before installing with CD or Usb try this at terminal:
```
sudo apt-get remove dmraid
```Works sometimes in this situation.

---

