---
title: "Ubuntu 7.04 instillation problems"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by FLCLFan on 2007-04-19
When i try to install Ubuntu 7.04 (tried i386 and amd64) i get some kink of error. It stops at 82% and i beleve the last part of the problem is:

> Apr 19 18:32:29 ubuntu ubiquity: cannot open /target/etc/apt/sources.list: No such file
Apr 19 18:32:29 ubuntu ubiquity: 
Apr 19 18:32:29 ubuntu ubiquity: Using CD-ROM mount point /cdrom/
Apr 19 18:32:29 ubuntu ubiquity: Unmounting CD-ROM
Apr 19 18:32:29 ubuntu ubiquity: Waiting for disc...
Apr 19 18:32:29 ubuntu ubiquity: Please insert a Disc in the drive and press enter 
Apr 19 18:32:29 ubuntu ubiquity: 
Apr 19 18:32:29 ubuntu ubiquity: Mounting CD-ROM...
Apr 19 18:32:30 ubuntu ubiquity: E: 
Apr 19 18:32:30 ubuntu ubiquity: Failed to mount the cdrom.
Apr 19 18:32:30 ubuntu ubiquity: 
Apr 19 18:32:30 ubuntu apt-setup: warning: /usr/lib/ubiquity/apt-setup/generators/50cdrom returned error code 100; discarding output

I attached the full log.

Please help

Thank you

---

### Post by Marcos.Rufino on 2007-04-19
> **FLCLFan said:**
> When i try to install Ubuntu 7.04 (tried i386 and amd64) i get some kink of error. It stops at 82% 

This same problem is happening to me!
My installation is stalled at 82%, with the following message: 
"Configurando o apt"; "Lendo o espelho" [In english, it is something like "configuring apt"; "reading the mirror"]

Please, how can I solve this??

---

### Post by FLCLFan on 2007-04-19
Ok, i figured out how to fix the problem for me.

All I did was I unplugged my Ethernet cable and reinstalled it and it worked fine.
(In other words, unplug the internet and install ubuntu again :) )

---

