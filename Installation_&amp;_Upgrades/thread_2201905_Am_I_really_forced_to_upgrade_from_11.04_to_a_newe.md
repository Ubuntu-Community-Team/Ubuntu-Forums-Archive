---
title: "Am I really forced to upgrade from 11.04 to a newer version?"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by pstein on 2014-01-26
One of my Ubuntu installations is an older Ubuntu 11.04 release.

I set it up to test a certain server software and it runs fine and I want to keep it.

However now I want to update some software but not the Ubuntu as a whole.

When I trigger update process then Ubuntu tells me "Your release is not supported any more" and it seems that I have no other choice than to update to a newer release of Ubuntu.

Can someone confirm that?

Is there really no AUTOMATIC (!) update of existing background software like openssh, ext3, crontab,...

All these tools can run independently from Ubuntu GUI and hence could automatically be updated by the update procedure.

I don't want to update them all manually in a terminal but want to use the update manager.

Peter

---

### Post by 1clue on 2014-01-26
Disconnect that machine from the outside world and keep going.  It would be a good idea to get a complete bootable backup and burn that someplace safe, so that if something happens to it you can restore it.

One good idea for that would be to convert it to a VM, take that snapshot and you can restore with the click of a button after that.

Part of the whole point of a release cycle is that at some point doing an upgrade to core functionality will cause a potential instability.  Linux can either use rolling releases like Gentoo, where you continually update and there's no real distinguishing feature about any image, or they can go like most distros (Ubuntu included) and build something more reliable around a specific set of dependencies.  By choosing a release cycle you also choose to put up with its obsolescence and a subsequent mandatory upgrade.

The upgrade is mandatory simply because of the loss of support, which gives you security updates for known vulnerabilities. If you can isolate yourself from those, you don't really need to upgrade.

---

### Post by sudodus on 2014-01-26
> **1clue said:**
> Disconnect that machine from the outside world and keep going.  It would be a good idea to get a complete bootable backup and burn that someplace safe, so that if something happens to it you can restore it.

One good idea for that would be to convert it to a VM, take that snapshot and you can restore with the click of a button after that.

Part of the whole point of a release cycle is that at some point doing an upgrade to core functionality will cause a potential instability.  Linux can either use rolling releases like Gentoo, where you continually update and there's no real distinguishing feature about any image, or they can go like most distros (Ubuntu included) and build something more reliable around a specific set of dependencies.  By choosing a release cycle you also choose to put up with its obsolescence and a subsequent mandatory upgrade.

The upgrade is mandatory simply because of the loss of support, which gives you security updates for known vulnerabilities. If you can isolate yourself from those, you don't really need to upgrade.
+1 (confirmed)

---

### Post by egeezer on 2014-01-26
Since 11.04 is no longer supported, the answer is that you will have to update the whole installation.  I recommend you go to a Long Term Support version, currently 12.04.  That will be supported until April of 2017, and from my experience is it a far better version than 11.04.  You will not be disappointed if you make the switch.

---

### Post by Bucky Ball on 2014-01-26
++1.

11.04 hasn't actually been supported for about a year and a half. If you are running servers you probably should be using LTS releases anyway. You can upgrade from one LTS to the next very simply, bypassing the need to upgrade through the interims. The LTS releases are five years support so I suggest you install 12.04 LTS and upgrade, if you want to, when 14.04 LTS is released in April.

With 12.04 you'll have until 2017 to decide by which time 16.04 LTS will have been released, supported until 2021!

---

### Post by grahammechanical on 2014-01-26
The developers have already done what you want. It is called Ubuntu 11.10 and then Ubuntu 12.04 and 13.04 and now 13.10. In this way we get the most recent libraries and tools that have been tested and shown to be stable. All these components of a Linux distribution are interdependent upon each other.

Oh, I have not noticed Update Manager running independent of a GUI. You need to install a server edition. Then you and upgrade without getting an upgraded GUI.

---

### Post by 1clue on 2014-01-26
I have to throw in a plug for an outdated release here.

If you're supporting custom software for a client, and they have old software and do not want to upgrade, then keeping an out-of-date distro around makes sense.  We have several such clients.  We continue developing on more recent distros but we still support clients who might want a single change to the version they have for as long as they pay support.

For that scenario, supporting an outdated service, when neither the development/testing environment nor the final product is exposed to the Internet, there's really no harm in it.  Especially if it depends on a certain version of a library, it can become crucial.

IF the server is connected to the Internet, then I strongly recommend bumping to the latest LTS, which is 12.04.  Keeping an outdated server publicly available is asking for more trouble than anyone wants.  But if it is or can be isolated completely, then moving it to a VM and backing that VM up becomes extremely viable.

---

