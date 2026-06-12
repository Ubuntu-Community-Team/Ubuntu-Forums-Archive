---
title: "Notebook with only one PC slot, without CD, floppy or net card"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by viktorh on 2007-03-08
My notebook (Toshiba Portégé 3500) crashed during Ubuntu installation. Now GRUB has the "Error 17", so all data incl. Win XP partition are unaccessible. I have no MBR backup, the notebook is little "used", so:

- orig. network card don't work, PC Card network card must be used
- Boot is possible from PC Card only
- is one PCMCIA only
- no CD drive available
- Wireless network is not accessible
- PC card with Hard-disk boot image don't find (resp., don't search) the USB slots (where is a USB memory with installation CD copy, both as files and ISO image)

Question: 
Is it possible to create new MBR from PC Card only (256 MB max.), for at least Win will be work?
Exists any way how to say to Ubuntu network boot image to new scanning of PCMCIA slots for new network card?

Thaks you for your help.

---

### Post by teaker1s on 2007-03-09
if you can get  "fdisk" onto a bootable device you can "fixmbr" with it or use an external usb cd or dvd rom drive and there should be usb boot option in bios if the laptop isn't too old

---

### Post by viktorh on 2007-03-09
Unfortunately, the boot from USB is impossible. The only PCMCIA can be used for boot.

---

### Post by viktorh on 2007-03-10
I have found the "Feisty"alpha installation ISO, so I booted notebook with "Feisty" CD-ROM boot image and then install the "Feisty".

---

### Post by teaker1s on 2007-03-11
excellent, maybe you would consider adding your experience to the wiki?

---

### Post by awm34 on 2007-03-15
I also have the ISO image (and a means of transferring it to my ancient laptop).

My question is:  how did you manage to boot from the ISO?

Thanks!
Alan Messer

---

