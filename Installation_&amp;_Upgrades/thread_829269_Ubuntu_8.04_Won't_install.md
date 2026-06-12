---
title: "Ubuntu 8.04 Won't install"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by Bloodember on 2008-06-14
HI guys,
I've looked all over the forums for an answer and I can't find one so I'll just ask it. When trying to install ubuntu 8.04 on my main computer and the installer just won't work. It just goes to a command line then gives me all these errors after sitting a few minutes. I got it to install on my old laptop with no problems. My specs are as follows:

Intel Core 2 Duo E6600
2GB ram
Audigy 2 platinum sound
Nvidia 8800GT video card

I have a LG DVD writer, 250GB, and 2 500GB HDD drives on SATA, the HDD drives are Seagate

My mouse and keyboard are on usb, they are: keyboard- Merc Stealth, mouse- Microsoft Sidewinder

last is a Dell 22in LCD widescreen monitor (don't think you needed this, but just in case)

I want to install on the second of the two 500GB drives, which I bought just for Linux.

thanks

p.s. I'm also having the same issue with Linux Mint 5

---

### Post by avtolle on 2008-06-14
I believe one problem is related to the SATA drives (from memory, reading other threads on the Forum). IIRC, some people have had success with booting the CD, pressing F6, then adding "all-generic-ide" (without the quotation marks, of course) to the boot line there, then continuing on. Try this and see if it gets you a bit further along.

---

### Post by Pumalite on 2008-06-14
Make sure is not a bad burn. Do md5sum, burn at 4x or less as an image.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Bloodember on 2008-06-14
I know it's not a bad burn, I installed it on my laptop a few hours ago, works just fine. 

I'll try out some of the suggestion I got here and a few I found elsewhere later, right now I'm downloading a few other distros to try out and see what I want to use.

thanks

---

### Post by alexbishops on 2008-07-26
This is what I did to get it working on my PC:

I booted from an Ubuntu 8.04.1 CD and did the following:
pressed F6 and added the following parameteres after --
all_generic_ide floppy=off irqpoll pci=nomsi

---

### Post by Gr0leau on 2008-08-26
> **alexbishops said:**
> This is what I did to get it working on my PC:

I booted from an Ubuntu 8.04.1 CD and did the following:
pressed F6 and added the following parameteres after --
all_generic_ide floppy=off irqpoll pci=nomsi

This worked like a charm!!!!

---

