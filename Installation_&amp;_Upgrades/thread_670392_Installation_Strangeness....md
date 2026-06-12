---
title: "Installation Strangeness..."
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by invictus84 on 2008-01-17
I was doing a complete fresh install, and planning to dedicate my entire hard drive to Ubuntu.  Used the manual install, instead of the guided, as I wanted a larger swap partition than what it gave me using the guided install (I've done a fresh install of Gutsy before, only gave me like a 730 mb swap partition).  Well, I thought I set it up right - put the swap as a logical partition, main partition as a primary.  Installation goes off without a hitch, reboot to go into the freshly OS and after login it just hangs.  Brownish screen (same as the login screen), and just sits there.  Activity light on the tower is going nuts, but nothing is happening.

I did, however, manage to get around it.  I used a Gparted live CD (ISO's available for download [here]("http://gparted-livecd.tuxfamily.org/")) to fix the partitions the way I wanted, making the swap partition a branch off of an extended partition, which forced the swap to be a logical partition (pardon my ignorance, not sure what the correct term for that would be).  Went back to the live CD and started the installer.  Again, went into the manual install method, changed the primary partition's mount point to "/", and it continued without any trouble.  Sitting in Gutsy right now, partitions are of the sizes I wanted and everything is working beautifully.

Just curious if anyone else has run across this problem, or perhaps knows what I may have done wrong during the initial manual installation. :confused:

---

### Post by zvacet on 2008-01-17
Did you during first install sign your primary partition as root (mountpoint /).if you didn´t that explains all.

---

### Post by Pumalite on 2008-01-17
It's better to have the /swap partition in the middle or at the end.

---

### Post by invictus84 on 2008-01-17
Yeah, seems I failed to mention a few things.  First of all, my system's specs are... less than impressive.  What I've got here is a Dell Dimension 1100, completely stock with the 2.66 GHZ Celeron, only has a 40 GB hard drive (Western Digital, I think, if that means anything to anyone) and 256 MB of RAM.  I've had to use the Gparted live CD I mentioned to make sure there's a swap file for the Ubuntu live CD to use, just to get it to boot at all.  And even then, it's pretty sluggish (but I'm fairly certain that's due to hard drive access times, being forced to use a swap file to suppliment my RAM and all :P)

Anyways, what caused the first reinstall was my attempt at resizing the partitions to suit my desire for a larger swap file.  I again used the Gparted live CD.  I'm thinking I caused some data loss, it would stop after the login after I resized the partitions.  So, since I hadn't really done anything with the computer yet, I just went for a reformat and reinstall.  Tried to size the partitions via the installer the way I wanted, made sure the mount point for the primary was "/", everything *seemed* to be in order, though it obvious wasn't.  Rebooted after reinstalling, got that brownish screen (same color as the default login screen), activity light went crazy, but nothing seemed to be happening.

This last time, I just did the partitions up the way I wanted them with that Gparted live CD (I've made it earn its keep the last week), went the manual route again, fixed the mount point for the primary partition, and off the installer went.  Installed without a single snag, boots up great, and I got the partitions sized the way I wanted them :popcorn:

[EDIT]: Forgot to say, I did accidentally leave out setting the primary partition's mount point to "/" once.  It didn't like that, gave me a warning and wouldn't proceed :P

---

