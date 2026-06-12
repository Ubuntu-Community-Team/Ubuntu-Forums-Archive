---
title: "IBM E-Server X-Series 342 Install Issues"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by Bansuri on 2007-10-01
IBM E-Server X-Series 342 
2-P3 @1.13
2 SCSI 18G HDD
2 Gigs ECC RAM

Trying to install Edubuntu7.04 or Ubuntu 7.04

The installation hangs at different % depending on what I add to the install command after F6ing on the install GUI. I've tried:
noapic
nolapic
acpi=off
pci=noacpi
sudo hdparm -d1/dev/hdb
and any combination of them.
I've dried 5 other drives, both DVD and CDROM.
Tried new cables.
Definitely not the disc, verified from install GUI on different PC and installed on different PC.
Tried Gutsy beta.
The BIOS Bug acpi thing pops up, also (numeric string) is not an IRQ resource errors are all surpressed by the above commands but it still wont get past 12 or 22 %.

I'd like to get something new but I don't have the cash and this is going to be a server for 6 or 7 thin clients at my kids daycare. I've convinced the owner to network boot some 95 and 98 machines and I'd donate the server and a couple IBM thinclients. With dual P3's and 2gigs RAM it seems like it would be a great server if I could just get it installed. I showed her how easy it is to install edubuntu on a PC, click update when the available updates prompt appear, reboot, and then PXE an old laptop without any configuring of the server PC. Pretty freakin impressive indeed, try that on a windows box! Unfortunately that install was on my main PC and I can't part with it yet.
But back to the problem, if this hardware is just too old maybe I could drop a different mobo in the case. She isn't averse to spending some $, but this IBM just seemed like the perfect candidate.
BTW, I found all of the install prompts on the forums, sounds like other folks are having similar problems and many were able to install with the additional arguments, just not me.

Thanks,
Robert

---

### Post by Mad Dawg on 2007-11-13
Good luck!  I'm the author of [this thread]("http://ubuntuforums.org/archive/index.php/t-445853.html"), and have never received any really good advice about what to do.  Now that Gutsy is out, I'm having the same problem with it.  As best I can tell, my issues start when Ubuntu moves to using some new disk drivers that treat all drives like SCSI (hda, on my machine, becomes scd0).  Apparently the IBM on-board IDE controller has some issue with this.  I can verify MD5 sum, I can install on other machines, but my IBM thinks the disc has errors when I run a file check from Ubuntu installation prompt.  If I alt+f1 over to console during the install progress indicator halt I see...

SQUASHFS error: sb_bread failed reading block ...
SQUASHFS error: Unable to read page, block ...

Over and over again.

Tried acpi=off, no apic, no lapic, hda=cdrom, etc.

If you ever figured it out, I'm all ears.

---

### Post by Bansuri on 2007-11-13
I finally gave up as I don't have enough knowledge for that level of troubleshooting.
However, maybe some expert eyes have seen this thread and might have some advice.
It's a solid machine, runs win2003 server with no issues, but if I can get edubuntu running on it there will be a whole daycare full of linux-kids. It's the only machine we have with the RAM or processing power to run LTSP. 

Fingers still crossed,
Robert

---

### Post by ethanlifka on 2008-07-10
I am having the same issue.  I have three IBM blade servers. 2x p3, 2g Ram, Same motherboards.  All three wont verify the CD MD5 and will hang on "Loading Additional Components", but the CD works fine on other PC's.  I have tried Ubuntu 6.06, 7.04, 7.10, and 8.04 with no changes.  I know now that it is an IBM thing and since all three do it, its not a defective cd drive.  At this point I am looking to see if other distros might work, but I realy would like Ubuntu.  I can only think it is a cd-rom drive issue.  Maybe inproper ATAPI drivers or BIOS issues with the cd drive.  

if anybody has any success please let me know.
thanks ahead.

---

### Post by Bansuri on 2008-07-10
Ethanlifka,
I tried a stack of varied CD-ROM drives with no effect on the install errors. In the end no cmd line argument, different drive, or different disc made any difference at all. I was able to get much further in the install using an old version of Ubuntu but it wasn't the flavor we needed and wasn't able to upgrade. 
*Please post* if you DO have luck though, because there are lots of those IBM's out there and I still believe they are a great candidate for an Ubuntu server. The LTSP is a perfect solution for many educational environments. (IMO)

---

