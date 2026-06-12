---
title: "2nd phase, the text goes nuts."
date: 2004-11-26
forum: Installation &amp; Upgrades
---

### Post by norwyn on 2004-11-26
Hi. I tried to install Ubuntu tonight, but in the second phase of the install (the first reboot) GRUB loads, and the installation starts and then, I can´t read the text. It looks a little bit like the matrixcode, exept it´s not green  :D .

Anybody knows whats wrong?
Yesterday i encountered the same problem, so I don´t think reinstalling it will be to any help.  

Some specs: IDE, three partions; first ext2 active and also root. 
                     second swap. then I got WinXP on the third partion. 
                     And yes, GRUB doesn´t recognise windows.

Thanx.

---

### Post by wallijonn on 2004-11-26
What type of video card do you have? mDid you turn off video-caching, video-shaowing & bios-caching and bios-showing in the BIOS? How much memory on the moemory card? what is the agp size in BIOS?

---

### Post by norwyn on 2004-11-26
Somekind of Geforce 2 card.  64 mb agp bios. 64 mb memory on the videocard.  Yes, I had thoose turned off. The text go weird directly when it starts to load the kernel.
Thanks by the way.

---

### Post by norwyn on 2004-11-27
Nobody knows what to do? I´ve experienced the same trouble with Mandrake.
Cheers.

---

### Post by wallijonn on 2004-11-27
norwyn,

If you are having the same problem with Mandrake then chances are that it may be hardware related. I have to ask if you have a sound card or NIC sharing an IRQ with the video card?; (usually the first slot next to the agp card will share IRQs).

Part of your troubleshooting process would be to either remove the sound card or NIC, or turning off sound and / or NIC in the BIOS (if those devices are built-in onto the mobo). I believe the kernel should try to install vga:vesa drivers when it starts to install. When you use the custom or expert install mode, is there an option to enable vesa?

---

### Post by norwyn on 2004-11-29
It didn´t work out.  I tried the Live CD again to look over the installation files, but then in GRUB (using the Live CD) the text changed again.

---

