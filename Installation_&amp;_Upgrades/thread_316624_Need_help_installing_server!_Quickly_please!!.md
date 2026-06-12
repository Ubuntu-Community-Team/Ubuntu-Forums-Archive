---
title: "Need help installing server! Quickly please!!"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by tokkosta on 2006-12-11
Ok im trying to install Ubuntu 6.06 server for a EM64T rack server machine and having some problems.

Specs: 

Specs:
Brand new HP proliant DL320 G5 Server
-Intel Celeron D 352 3.20GHz (EMT64T)
-Memory:512mb
-2x 80gb hot swap hard drives
-writing dvd optical drive.
-Embedded Sata raid 0,1 support

I downloaded the 6.06 server EM64t Alternative verison and checked hash which matched. Then i burned it on a DVD(Also tried CD) using 1-4x speed.


I stated by enabling Embedded Sata raid support from the "bios" or Rom Based Setup Utility as it is called on my server. Then i went on the create the hard-drive array. This is what i did:

Created an array with my 2 harddrives and set them on raid1 and used "clear"(this deletes all existing data on the drives) method to install raid 1, i also set write cache on and set the array as bootable. Then i put my boot order (IPL) to number1 boot= harddrive number2= CD-rom

computer rebooted and went on to the ubuntu install prompt. I selected install server. I goes into the blue screen installation process and i select language and location but after ive selected my location it goes wrong. The screen turns blue with a grey bar on the bottom into which i can write stuff but nothing happens. I just stays in this mode forever.

Ive tried adding "irqpoll pci=noacpi noapic nolapic acpi=off" to the boot but didnt help.


Should i download another version of Ubuntu? Like 6.06 Intel version? Or is there something wrong with the way i set up my drives or have i just missed something?

Please help its urgent.

Thanks

---

### Post by linuchsan on 2006-12-11
Have you tried it with Edgy (6.10)?

---

### Post by tokkosta on 2006-12-11
Yeah just did and it worked :D Thanks anyway!

---

