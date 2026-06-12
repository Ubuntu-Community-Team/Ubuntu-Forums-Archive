---
title: "Karmic will NOT install with AMD/ATI HD2600 card."
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-03
Anyone else with this issue - I had to remove the card to get anything past the new monochrome Ubuntu logo.

I reformatted and reinstalled and tried via USB and everything, but in the end I had to pull the card and go "native SVGA".  This is a 2.94 Ghz Celeron with the ATI/AMD Radeon 2600XT AGP8X card (This card is still supported by ATI) and it's Mfg. is: "ati2mag_RV630,PCI\VEN_1002&DEV_9586"

I will reinstall and see if I ca nget the new Cadalyst release for this card as found here: [http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzUxNA)

---

### Post by emarkay on 2009-10-04
Updated and rebooted, then installed the card.  Same thing!

Tried F4 "Safe Graphics Mode", "vga=771" and "xforcevesa" in trying to get the Desktop up to install and by installing alone. 

It's not the card, for Window$ works fine.

It's not the disc, for I also tried to install via USB (the disc is goodtoo, for it loads on my other PC; that's where I got the USB Karmic image)

Still, nothing past the logo.  With 2 different monitors. Of course with the card in, I can't use the onboard SVGA, so I am stuck.

Surely someone has ideas????  Debugging, grabbing of logs, test routines, anything???

---

### Post by emarkay on 2009-10-04
To make it clear, this is a completely new ext-4 install; reformatted and all.

ALSO there is NO "XFIX" option in the "Recovery" mode.

---

### Post by emarkay on 2009-10-04
MAybe something to do with this?

[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126)

I don't think so, but???

---

### Post by screaminj3sus on 2009-10-04
I am using a mobility hd2600 and it installs fine...

And that GDM bug you posted, I did experience but it has been fixed for a while.

---

### Post by PGHammer on 2009-10-04
> **screaminj3sus said:**
> I am using a mobility hd2600 and it installs fine...

And that GDM bug you posted, I did experience but it has been fixed for a while.

If you had the proprietary drivers installed and then did a kernel update, you will need to reinstall the proprietary drivers after.

I had an issue after doing a kernel update (from 31.10 to 31.11) with my HD3450 due to this; however, a reinstall of the proprietary drivers fixed the woes.  (Also, for the first time ever, I have not just compositing available in KDE, but I got the cube back.)

This is in Kubuntu Karmic beta 1 (current version).

---

### Post by emarkay on 2009-10-05
This is a desktop, not a laptop.  The whole point is that I cannot even get past Grub, then the Ubuntu logo - there is nothing beyond that!  So how can I install anything; is there a commandline way to install the drivers?????

I gave up after about 8 hours on this - am I really going to have to wait till the RC comes out to test Karmic?

---

### Post by moviemaniac on 2009-10-05
> **emarkay said:**
> is there a commandline way to install the drivers?????

sudo apt-get install xorg-driver-fglrx

I've got the same card as you (well, same chipset...) and I also had to install the proprietary drivers manually but that was due to a (since then fixed) GDM bug.

Maybe you're encountering another bug. When your system boots up, try to switch to tty7 by pressing "ctrl+alt+F7" when the screen goes blank.

---

### Post by emarkay on 2009-10-05
Success - "wutwutwut" suggested messing around with the "AGP aperture"...

I had it at 128.  Less did not work, but 512 and 256 did!

Strange!

THANKS!

---

