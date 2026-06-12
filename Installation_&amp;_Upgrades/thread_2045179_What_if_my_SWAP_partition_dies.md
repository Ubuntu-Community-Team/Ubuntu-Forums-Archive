---
title: "What if my SWAP partition dies?"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by schworak on 2012-08-20
Ok, I have a RAID1 for my main data, and a separate drive for my /tmp folder and another separate drive for my SWAP.

I really haven't seen Linux actually use the SWAP because I have 8 gig of RAM. 

I know if for any reason if the drive that maps to /tmp fails to mount, the system uses the main /tmp folder without issue.

But what would happen if for some reason my SWAP drive stopped working? Does the system stop working until that drive is fixed? Does it boot up and simply disable SWAP until it is fixed?

I would really like to know before something actually happens to the swap. Mainly so I am prepared if it does.

---

### Post by 1clue on 2012-08-20
It's the same as any other data failure on a disk.  Only I don't think you could have a surface failure on your SWAP partition(s) and actually lose permanent data on the disk.  You might have a program crash but I don't think you could lose "persisted" data.

If you REALLY want a failure-tolerant drive, then you should put SWAP on RAID too.  That's typical for a production server with real data on it.

On my home box I've been playing with RAID for a few years, but haven't ever bothered to put SWAP on RAID.  I have 12g RAM, and I know for a fact that it's never actually paged out to SWAP.  I've put a lot of stuff on tmpfs too.

If this is a normal workstation then the rest of the drive is going to see a lot more use than your SWAP partition.  You need to have a partition of at least the size of your RAM, because if you hibernate it you need to page all your RAM out to disk, and AFAIK it needs to be a single partition.  It would be entirely different if you had 1g RAM.  Then your swap would be busy constantly, your box would run like carp and before you knew it the iron filings on your disk surface would get tuckered out and go to sleep forever.

IMO the only way you'll get a swap failure statistically speaking is if your whole drive goes.

---

