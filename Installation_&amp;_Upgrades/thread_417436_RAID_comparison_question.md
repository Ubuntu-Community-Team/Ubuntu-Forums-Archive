---
title: "RAID comparison question"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by DaftBugger on 2007-04-21
Hi folks,

I'm a long time XP user, interested in trying Ubuntu (cos everything MS touches seems to turn to pish). Problem is that I have to keep my Windows install for work reasons.

Tried installing Ubuntu, but I have a fakeraid setup and it's an a**load of hassle to do, especially for a Linux noob like me.

Found an old Adaptec 1210SA RAID controller card in my junk drawer.

My question is this - which would give me better performance?

1) the onboard fakeraid on my Asus A8ne motherboard

2) the Adaptec 1210SA (PCI) RAID controller

3) a new PCI-E RAID controller (I read somewhere that PCI-E is much better for this sort of thing). If so, any recommendations?

If the hardware controllers give better performance, will Ubuntu see them staight away, or would I still have to bugger about with dmraid and all that?

Thanks for your help!

---

### Post by stevecs on 2007-04-21
Unless you have a server motherboard that has a full fledged hardware raid chip on it the on-board raid will not be that fast (and even with server based solutions a dedicated card (a good one) will be much faster).   

Software raid (meta devices or whatnot) is probably the fastest with the same hardware assuming you have a recent computer.   The problems with software raid is that you are stealing cycles from your system to run the raid code which removes those from running your applications.    Then IMHO software raid is more manually intensive for doing replacements/migrations/et al of the raid in operation.    With hardware it's down to the point where a "tape monkey" (no offense to anyone doing that job, used to do it myself. ;) )  can pull a drive out and slap a new one in and that being the end of the matter.    With software raid you have more configuration that you need to do as an admin (this is true regardless of platform, ie, veritas, disksuite, md, whatever).

In my systems I've used both extensively over the years.   I'm actually using both on the same platform right now actually for the new build a raid-1 for my two boot discs (software meta device) which holds the applications and then an Areca ML1280 24-channel sata raid controll for the 12TB of disk in the same chassy.   With the drives formatted out as a JFS partition (should have used XFS and probably will with my next full backup/restore) I got about 500MB/sec in random block mode (bonnie++) to the drive.   That slows down when you fill the drive up but not too bad using the WD5000YS 500GB drives. 

To your point PCI-E is much preferred for pretty much everything.   I can not think of any reason to go with a PCI-X or absolute worse PCI based slot at all unless you have absolutely no means to get a PCI-e card (or don't have the slot(s).     PCI-X 133Mhz 64bit (the top of the spec) is rated at 1.04GB/sec it is a buss architecture so if you have two cards (say two 10GbE cards) you'll get best case 500MB/sec each in the real world less as you have other items on the same buss.    With PCI-e you have much more headroom up to 8GB/sec with the 8x card that I have I have theoretically 4GB/s bandwith to the card.    When I test writing to/from the card's 2GB cache module I get over 1GB/sec (raid-5).  so I'm doing equal-better than what a PCI-X can do right there.


Areca cards I've found are real nice and have performed better than the 3ware/adaptec cards I've compared them to.   These are for SATA drives, if you have a mixed environment w/ SAS though you can get some real nice SAS raid/HBAs that can do both.

---

