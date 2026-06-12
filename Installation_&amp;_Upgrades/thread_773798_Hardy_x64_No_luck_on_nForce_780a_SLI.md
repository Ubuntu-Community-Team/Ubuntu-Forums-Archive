---
title: "Hardy x64: No luck on nForce 780a SLI"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by silanea on 2008-04-29
Hallo!

Hardy x64 won't install on my new rig. Specs:
[LIST]
[*]CPU: AMD Phenom X4 9850
[*]Board: ASUS M3N-HT deluxe (chipset: nForce 780a SLI)
[*]VGA: Gainward BLISS GeForce 8800 GT, PCI-E (2x, running as SLI combo)
[*]HDD: Seagate Barracuda ES.2 500GB (S-ATA)
[*]Optical drive: LG somethingorother (S-ATA)
[/LIST]

I first tried the x64 RC cd, then the x64 release alternate cd.

Besides the still occuring USB reset bug (keyboard is reset about every second, already did so with any previous Ubuntu install CD but funnily enough never in the installed system) I am experiencing problems with the S-ATA drives:

[LIST=1]
[*]Loading the installation after the CD's bootscreen takes forever. During this time I get messages about "ata100 qc timeout" claiming that a device "failed to identify". At some point the setup screen appears.
[*]My S-ATA disc drive is not recognized (despite my having just booted from it :confused:). There is just one module offered to load (cdrom) which apparently does not solve the problem. I plugged in an older LG IDE drive and then got to my final point of defeat:
[*]My S-ATA hdd is not recognized. The installer claims there was no hdd and offers me to load modules none of which seems to work.
[/LIST]

I am not new to installing Ubuntu - or Linux in general for that matter - but I am at a loss as to how to deal with these problems. Under Windows I simply slipstreamed the nVidia drivers into the installation and was more or less fine (despite being unable to install onto a raid array using the onboard controller, something I will have to take care of later on).

[COLOR="Red"]But how do I provide additional drivers to a linux installation? Floppy discs are out of the question since I could not find any working drive.[/COLOR] I do however have a USB card reader with a 4GB microdrive that is recognized as bootable device by the mainboard. I already tried to simply copy the install cd onto the microdrive and install from there, apparently I'd still have to setup a proper boot sector on the md since all I got was a blinking cursor.

So my question is: [COLOR="Red"]How can I integrate the nVidia driver into the install cd?[/COLOR] Or is there another way to get around this problem?

[edit] I already have a working Windows XP on the disc with EXT3 driver so I could create partitions for the install to read and drop stuff there if that's of any help.

[edit 2] I was rather sure nVidia provided some linux drivers for parts of the chipset but that turned out to be a mistake on my part.  So what options am I actually left with?

Thanks alot,

Flo

---

### Post by markusr on 2008-07-13
I've solved most of your issues with M3N-HT DELUXE but there are plenty of them left :(

I managed to get ubuntu 8.04 to work in IDE and AHCI mode.

its possible to do that by giving boot parameters

first thing i tried was to remove "quiet splash" and replace it with "all_ide_generic" that did work but this only fixes the harddisk-issue

second possibility (using this now) is to replace "quiet splash" with "pci=nomsi" 
your harddisk should work fine now in any controller mode (havent tried raid yet)
and it makes network work at the same time

but I am still trying to fix sound - so I hope anyone has got some tips for me

---

