---
title: "Installing gaming gpu in to server"
date: 2014-12-25
forum: Installation &amp; Upgrades
---

### Post by ads2996 on 2014-12-25
Hi, i own a rackmount server that i got for free, i then got a msi r9 280 for christmas with the intention of adding it to the server and play games. I have installed the card, but i get no image over the dvi port. I have supplied the card with power but just cant get it to work. The server is a hp dl385 g2. Thanks for any help in the matter.

---

### Post by MAFoElffen on 2014-12-26
So... You have which GenII DL385 rackmount? There were 3 configurations of that Genration. Each had differing slots. Ensure that you have a PCI-Express 8 card in a matching slot. There were also PCI-X and PCI-Express 4x slots in those servers, based on what config they were. There was a later PCI/ Express x16 riser card that was an option, but that was not standard yet. (I have an HP DL380 GenII)

If Linux does not see the card on the bus, then it may be that the card is not in a compatable slot.

I would say first to hook to a monitor on both the vga and the GPU card... so you can get graphics and use lspci and lshw to see if Linux sees the card on the bus. If so, then you may or may not have to go into the BIOS to disable the onboard VGA as the primary graphics. (Most likely not) If it sees the monitor that is attached (looking at the xorg.0.log, then since that card is high end Radeon, you will initially have to start it using "radeon.modeset=0" added into the grub/Linux boot line to turn off KMS until you get the right Radeon driver installed. Otherwise, it will not have grahics/ will be a blackscreen.

---

### Post by ads2996 on 2014-12-27
> **MAFoElffen said:**
> So... You have which GenII DL385 rackmount? There were 3 configurations of that Genration. Each had differing slots. Ensure that you have a PCI-Express 8 card in a matching slot. There were also PCI-X and PCI-Express 4x slots in those servers, based on what config they were. There was a later PCI/ Express x16 riser card that was an option, but that was not standard yet. (I have an HP DL380 GenII)

If Linux does not see the card on the bus, then it may be that the card is not in a compatable slot.

I would say first to hook to a monitor on both the vga and the GPU card... so you can get graphics and use lspci and lshw to see if Linux sees the card on the bus. If so, then you may or may not have to go into the BIOS to disable the onboard VGA as the primary graphics. (Most likely not) If it sees the monitor that is attached (looking at the xorg.0.log, then since that card is high end Radeon, you will initially have to start it using "radeon.modeset=0" added into the grub/Linux boot line to turn off KMS until you get the right Radeon driver installed. Otherwise, it will not have grahics/ will be a blackscreen.

Hi thx for the reply the probelm was the server wouldnt even post never mind be able to get into an os. So have given up on using the server, one of my friends will hopefully be able to get me an old hp workstaion with two dual core xeons at 2ghz wiht the pci express connector and allow me then to play my games. The server does have the riser card with the x16 pci express and x8 electricly. I think the probelm may have been a compatabiity error.

---

