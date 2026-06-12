---
title: "[SOLVED] Trouble installing to SD card on Asus eee PC 901"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by nfraser on 2008-07-26
Hi

Apologies that my first post is a query rather than a solution!

I have just managed to get of an eee PC 901. I was after the Linux version but they have been delayed so I veered towards the dark side and bought thew Windows XP version. Of course I also bought an 8GB SD card at eh same time to install Ubuntu 8.04 onto and thiss is where I'm having trouble...

I used the 8.04 Alternate CD and booted it using my external USB DVD-Writer. All went well and I chose to install the boot loader on the MBR of the SD card.

The reason I did this is that I want the eee to boot into XP by default when my wife is using it. But I want to be able to press Esc during the POST to allow me to boot off the SD card instead when I need to.

I don't want to install GRUB into the MBR of the first SSD - in fact I don't want to install GRUB at all if necessary - but I presume I need some form of bootloader?

Anyway - to the problem!

It works so far in that I can boot the XP partition by simply turning on the eee. I can press Esc during the POST and coos to boot from the SD card and this brings up GRUB with the detected menu items. However none of the menu options actually work - all give an Error 17.

I have checked that the correct hdx is being used (hd2,0 in this case) but no joy. I can't think of anything that I can do yto solve this.

Does thte fact that I have used Ext2 rather than Ext3 for the partitions make a difference?

TIA

Neil

---

### Post by pcjason on 2008-07-26
I'm not sure if it will fix your problem, but on my EeePC 900, I had to change grub to use hd0, instead of hd2, to be able to boot off of the SD card.  I know it is strange, but that is the only way that I could get things to boot.  I suggest you play with the hdX number and see if it helps.  It certainly couldn't hurt at this point!

---

### Post by nfraser on 2008-07-26
Thanks - will try it now...

---

### Post by nfraser on 2008-07-26
pcjason - many thanks - changing the hard disk so hd0,0 has worked. Not sure why - presumably the BIOS enumerates the drives differently when I instruct it to boot from the sd drive???

Thanks again

Neil

---

