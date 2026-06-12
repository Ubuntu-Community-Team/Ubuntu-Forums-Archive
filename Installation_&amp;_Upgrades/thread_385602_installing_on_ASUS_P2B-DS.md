---
title: "installing on ASUS P2B-DS"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by reckless2k2 on 2007-03-15
I'm having a great deal of problems trying to install Ubuntu 6.06 or 6.10 on an ASUS P2B-DS. It hangs right off the bat because of the onboard SCSI. I'm using IDE and not SCSI but the hardware detection picks up the SCSI and read around a little about problems in many OS's regarding this board. Is there any way to tell it not to try to detect the SCSI or not let it allow the aicxxx driver that hangs?

---

### Post by mykeszone on 2007-03-30
You may have to disable the adaptec SCSI controller in the BIOS and make sure the boot sequence has IDE near the top of the list. Also have the BIOS auto-detect your hard drive. That motherboard [I'm using one right now] only supports 33UDMA standard. Have your hard drive set to MASTER and not CABLE SELECT. Make sure it's on the first IDE channel.

I'm using a Promise 133ATA controller on mine for faster hard drives but have SCSI at the top of the boot list because most OS's view the controller as an add in card so it must be SCSI. I don't know why, just what I've found.

While you're messing around in the BIOS you could also try changing the "Plug and Play OS" option from yes to no or visa versa. If the board revision isn't 1.05 or 1.06 it won't turn off properly or go into stand-by or sleep mode. You'll have to turn it off by pressing the power button and disabling the power saving features in the OS. If you have a revision 1.04 or earlier board and are good with a soldering iron Google P2B-DS modification guide or P2B APCI [ACPI] resistor mod for some trick moves on that board.

Cheers

---

### Post by reckless2k2 on 2007-05-02
I still can't get this thing to boot. Now I'm getting a PnPBIOS error when i try to start using the Xubuntu alternate install disc. If i try to boot using an IDE hard drive with Ubuntu already installed , I get a grub error. 

Could you please tell me and or PM me your BIOS settings? I'm sure it's something in there that needs to be tweaked.

---

