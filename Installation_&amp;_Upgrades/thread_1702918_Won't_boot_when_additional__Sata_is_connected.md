---
title: "Won't boot when additional  Sata is connected"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by Simon Hansen on 2011-03-08
I am a relative newbie to Linux but I am not dumb. I have been reading blogs and notes for 3 days now and nowhere is there a clear solution to my problem. I have tried with both Desktop and server and the problem is as follows:

1. I install Desktop 10.4 or server 10.10 on my 250GB IDE drive using guided partition structure. 

2. I add SATA Drives (of varying types and sizes to test) to the system and create a raid.

3. When I restart grub won't initialize with the SATA's plugged in.

4. I have tried this in various ways, installing with the SATAs already connected, making the raid in the install process etc. 

I have tried re-installing formatting the drives in windows, deleting partitions, making new ones, low level formatting. It appears to be related to an issue with GRUB re-ordering drives so it is trying to boot off the wrong drive - I would edit grub but it doesn't get that far into the boot. Just rudely flashes it''s cursor at me. Is this really so uncommon that there isn't a straight simple answer?  

What makes me think it has to do with partitions and formatting is that when I first added new drives they worked on the boot. I even made the raid in Desktop mode in Server - Rebooted- Rude flashing cursor.

Please could someone point me in the right direction as I am wasting so much precious' time for something relatively basic.

Thanks!

---

### Post by Hedgehog1 on 2011-03-09
> **Simon Hansen said:**
> 

1. I install Desktop 10.4 or server 10.10 on my 250GB IDE drive using guided partition structure. 

2. I add SATA Drives (of varying types and sizes to test) to the system and create a raid.

It appears to be related to an issue with GRUB re-ordering drives so it is trying to boot off the wrong drive

Simon,

I fear you will need to write this up as "It's a Unix/Linux" thing.

Don't mix IDE and SATA drives like this.  It never really works.

Please go all SATA - _**OR**_ - move all the SATA drives to a single real hardware RAID controller that always boots after the IDE drive.  Make sure that RAID card has Linux drivers!

I don't know of any better solution.

***The Hedge***

---

### Post by Simon Hansen on 2011-03-09
Thanks for the quick response Hedge.

I am a little shocked by your advice though. I can't mix SATA and IDE without a controller? Most of what I am using UBUNTU for is old machines which have 2 of each. It's the perfect place for file servers and a linux development zone (I thought).

If that really is the answer and I have been wasting time trying thanks for ending the pain - but please confirm that mixing SATA and IDE doesn't work on 10.10. Our oldest server running UBUNTU 6.X or something ,mixes the two.

Simon

---

### Post by gradinaruvasile on 2011-03-09
May be a BIOS issue (i never worked with RAID on Ubuntu but i had plenty of issues caused by altered boot order when i had multiple drives in my comp). 

Did you check the boot order after adding the SATA (or any new) drives?

Also BIOSes  seems to favor IDE drives in the boot order.

---

### Post by Simon Hansen on 2011-03-09
Thanks gradinaruvasile,

I seem to have fixed it... Holding thumbs. I tried two things. 

1. Flashed my bios with latest. (It's an old machine)
2. Changed the boot order to SATA. (When I actually have UBUNTU on my IDE)

This worked on UBUNTU desktop. Then I switched IDE drives to my UBUNTU server IDE drive. It didn't work. However when I switched the Bios boot order again back to IDE it worked again on the SERVER IDE Drive. I am testing now.

Thanks for the tip.

Simon

---

### Post by Hedgehog1 on 2011-03-09
Simon,
 
The advice to use all SATA **_OR_** use SATA via a hardware RAID card if you use IDE is based on long term reliability.
 
Anytime any 'little' change will risk the system not booting correctly, you are inviting more pain later. Typically late at night during the worst possible moment. *Ask me how I know.*
 
A RAID card will run from a driver loaded from the IDE drive. This means the SATA drives become avaiable in a known sequence. It also means improved performance, as most RAID cards have memory cache and intellegent controllers.
 
You have it working for now, and that is great.
 
I hope it stays up for you. But if not, we are here to help...
 
***The Hedge***
 
***:KS***

---

### Post by Simon Hansen on 2011-03-09
Thanks Hedge,

From what I have read the drive order was a problem when the /dev/hd0 system is used to initiate devices. UUID was supposed to solve this? There is a UUID address in my grub.

It wasn't working on my setup but is that because of hardware or bios or something? You are wise - if it is erratic it will be painful in the future but surely there are ways to force the boot to a particular device. Is that the problem here? Is it a grub issue (software) or a physical drive issue? I just wan;t to understand so I can orient myself around the risks

Thanks guys you input is invaluable.

Simon

---

### Post by tallthom on 2011-03-10
Simon and Hedge,

I'm experiencing the same kind of symptoms on my old Pentium III machine.  I've got sda as an IDE HDD.  Also, sdb and sdc are two S-ATA drives attached to a Sil PCI RAID card.

I was able to install 10.10 server configuring LVM using the IDE drive with /boot, /, and swap in one VG.  Then I lumped the two S-ATA drives for /var into a second VG.  No boot.  Doesn't even hit the GRUB menu.

Unplug the S-ATA drives and the system makes the grub menu and boots - of course complaining the /var file system is not available.  I hot-plug the two S-ATA drives back in and the system boots!  It is up and running.

Seems to me there is something that could be configured in GRUB to make it all work.  But perhaps I could gather more information for the more technically minded?

Thanks for your posts, by the way.  Just glad to know people are experiencing the same issues out there.

---

### Post by tallthom on 2011-03-15
The strange thing is that the Ubuntu Server Install CD will allow me to have this configuration while I'm installing.  So it appears that what I'm doing is not as strange a setup as people make it out to be.  The root file system is on an IDE drive (IDE-0 MASTER).  And the /var file system is simply on a different HDD group - the PCI RAID card.  Note, RAID isn't configured.  I'm just using it as a S-ATA drive adapter in the machine.

Anyone have a deeper explanation or advice other than don't mix two hardware types together?

---

