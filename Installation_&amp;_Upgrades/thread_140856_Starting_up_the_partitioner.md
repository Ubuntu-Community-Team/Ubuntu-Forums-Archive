---
title: "Starting up the partitioner"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by Gabe on 2006-03-07
I'm installing on an old laptop (Compaq Presario 1600) and at 29% of "starting up the partitioner", it hangs, exits the GUI, and scrolls either "Killed" or a bunch of junk followed by "segmentation fault".  Formatting the drive does not fix this, nor does installing from a disk burnt at a lower speed, as someone on the #ubuntu IRC channel suggested.  Any help would be appreciated.

---

### Post by Mustard on 2006-03-14
I've been looking around for a solution for this problem, as its something I have seen on the forums quite frequently.  I suspect its caused by system with low RAM and that it could possibly be related to not having a swap partition.  Can you confirm whether you created a swap partition on installation and what RAM you have available on this system?

---

### Post by Gabe on 2006-04-05
Glad to see someone's looking into this, and yes, I wouldn't be surprised if it were caused by low RAM, as the machine that I'm installing on only has 56 MB.  However, I can't confirm whether I created a swap partition on installation.

So far, I have also tried installing on expert mode with "lomem" components loaded, and I'm still getting the same "Killed" message.

---

### Post by Mustard on 2006-04-05
[QUOTE=Gabe]Glad to see someone's looking into this, and yes, I wouldn't be surprised if it were caused by low RAM, as the machine that I'm installing on only has 56 MB.  However, I can't confirm whether I created a swap partition on installation.

So far, I have also tried installing on expert mode with "lomem" components loaded, and I'm still getting the same "Killed" message.[/QUOTE]

It's probably not really the best news, but I believe this issue has been dealt with in the new paritioner for the Dapper Drake release.  There are no plans to fix this in Breezy Badger release.  I guess the bull is already out of the gate so to speak, as there have been hundreds of thousands of CD's sent out with the old paritioner in the installer.  I would either look into running the current unstable development version or wait for the stable version of Dapper Drake to be released.

When I first read of the bug on Launchpad.net, the person describing the bug somehow set up a swap partition and mounted it, which allowed him to use the installer.  This is not something that I think is going to be easy for someone who is new to linux to do.

---

