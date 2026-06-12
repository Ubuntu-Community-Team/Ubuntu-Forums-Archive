---
title: "Upgrading from hoary not possible - breezy is no longer supported"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by craig.taverner on 2007-06-07
I want to upgrade a production server from hoary, if possible all the way up to feisty. But all the articles I've found on the subject recommend incremental upgrades, through breezy, dapper, edgy and finally feisty.

The problem is that I cannot find breezy on any archive or mirror site, so I cannot use either apt or update-manager to do the upgrade. I would rather avoid having to re-install completely if possible. I saw on another post a mention of a packages.ubuntu.org site, but that did not appear to be structured for apt to work with. Any ideas?

---

### Post by autocrosser on 2007-06-07
Goto your /etc/apt/sources.list & manually change everything from hoary to breezy & do a sudo apt-get update--this will see if you can still download the breezy files---if not, I still have some breezy alernate & liveCD's--just E me.....

---

### Post by craig.taverner on 2007-06-08
Thanks for the advice, but that's exactly what I meant by "cannot find breezy on any archive or mirror site". I had tried a bunch of possible sites in the sources.list and apt rejected all of them. Manual searches of those sites, including the main archive.ubuntu site showed that breezy was no longer available. Google searches indicate that they were removed as recently as last month. Bad timing for me :(

Thanks for the suggestion to use the CD's. I've just discussed this with a friend, and he happened to have exactly the breezy live CD, so I'll give that a try. :p

---

### Post by madmetal on 2007-06-08
i think i also have some breezy cds somewhere.. 
if you really need them i can search..

---

### Post by AlanRogers on 2007-06-08
Unless you are specifically setting out to prove a point or carry out some research, I would suggest that you're in grave danger of not achieving your end goal, if you want to try to incrementally upgrade from Hoary to Feisty.

For the time it would take you to perform the upgrade 4 separate times (Hoary > Breezy > Dapper > Edgy > Feisty), including the download times to get all the files and then make sure that they were the latest before performing the next upgrade, you'd be better off installing from fresh.

I recently upgraded a machine from Dapper to Edgy to Feisty and it wasn't smooth. That is most likely because I'm still learning but the fact remains that you're potentially heading into a world of pain, especially if you have no backup.

If I may be so bold as to make a suggestion, this is what worked for me:[LIST=1]
[*]Partition your hard drive or add a second one
[*]Use [Aiysu's notes]("http://www.psychocats.net/ubuntu/separatehome") to move /home to this location
[*]Install Feisty from scratch, remembering NOT to format your /home partition[/LIST]I believe, but stand ready to be corrected, that this is the recommended method anyway. Either way, this'll take you a couple of hours while I suspect the route you're suggesting will take far longer.

---

### Post by Josh Kurtz on 2007-06-08
I second AlanRogers' suggestion.  It will be much less painless on this upgrade and any others if you just move /home to a separate partition and then install a fresh fiesty in / which would have its own partition.

---

### Post by Aelfric5578 on 2007-06-25
You may have already resolved this problem by performing some sort of backup and clean install as described above, and I don't really know if incrementally upgrading from Hoary to Fiesty is a good idea, but you can find old Ubuntu releases on the main website, if you click around a bit: [http://old-releases.ubuntu.com/releases.](http://old-releases.ubuntu.com/releases.)

---

