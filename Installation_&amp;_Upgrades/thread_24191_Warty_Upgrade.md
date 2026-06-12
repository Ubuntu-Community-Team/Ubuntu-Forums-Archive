---
title: "Warty Upgrade"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by Nez7165 on 2005-04-05
I have been reading all these threds and have recently installed ubuntu onto my machine and would like to go to Hoary. I dont beleve i have any back ports. Also so many ppl have had problems i was wondering if anyone could put it into a simple turms for me whitch i can follow. and give me a sause list i can use to do it from. Thanks

---

### Post by Psquared on 2005-04-05
[QUOTE=Nez7165]I have been reading all these threds and have recently installed ubuntu onto my machine and would like to go to Hoary. I dont beleve i have any back ports. Also so many ppl have had problems i was wondering if anyone could put it into a simple turms for me whitch i can follow. and give me a sause list i can use to do it from. Thanks[/QUOTE]
sudo apt-get clean
sudo apt-get autoclean (these clean the apt-cache)

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup (you can restore this if it does not work out)

sudo Gedit /etc/apt/sources.list to make sure backports are not enabled. If you do there are instructions in another thread (search backports) that tell you how to downgrade to a basic "warty." Then rem out (use #) any non-ubuntu sources. In the remaining entries change the word "warty" to "hoary." Do NOT change anything else - not even the spaces. Save the file.

Then run

sudo apt-get update
sudo apt-get dist-upgrade 

**with a broadband connection it will probably take close to 90 minutes.

If it doesn't take try rebooting a couple of times and running it again. I have heard that helps stubborn warty installs that don't want to upgrade.

If it still doesn't work chances are you have some backports installed. There is a thread on here about how to downgrade to a basic Warty so do a search and follow the instructions.

---

### Post by BillDrew on 2005-04-07
[QUOTE=Psquared]sudo apt-get clean
sudo apt-get autoclean (these clean the apt-cache)

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup (you can restore this if it does not work out)

sudo Gedit /etc/apt/sources.list to make sure backports are not enabled. If you do there are instructions in another thread (search backports) that tell you how to downgrade to a basic "warty." Then rem out (use #) any non-ubuntu sources. In the remaining entries change the word "warty" to "hoary." Do NOT change anything else - not even the spaces. Save the file.

Then run

sudo apt-get update
sudo apt-get dist-upgrade 

**with a broadband connection it will probably take close to 90 minutes.

If it doesn't take try rebooting a couple of times and running it again. I have heard that helps stubborn warty installs that don't want to upgrade.

If it still doesn't work chances are you have some backports installed. There is a thread on here about how to downgrade to a basic Warty so do a search and follow the instructions.[/QUOTE]
 This is simple?  I have non ubuntu applications running such as blosxom.  Will these cause any problems if I try to upgrade?  I am using the machine running Ubuntu as a production server.  Why not make the upgrade as a part of updates via Synaptic package manager?  I don't understand why it has to be so hands-on.

---

