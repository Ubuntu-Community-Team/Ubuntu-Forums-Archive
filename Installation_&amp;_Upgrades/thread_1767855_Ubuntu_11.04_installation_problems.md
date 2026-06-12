---
title: "Ubuntu 11.04 installation problems"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by kdx7214 on 2011-05-26
Okay, I have two major problems with this installation.  I am seriously disappointed in this - it's the first release of Ubuntu I've had any serious issues with.

First, the video drivers during install.  I can boot from the install CD and everything works just fine.  I can load firefox, browse the web, etc.  When I go to run the installer I pick English and then it just goes into perpetual wait mode. I've let it sit for > 1 hour to no avail.  Ctrl-Alt-F1 terminal and checking logs looks like the problem is with the Nvidia drivers it's trying to use (I have a GTX-460 card).

So then I decided to say to heck with it and use the alternate installer in text mode.   Downloaded, burnt to disc, verified disc and all is fine.   Start going through partitioning and it shows the wrong partition table.  

By wrong partition table I mean that it shows a partition table that had been used back when I ran Mac OSX on this machine.  Currently it's a simple 360gb Win7 installation with 140gb free space.   

I've never seen a partition table show up incorrectly but it is now.  I can boot with the 10.10 installer and it shows the partition table correctly.

Any thoughts on this or is 11.04 just so screwed up that I should stay on 10.10 for a while?

---

### Post by this_costs_more_cell_bill on 2011-05-26
I have serious installation problems with Ubuntu 11.04 too. First I used a CD, and I got input/output error during installation so I thought it was the CD. Then I used an USB drive and I got the same error.
I suspect it's the same issue reported by ***kdx7214 - ***partition table show up incorrectly.

When I did a Kubuntu upgrade from 10.10 to 11.04, I have another problem - It won't start X up to the end, but keeps looping back to credentials panel, asking for the password.

Kubuntu/Ubuntu 11.04 seems to be really buggy... :mad:

P.S. It proved to be the ISO file. If you will use the torrent to get the ISO file, then installation goes well.

---

