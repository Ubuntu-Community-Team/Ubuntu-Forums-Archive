---
title: "Brother lpr printer driver corrupted my package database"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by roscar on 2007-03-19
Hi, I'm trying to figure out how to fix my package manager. When I open Synaptic, I get the following error:

E: The package hl1430lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

This began when I tried to install the hl1430lpr driver for my printer. I had a .deb file from the  brother website and part way through the install, it failed from the lack of a file. I can't remember which one and I can't duplicate it because the package database is messed.

I currently can't install or update any of my programs using apt or synaptic. I'm hopeing that I can figure out how to make things functional again. I'm quite happy to have the printer driver removed.

I'm running Ubuntu 6.06

---

### Post by nicktheawesome on 2007-05-31
I have this exact problem except I'm running Fiesty. I got the driver from the Brother website because I'm new to linux. I figured thats what you had to do. After hours of searching google, threads on here and other forums, and asking friends, I was told Ubuntu will run my printer (HL-1435) natively.

That may help you out, but then you will come to my problem. I can't delete the hl1430lpr file. And while it is still installed, I can't get the synaptec or anything to work.

If anybody had any solutions, I'd be most grateful. I'm getting really frustrated because I can't get rid of this one file.

Thanks

---

### Post by jaucremann on 2007-05-31
I've had the same problem myself. I have a mfc-440cn and it did the exact same thing. I have a hl-2070n that worked. I'm not new to linux but I am to Kubuntu. If anyone has a suggestion on how to clear out that bad package I'd love to hear it. At this point I just want to dump the driver and start over, I can't install any packages until I fix this. I'm running Kubuntu 7.0.4. I did send brother a message telling them what the problem was, if they respond I'll post the solution. Thanks

---

### Post by nicktheawesome on 2007-06-01
I got it, it is probably excessivly complex, but it works.

[http://ubuntuforums.org/showthread.php?t=340848&highlight=hl1430lpr](http://ubuntuforums.org/showthread.php?t=340848&highlight=hl1430lpr)

I've been trying to figure out how to delete the files in question, and you have to login as root, and do it there. It all works now. Awesome.

---

### Post by jaucremann on 2007-06-04
Hey thanks for the link. That worked great.

---

