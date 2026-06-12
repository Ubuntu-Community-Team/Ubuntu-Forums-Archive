---
title: "Continuous Harddrive Activity"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Zelandeth on 2008-05-12
Okay, upgraded to Hardy, and despite a few niggles, have got everything back up and going again to full strength - even though my login screen is still a strange size - I'm happy to fight with that later though.

What is however driving me around the bend is the fact that CONTINUALLY ever since the install, the harddrive has sat churning away.  The pattern of activity sounds almost like Windows defragmenting a drive, which made me think of the indexing thingie (excuse the highly technical term), but I've unchecked the boxes for both indexing and watching - and it's still going.

If it were just cataloging the drive, I've really have expected it to have finished by now - unless of course it restarts every time the system does, in which case if I leave it alone for a good while is it likely to finish and not do it again?  It must have had a good 15-20 hours of running time over the last few days now.

To be honest, it's driving me around the bend...which is a shame as everything else seems to be working fine!

---

### Post by Rallg on 2008-05-12
I recall that for a short time during beta test, some installations (including mine) did that. It was some sort of problem with a hardware driver, fixed in a later beta version. It was not the indexer.

You didn't say how or when you upgraded. Before trying anything else, boot to recovery mode, and do

sudo apt-get update && sudo apt-get upgrade.

You might have to do dist-upgrade instead of upgrade.

Then re-boot normally. Problem solved? If not, re-boot normally but when you login, choose the "Gnome fail-safe" option, which does not load all drivers. Did that help?

If the problem persists, get back here with a description of your hardware, so that others with the same hardware can comment.

---

### Post by Zelandeth on 2008-05-13
Cheers for that.  I'll give your suggestion a shot and see what happens.

Upgraded last weekend from within the update manager.

For reference, the hardware it's running on in no particular order:

> Gigabyte GA-M52S-S3P
(Which has built in sound and networking - all of which seem to be working)
> AMD Athlon 64 X2 5000+
> 2Gb DDR2 800 memory.
> GeForce 8500GT 512Mb PCI-e.
> Hitachi DeskStar 750Gb SATA-II Harddrive.
> Hitachi DeskStar 60Gb Harddrive in a USB2.0 enclosure, which Ubuntu is running from at the moment - Installing the PATA-SATA convertor I'd need to run this drive internally causes Windows to lock up on startup - hence it being run externally - Having only just got Windows back up and running properly, I'm not reinstalling again!
> Belkin PCI 802.11g wireless card which I can't remember the model of to save my life.  Ubuntu's detecting it as an RaLink RT2561/RT61 802.11g PCI card.

Aside from that, just your garden variety CD-RW, DVD-ROM and 3.5" floppy drives to contend with.

EDIT: Just tried that - still the same.

Further thoughts?  One thing that springs to mind is that this disc thrashing starts before I've even logged in, so it's not something that Gnome is starting up when I log in.

---

### Post by Zelandeth on 2008-05-15
Eventually it drove me around the bend, so I gave in and burned a CD, and did a clean install.

Installer didn't even glitch on me once, sailed straight through, and is now working perfectly.  Should have just done that to start with!

---

