---
title: "Ubuntu install caused problem on DCHP server."
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by ivaarsen on 2008-10-29
Heya guys.  I've got an interesting one for you.

I recently attempted to start an install process on a machine using the 8.04.1 Alternate CD.  I was on a mission to try out the OEM installation feature, so I was using OEM mode during the alternate install.  I discovered something interesting and (maybe) potentially alarming.

Even though there's a Windows 2003 Server machine providing DCHP, I found that the DCHP query didn't work.  Then, out of coincidence, another machine I had brought up on the network also couldn't get a DCHP address.  This was the first thing I noticed.  

It didn't take me long to start looking at my DCHP server, and to my horror, ALL (and I mean ALL) of the addresses in the DCHP pool that didn't have a lease already showed as a BAD_ADDRESS, and NO (and I mean NONE of the) addresses were available for new DCHP clients.  For some reason Ubuntu rejected all of the addresses?

I confirmed this over and over by accident.  I would delete the BAD_ADDRESSes out of the DCHP server and then immediately try to obtain an address in my Ubuntu install;  same result.  I was, however able to obtain an address with another machine after I deleted the BAD_ADDRESSes, but before I queried the DCHP server with my Ubuntu install.  It took me shutting of the culprit machine to figure it out.  It stopped happening after that.

I don't have any screen shots or anything to prove this, and I haven't tried to recreate it yet.  I just wanted to know:  Has anybody ever heard of this kind of scenario?  Where a DCHP query clogs up a DCHP server like that?  :confused:

---

