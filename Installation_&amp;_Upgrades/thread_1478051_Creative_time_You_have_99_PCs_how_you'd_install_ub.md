---
title: "Creative time: You have 99 PCs how you'd install ubuntu in all of them?"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by stimpak on 2010-05-09
Here's a nice scenario: You are in charge of a computer lab, which has exactly 99 PC + 1 (The administrators workstation) connected to the intranet. (ip ranges from 192.168.1.1 - 100 + 1 , router at 192.168.1.254) 

How you'd install ubuntu in all of them with the minimal effort, or waste of time?

Of course you wouldn't burn 20 cds and install it in batches of 20? 

How you'd pass some rudimentary configuration in all of them? 

Lets say there's a NFS you need to mount in all of them in the mount /data (what happens if the time of install you cant ping the NFS server)

How you'd  handle a situation like that? 

ps I really have no idea how to solve this problem: It poped to my mind and i thought lets ask the others and see how imba they can be!

---

### Post by lemming465 on 2010-05-10
This is a job for PXE network booting off a dhcp+tftp+nfs server.  You'd have to figure out what you wanted to boot: a LTSP lab, diskless workstations, or just the regular installer.

---

### Post by lykwydchykyn on 2010-05-10
> **lemming465 said:**
> This is a job for PXE network booting off a dhcp+tftp+nfs server.  You'd have to figure out what you wanted to boot: a LTSP lab, diskless workstations, or just the regular installer.

This, plus a local [apt-mirror]("http://apt-mirror.sourceforge.net/") and [preseeding]("http://wiki.debian.org/DebianInstaller/Preseed").

Alternately, something like G4L or clonezilla would work.

---

### Post by tgalati4 on 2010-05-10
Burn 5 CD's, print out a cheat sheet and let the students do it.

Show them how to stream some music so they have something to listen to while babysitting the installs.

---

### Post by Aearenda on 2010-05-11
If they are all the same, install one and have Clonezilla + DRBL multicast the disk image.

---

