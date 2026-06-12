---
title: "Can't boot from CD, how to inbstall?"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by leebrown66 on 2007-06-26
Hi All,

I have a PP-166/256M ram, 2x4G SCSI drives, 1xCDROM.  I want to install Ubuntu onto one of the HD's, but this machine won't boot from CD (not supported in BIOS) and the floppy disk controller on the motherboard doesn't work (so no sbm.bin option).

I burned a CD from the ubuntu-7.04-desktop-i386.iso image and can manually run the setup.exe (that the autorun points at) that is on there, but it doesn't give me an option to install, just try out some applications.

Any clues here?

Thanks,
Lee

---

### Post by Pumalite on 2007-06-26
Update your BIOS. Even then, Ubuntu 7.04 CD won't install from low memorey. Your best bet after you fix your BIOS is to try 'Alternate Xubuntu CD'.

---

### Post by az on 2007-06-26
> **leebrown66 said:**
> Hi All,

I have a PP-166/256M ram, 2x4G SCSI drives, 1xCDROM.  I want to install Ubuntu onto one of the HD's, but this machine won't boot from CD (not supported in BIOS) and the floppy disk controller on the motherboard doesn't work (so no sbm.bin option).

I burned a CD from the ubuntu-7.04-desktop-i386.iso image and can manually run the setup.exe (that the autorun points at) that is on there, but it doesn't give me an option to install, just try out some applications.

Any clues here?

Thanks,
Lee

You really need to boot the cd.  Can you remove the drive and install on another box?

---

### Post by leebrown66 on 2007-06-26
> **Pumalite said:**
> Update your BIOS. Even then, Ubuntu 7.04 CD won't install from low memorey. Your best bet after you fix your BIOS is to try 'Alternate Xubuntu CD'.

Unfortunately flashing the BIOS is a dangerous option.  In the event the flash doesn't take (this is a DEC machine with a proprietary motherboard, possibly with a proprietary BIOS) I would have to use a floppy to recover and .... the motherboard floppy controller is dead... So if I get the wrong upgrade or it doesn't work for some reason, the motherboard is completely trashed...

---

### Post by leebrown66 on 2007-06-26
> **az said:**
> You really need to boot the cd.  Can you remove the drive and install on another box?

he heh.  I'm trying to do this in the hopes of installing Ubuntu on a HD to put into *another* machine!!

Hmmmm......

---

### Post by leebrown66 on 2007-06-27
> **Pumalite said:**
> Update your BIOS. Even then, Ubuntu 7.04 CD won't install from low memorey. Your best bet after you fix your BIOS is to try 'Alternate Xubuntu CD'.

Definately not an option.  It is at the latest release .. and it's a custom BIOS for DEC --> Compaq --> HP, so I'm not risking the generic BIOS from Phoenix.

---

### Post by Pumalite on 2007-06-27
Get yourself ( borrow ) a USB CD-ROM. Try that, see what happens.

---

