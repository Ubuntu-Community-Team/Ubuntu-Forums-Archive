---
title: "Ubuntu just won't install"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by dryder on 2007-01-30
Hi - newbie here,

I downloaded ubuntu-6.10-desktop-i386 - the md5Sum matched OK.

But when I try to boot using the CD I get "Unknown keyword in config file" before ubuntu gives me the menu - and from there, whatever I do (except Check Memory) it just hangs with the line going back and forth .... 

The ISO image was burned correctly (and verified).

Can anybody please give me some help?

My native system is M$ XP SP2, NTFS, plenty of disk space but at the moment if I could just get to boot using the CD ...  

Many thanks,

David

---

### Post by meng on 2007-01-30
I've not seen this problem before (perhaps someone else has) but I would try downloading and installing from the Alternate CD if you're having problems with the Desktop/Live CD.

---

### Post by dryder on 2007-01-30
Thanks meng - but what is the "Alternate CD"?

I get my downloads from my ISP's "Free downloads" - that is they don't use up my monthly GB allowance so I am not familiar with other download sites for Ubuntu.

Many thanks,
David

---

### Post by rsambuca on 2007-01-31
What are your system specs?  Sometimes you will need to add in some different boot options depending on your hardware.

---

### Post by meng on 2007-01-31
ubuntu-6.10-alternate-i386.iso

You can find it at [www.ubuntu.com](www.ubuntu.com)

---

### Post by dryder on 2007-01-31
> **rsambuca said:**
> What are your system specs?  Sometimes you will need to add in some different boot options depending on your hardware.

Hi rsambuca,

P4 200 GHz
768MB RAM
2 x 232 ULTRA ATA HDDs
2 x 112GB IDE HDDs
BENQ DVD-ROM
CORDLESS (M$) KEYBOARD/MOUSE - USB
OKIDATA P/L PRINTER
EPSON 1270 USB PRINTER
EPSON R210 USB PRINTER
MICROTEK 5000 USB SCANNER
ONBOARD REALTEK RTL8139 PCI ETHERNET
ONBOARD NVIDIA GEOFORCE MX400 GRAPHICS
8 USB PORTS

Many thanks for your help,
David

---

### Post by rsambuca on 2007-01-31
After you get the initial start-upscreen, press F6 and try entering some of these boot options before the "--" and leave a space between each option and the last --

ide=nodma (try this one by itself first)

irqpoll pci=noacpi noapic nolapic acpi=off (just stick all of these in at once and see what happens when you boot, if that doesn't work, try different combos of them, sorry)

---

