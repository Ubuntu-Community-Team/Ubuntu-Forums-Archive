---
title: "Intrepid to Lucid with Alternate CD"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2010-12-25
I have used the alternate CD to upgrade other people's older Ubuntu installations and it always presents the option to upgrade as well as the option to install. For some reason the alternate CD is not seeing the current installation of Intrepid. 

When booted to Intrepid the update manager offers me the option to upgrade to 9.04, but I'd have to do two more upgrades to get to Lucid. I thought it would be simpler to use the alternate CD to go directly to Lucid.

The computer currently has Intrepid x86_64 on a software RAID (two hard disks mirrored with mdadm). Update manager has never been run, so there are 300+ updates currently available for Intrepid. I doubt that is the source of the problem; I think it has something to do with the alternate CD not seeing the RAID.

Suggestions and advice needed. Oh, but if the only solution is to reinstall, I'll leave it as Intrepid. Too much software and tweaks installed - it would take a week to get it all back again.

---

### Post by John Jason Jordan on 2010-12-25
Well, now I've done it. I tried to run Update Manager to install the 300+ updates for Intrepid. It failed to find all but a couple of the packages, so I aborted the upgrade.

Then I launched Synaptic and marked all the updates for installation. Again, Synaptic failed to find almost all the packages, so again I aborted the update. 

Then I reloaded the repositories, and now I'm really in bad shape. Synaptic failed to find almost all the repositories, and now lists a total of 1642 packages available. It had been set to Main Server for the United States, so I tried setting it to other servers, but it still lists only 1642 packages available.

What happened to the repositories for Intrepid?

---

