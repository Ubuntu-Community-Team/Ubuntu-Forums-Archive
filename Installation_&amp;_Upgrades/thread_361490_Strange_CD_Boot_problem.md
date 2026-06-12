---
title: "Strange CD Boot problem"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by Brismetal on 2007-02-14
Hi

I've searched the forum.  I don't have a Core Duo 2 board or one of the controllers giving problems but I am recieving the "hda: cdrom_pc_intr: the drive appears confused (ireason =0x01)" errors while trying to boot from the CD then the boot stalls and keeps repeating that message before "detect soft lockup" and the system locks up.  I don't get into X

I managed to get around it by disableing two of my IDE HDD's (I have 2 IDE and 2 SATA) but leaving the DVD-RW and DVDRom (both IDE) running.  It installed and ran fine.

I installed Ubuntu on the second SATA drive.

When I try to boot into it with all drives active I get errors again..  When I have them disabled it boots fine (or seems to)

I have a MSI MS-6728

Do I need to post more info?  Does anyone have any ideas?

I think I might purchase a PCI IDE card and try running my other IDE drives off them.

---

### Post by Kateikyoushi on 2007-02-14
I would say your Ide controller is not supported. Check out the launchpad whether someone filed a bug for it already.

---

### Post by Brismetal on 2007-02-14
Yeah, I thought that but my DVD drives are IDE also.  It seems to be only half of the IDE controller that is causing the problems which kind of leads me to think it's not the IDE controller..  There should be any problems installing/running it with 4 hdd's and 2 dvd drives plugged in should there?

---

