---
title: "Can't install 11.04 on SSD using SATA3 Marvell chipset"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by wesg on 2011-07-10
When I first built my workstation, I installed Windows 7 and 11.04 on my SSD, using the SATA2 headers on my ASUS motherboard. When the SSD broke, I replaced it with an SSD that I connected to the SATA3, and that seems to have presented a problem.

First I selected the installation from the GRUB menu, and that resulted in nothing. I booted from the install USB stick to try to repair, or even find, the installation, but no dice. Does Ubuntu have a beef with SATA3 headers, or the Marvell chipset, on my board? 

ASUS P6X59D Premium

---

### Post by psusi on 2011-07-10
It shouldn't.  You will need to provide some more details for help though.

---

### Post by wesg on 2011-07-10
What sort of information might be helpful?

GRUB says there are two installations, but can't boot Ubuntu. 

How can I repair GRUB with the live disk?

---

### Post by psusi on 2011-07-10
Like what exactly happens when you do try to boot.  "It doesn't work" is not an error description.

---

### Post by wesg on 2011-07-23
By "doesn't work" I mean the Ubuntu installer can't detect my SATA3 SSD, so there's no where to install. My system has a 500GB WD Blue on SATA2, and a 120GB Intel 510 using SATA3 for booting Windows. I'm actually running a live disk of Ubuntu 10.10 now, and the installer could not detect the SSD. I thought maybe it was because booting from a USB drive would disrupt the drive arrangement, but booting from the CD doesn't work to install either.

---

### Post by sk3499 on 2011-07-23
> **wesg said:**
> By "doesn't work" I mean the Ubuntu installer can't detect my SATA3 SSD, so there's no where to install. My system has a 500GB WD Blue on SATA2, and a 120GB Intel 510 using SATA3 for booting Windows. I'm actually running a live disk of Ubuntu 10.10 now, and the installer could not detect the SSD. I thought maybe it was because booting from a USB drive would disrupt the drive arrangement, but booting from the CD doesn't work to install either.

Did you try booting the CD drive from UEFI using the boot menu? Note that UEFI has to be enabled in the BIOS and supported by your mobo.

---

### Post by Quackers on 2011-07-24
Unless things have been updated lately Ubuntu did not suppoprt the Marvell controller for SATA 3.

---

### Post by olel on 2011-07-24
SATA 3 isn't supported yet. I had to switch my SATA cable over to a SATA 2 port in order to install Ubuntu.

It kinda sucks, so I'm hoping to see SATA 3 supported soon!

---

### Post by wesg on 2011-07-25
Thanks for the replies, everyone. Now the question is if I have to wait for 11.10 in the fall for SATA3 support...

---

### Post by psusi on 2011-07-25
> **olel said:**
> SATA 3 isn't supported yet. I had to switch my SATA cable over to a SATA 2 port in order to install Ubuntu.

It kinda sucks, so I'm hoping to see SATA 3 supported soon!

It is on standard AHCI controllers.  The only difference it makes is that instead of flipping on the bit to select 1st or 2nd generation signaling, you flip the bit for 3rd generation.

---

