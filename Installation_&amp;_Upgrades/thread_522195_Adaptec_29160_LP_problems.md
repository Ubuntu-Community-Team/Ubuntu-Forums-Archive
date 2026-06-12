---
title: "Adaptec 29160 LP problems"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by Nicolas_x on 2007-08-10
Hello,

I do encounter problems when trying to install ubuntu on my new pc.

I keep receiving messages "domain validation failure" with my adaptec 29160LP card.

This card works prefectly under windows XP and was working with my old pc and unbuntu.



Any suggestion ??

---

### Post by PaulFr on 2007-08-11
Ultra 160 has a feature called "domain validation" which checks bus integrity during initialization. If that is giving failure, perhaps your cabling or drive is having problems, please post relevant section of dmesg output.

---

### Post by Nicolas_x on 2007-08-12
I've checked the most relevant information from the kernel.log

parity error detected in data-in phase. SEQADDR(0x1e7) SCSIRATE(0x80)

Ubuntu is trying to communicate at different speed but none is ok.

I'm sure that my card, cabling and hard disk are fine because this is the drive i'm using for my windows..

I've also checked in the card bios  andeverything is ok.

Sorry for not beeing able to paste to full kernel log here but I've also a problem with my realtek ethernet controler and so no internet from ubuntu :(

If I take the card, cabling and hard disk and plug it into my old PC everything is ok.... 

One way to be explored. This is a PCI X card plugged into a PCI slot (so 64 bit into a 32 bit slot). Maybe that it can helps finding a solution..

---

