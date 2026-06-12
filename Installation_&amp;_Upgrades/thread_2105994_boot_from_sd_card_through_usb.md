---
title: "boot from sd card through usb?"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by mIRChele on 2013-01-17
i have a live version of ubuntu installed on my sd card. unfortunately my notebook can't boot directly from sd card, but I want to use it anyway. Is there a way to boot from sd card using a launcher (or something like that) from a usb drive? how can i do that?
i want something that redirects  you directly to the operating system in the sd card, like in the old times when computers didn't support boot from cd and you had to use a floppy to launch the installation from cd-rom.

---

### Post by dabl on 2013-01-17
I would suppose a USB card reader would allow booting the card (but fair warning, I haven't tried it myself).  They're not expensive.  Here's the type of product I'm talking about:  [http://www.sandisk.com/products/memory-cards/readers/imagemate-all-in-one-usb-30/](http://www.sandisk.com/products/memory-cards/readers/imagemate-all-in-one-usb-30/)

---

### Post by irv on 2013-01-17
I happen to have one, but it's at home and I am not. When I get home I can see if it will boot from a sdcard. I know it plugs into the usb port and I know I can boot from a usb so it should work. I need to pickup a couple of sdcard today anyway, so I will try it and then repost here.

---

### Post by mcduck on 2013-01-17
> **dabl said:**
> I would suppose a USB card reader would allow booting the card (but fair warning, I haven't tried it myself).  They're not expensive.  Here's the type of product I'm talking about:  [http://www.sandisk.com/products/memory-cards/readers/imagemate-all-in-one-usb-30/](http://www.sandisk.com/products/memory-cards/readers/imagemate-all-in-one-usb-30/)

I agree, that would e the easiest solution. And as long as the computer is able to boot from USB drives, it shouldn't have any troubles booting from SD card reader either.

...the one thing to be careful with is the type of the reader, some multi-card readers expose each card slot as a separate device, and some computers can only boot from the first device. However in most cases even a multi-card reader has worked just fine for me.

---

### Post by dabl on 2013-01-17
I have an Imagemate that is a few years old, but I don't have an SDHC card with an OS installed on it, to boot.  I guess I could turn unetbootin loose on it and see what happens.  More later ....

---

### Post by dabl on 2013-01-17
And the answer is ...

YES.  I just booted Bodhi Linux on a SDHC card in a Sandisk Imagemate 5 in 1 reader, on a Dell Latitude E6500.  So, it works.

---

### Post by ajgreeny on 2013-01-17
I installed Ubuntu 10.04 onto my wife's netbook using an SD card from my camera in a cheap card reader with no problem at all.  The system sees it as a USB drive whatever it is.

The same card in the integrated SD card reader of the netbook would not boot; it needed to be attached by USB.

---

### Post by efflandt on 2013-01-18
The card slot in most laptops is /dev/mmcblk0 (1st partition is /dev/mmcblk0p1) which BIOS usually does not offer any choice to boot from.  The only computer I know of that can boot from an SD card as /dev/mmcblk0 is a raspberrypi, which is the only thing it can initially boot from (it cannot boot directly to USB).

But I know that a normal computer, that can boot from USB, can boot from SD or microSD in a card reader.

My tablet PC (Acer W500P) is able to boot Linux from its internal SD card slot, but that slot is internally USB connected as /dev/sdb.  And even my old desktop PC from 2004 can boot from SD in its built-in card reader, which is internally USB connected.

---

