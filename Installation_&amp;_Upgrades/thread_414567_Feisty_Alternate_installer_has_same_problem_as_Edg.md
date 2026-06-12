---
title: "Feisty Alternate installer has same problem as Edgy one"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by futz on 2007-04-20
I prefer the Alternate installer, so that's what I downloaded and burned. I went to install it on one of my older machines, which the Edgy live disk works perfectly on. Everything goes fine till 85% thru the 'Select and Install Software' part. It gets to britty-x11 at 85% and just stops. I let it sit for an hour just to see if it would eventually go, but no.

They obviously haven't changed a thing in the installer, because the Edgy alternate install did **exactly** the same thing on some machines.

I'm going to try the live disk installer tomorrow. I expect it to work, as the Edgy one did on all 85 percenter machines except one picky machine I have (that one takes a few boot options to get anything installed on it).

Anybody got any idea what's the deal? And how to get around the problem? Nobody had any idea last time I asked...

---

### Post by rgsproductions on 2007-04-20
I am having the same issue.  I made 2 disks just in case and both stop at the same x-11 britty 85% mark.  This is the firs time the alternative installer failed to work.  ISO file was ok and disks checksum is fine.  

Running on AMD 2400 512 ram with nvidia g420.

---

### Post by maxamillion on 2007-04-20
Either of you file a bug for it? ... if not please do, it will help the developers get it resolved. Sorry it didn't work :(

---

### Post by SmokingGun on 2007-04-20
It's a ******* joke!!!  That's all i can say.....

---

### Post by wadeall on 2007-04-26
I have the same probel with the installer gfreezing (at 61%)  when preparing to configure britty-x11

Before that it said that it couldn't find bangali fonts so maybe it has something to do witb that but Im just an average user - no expert.

---

### Post by mianwright on 2007-05-25
Yep. Me too. Feisty hung on britty and failed. I tried netboot, cd, iso. Nothing worked. Bummer. Also I am PPC (PowerPC) iBook G3 so it seems to be cross platform.
Luckily, OpenBSD works like a champ.

---

### Post by kelvin spratt on 2007-05-25
well i don't have the problem on my setup its stange working on one machine and not on another

---

### Post by Shaydog on 2007-06-19
I'm experiencing the same issue.  This is my first experience with Ubuntu and I've been having a horrible time trying to even get it installed.  When I use the alternate installer, it freezes at 85%.  When I use the Live CD, it boots into a blank screen.  When I boot into the rescue mode, it freezes upon performing fsck.  I don't know what to do :)!

I am trying to install it on a new HP tx1000z, AMD 64-bit dual core, 2GB Ram, NVIDIA GeForce GO 6150 :(

---

### Post by Shaydog on 2007-06-20
Well, it seems that it wasn't actually frozen, but attempting to download packages from the Internet.  However, I misconfigured my DHCP so it was not resolving any of the domains and was just taking a really long time to timeout on each request.  I went back and delayed configuring my network until later and it went okay.

---

