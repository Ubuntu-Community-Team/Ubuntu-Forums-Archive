---
title: "ubuntu 14.04 bootable USB &gt; login loop"
date: 2014-12-17
forum: Installation &amp; Upgrades
---

### Post by PsYcHoTiC_MaDmAn on 2014-12-17
have tried to install ubuntu onto my new ssd a couple of times now, used different USB sticks, different ports, re-downloaded the ISO to make sure its not something odd there.

basically, I choose the USB stick, get to the option screen for try ubuntu without installing (need to play about with gparted to setup my install), gets to login screen (for which: Ubuntu; blank; is the correct response) at which point it repeatedly loads the login screen (but so quickly you cant do anything)

I run ubuntu 12/04 on my old SSD with no issues, but as I have a larger SSD, I wanted to do clean install of 14.04

as one bit of checking, I was able to boot the USB on my laptop.

so this leads me to believe its hardware based, but dont want to start pulling things out my system as a number components are watercooled.

system is: i5 3570k, Asus P8Z77-v LX, 12GB (2*4GB + 2*2GB) RAM, Samsung 250GB 840 Evo, AMD R9 290, AMD HD 6450 (second card is for a separate display (VGA only) and two cards was the only way to get both screens working in both OS's without switching cables continuously)

graphics looks like the likely issue to me, however as I said, the items are water cooled so bit awkward to remove.

---

### Post by sudodus on 2014-12-17
I agree that the cooperation between the graphics driver and the graphics chips is suspected.

If the computer works well with 12.04 LTS, I suggest that you stay with that version. It is well polished and debugged, and will receive support until April 2017 (at least standard Ubuntu and Kubuntu).

---

