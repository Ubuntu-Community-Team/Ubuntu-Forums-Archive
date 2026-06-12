---
title: "Unable to boot after upgrade"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by sgoodall on 2007-04-21
After upgrading to feisty, I am unable to boot into the 2.6.20-15-generic kernel.  It is unable to find my harddisk and just hangs at bootup at the "waiting for root file system" point and eventually dumps out into the initramfs console.

The root disk on on a PCI IDE raid card using the IT8212 chipset, but used in IDE mode.
Previously this device was reported as /dev/hde.
I also have another hard disk on the primary IDE channel (hda), and a cdrom drive on the secondary IDE (hdd) channel.
Now I only have a /dev/sda drive (which appears to be the disk that was hda).

When booting up  in recovery  mode, I see that following messages;

scsi4 : ata_piix
ATA: abnormal status 0x7F on port 0x0001ec07
scsi5 : ata_piix
ATA: abnormal status 0x7F on port 0x0001e407

I can boot up in the old 2.6.17-11-generic kernel that was already on the system and this gives me back my old devices. However, there are no ATI drivers in the feisty repos for this kernel.

The main difference seems to be the move from the it821x kernel module in the 2.6.17 kernel to the pata_it821x driver in the 2.6.20 kernel. Is there anyway to fall back to this driver in 2.6.20?

---

### Post by FeraTech on 2007-04-21
Same thing for me, I'm just stuck at the boot screen.

I'm was running Edgy on a Laptop. Turion ML 30 with Radeon 200m.

---

### Post by katanacb on 2007-04-23
I have a very similar problem on Feisty 64-bit.

I ran Feisty through several of the betas, and they all ran just fine.   However, I noticed that during one of the last mass-updates (i.e., within the last week or so before Feisty was released) that my it8212 raid card just kinda 'stopped working' ... meaning that I could no longer see any of the drives attached to this card.  Poking around I noticed that some of the things mentioned above were true ... namely that the it821x module was gone from the kernel modules directory, and the pata_it821x module was being used in its place.  But, something's wrong with this driver it seems, because it doesn't recognize any of the drives attached to the raid card, whereas the 'old' driver did.

Something else to note is that boot-up takes AGES now, I get 'failed to ident' messages during boot when the pata_it821x module is loaded, and several-minute pauses during bootup (presumably waiting for something to time out).  I've looked around on launchpad and it looks like some bugs similar to this have been filed but they are marked as 'low' on the priority.

This is a showstopper for me re: feisty, and it's a regression (since things worked fine through the betas and on edgy, etc).  Guess I'll either have to recompile the kernel until the devs decide to release an updated patch that has the old module in it, or go back to an older version of Ubuntu.

---

### Post by cet.junior on 2007-04-23
Same problem too...waiting for solution... :(

I don't want to reinstall... :(

---

### Post by ronmonki on 2007-04-23
This problem is back for me too, just did a clean install of fiesty and now my IT8212 raid card is not showing, I can remember the old days of breezy I think, when i had to recompile the kernel to get this working, what a shame to regress to the old bug.....

anyone remember how to manually install this module???

---

### Post by Horatio on 2007-07-19
I'm trying Kubuntu after I have been using Gentoo for years. I wanted some thing more easy to fix.
 
 The kernel is 2.6.20-16-generic, and the driver pata_it821x is shown in the output.
 
 Is there a standard amd64 linux kernel with the it821x module available in any repository, or how does this new module work
 
 p.s. All worked well with Gentoo's kernel, and I was thinking I could use that one.

---

