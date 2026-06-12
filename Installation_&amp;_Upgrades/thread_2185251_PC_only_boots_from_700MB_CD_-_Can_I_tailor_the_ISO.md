---
title: "PC only boots from 700MB CD - Can I tailor the ISO down to 700MB?"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by Jon02794 on 2013-11-01
Can I reduce the Saucy ISO to 700MB?      My PC will not boot from USB DVD or USB stick  and CDROM drive is limited to 700MB CDR.

---

### Post by Bashing-om on 2013-11-01
Jon02794; Hi ! Welcome to the forum.
No can reduce the size of the desktop (or any online .iso file) with out really getting down to the guts and gore level.

A better option might be to use the alternate or minimal edition, both will fit onto a CD.
Also Lubuntu will fit on a CD (at least 13.04 did ).
Admittedly a fair amount of familiarity with 'buntu to effect an alternate install would be helpful, It is not that difficult, and we can help you over the rough spots.

[INDENT][INDENT]hey, it's a thought
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2013-11-01
Does your computer have a USB port?  If so, a USB install may be easier.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by drs305 on 2013-11-01
Jon02794,

I see you joined the Ubuntu forums last year. Do you happen to have Grub 2 on your computer for booting purposes?

If so, you can download the ISO file directly to your hard drive, boot it from Grub 2 and then install or try it without using a CD/DVD/thumb drive.

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

---

### Post by fantab on 2013-11-01
> **Jon02794 said:**
> Can I reduce the Saucy ISO to 700MB?      My PC will not boot from USB DVD or USB stick  and CDROM drive is limited to 700MB CDR.

> **drs305 said:**
> Jon02794,

I see you joined the Ubuntu forums last year. Do you happen to have Grub 2 on your computer for booting purposes?

If so, you can download the ISO file directly to your hard drive, boot it from Grub 2 and then install or try it without using a CD/DVD/thumb drive.

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

If you don't have any Linux with Grub2 on your PC then Install Lubuntu from CD and follow drs305's suggestion if you insist on having Ubuntu. Once Ubuntu is installed and running you can remove Lubuntu, if you don't want it.

@drs305: glad to see you.

---

### Post by Dennis N on 2013-11-02
**Still another way**:

For PCs that will not boot from a USB device, this may work (I have only used it once and it did work):

Download iso of plop bootloader, burn it to a CD.
Download iso of Ubuntu OS, create a USB installer.
Boot plop bootloader from CD drive.
Plug in USB installer.
Select USB boot from Plop menu.
USB should boot.
Carry out normal installation.

[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

use the download link, download [B]plpbt-5.0.14.zip
[/B]
The iso you burn is inside.

---

### Post by mikewhatever on 2013-11-02
How about using Xubuntu 12.04? It's not the latest, and definitely not the prettiest, but older PCs that can only boot from CDROM will actually appriciate it.
Xubuntu 12.04 is supported for 3 years till April 2015, and does fit on CD.
[http://old-releases.ubuntu.com/releases/xubuntu/releases/precise/release/xubuntu-12.04.1-desktop-i386.iso](http://old-releases.ubuntu.com/releases/xubuntu/releases/precise/release/xubuntu-12.04.1-desktop-i386.iso)

Of cause, you can also remaster an Ubuntu ISO:
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

