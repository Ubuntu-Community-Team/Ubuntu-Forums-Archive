---
title: "Ubuntu install issues with intel maxtrix raid"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by wildstars on 2010-01-06
This issue is with Ubuntu 9.10. The system is home build pc with vista 64 on one drive, attempting to install ubuntu on a different drive. All the vista applications and data are on 4 other drives configured as raid 0+1 using the motherboards onboard intel matrix raid.

I'm new to ubuntu (and linux for home use in general) and decided to do a dualboot ubuntu install on my primary vista pc, using a separate 80 gb drive.

I downloaded and ran wubi, and then things went down hill rapidly. I can't seem to find anything in the forums that covers what I'm experiencing.

First and foremost, ubuntu destroys half of my motherboards intel matrix raid. Every single time. Its a total mystery to me as to why it does this because a) it is being installed to a totally different non-raid drive on a totally different sata controller, and b) ubuntu blanks my screeen out as it commits this dastardly deed.

Secondly, when its destroys the raid, it re-arranges the logical arangement of the drives, which I think screws up a boot configuration for grub (what was sda2 is now sda3, etc). When I pick ubuntu as a boot option it puts me in a cli grub environment with about a dozen commands.

It would have been nice if there was some sort of warning about intel matrix raids somewhere on the install instructions pages and the wubi install pages. Its only costing me about 8 hours to rebuild my raid each time, but it could totally hose somebody running raid 0,5, or 10.

Anyways, does anybody know if using the alternate install method will prevent ubuntu from wrecking my raid? Don't get me wrong, I'm doing my dead level best to be civil about it, but I'm really very unhappy about losing the use of my main PC for 16 hours total now.

---

### Post by wildstars on 2010-01-09
Some research indicates that this is due to a bug in grub2. There is a document on how to install using the alternate install CD that says it might take care of the issue, but the instructions reference 9.04. I attempted an install and followed the instructions using 9.10 with no success.

Something that is extremely interesting about this is that it wrecks the matrix raid even when it supposedly has not written anything. At one point I chose the 'verify install media option' and rebooted after successful verification. I didn't pick anything that should be invasive. On reboot, half my raid was wrecked.

I'm going to go look to see if there are any known issues with linux and my gigabyte ex58 ud5 motherboard. 

Any help would be appreciated.

---

