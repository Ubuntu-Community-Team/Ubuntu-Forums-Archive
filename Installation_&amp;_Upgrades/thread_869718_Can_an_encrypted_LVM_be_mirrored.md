---
title: "Can an encrypted LVM be mirrored?"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by ericcat on 2008-07-25
Hello there,

I hope that someone can help me with this little question concerning LVM and encryption.

I recently reinstalled Hardy 64-bit after I screwed up my setup trying to be clever (don't ask!:oops:).  It is now installed from the Alternate CD in an encrypted LVM (paranoid about hard drive theft!) on a single 160GB drive.  I have a second, identical drive that I'd now like to set up as a mirror to the first drive, for resiliency and redundancy (spent too long in the past rebuilding PCs due to drive failures!)

Thing is that I've not used LVM previously so don't know whether encrypted LVM mirroring is possible, and if it is, how it's done.

Has anyone else got this sort of config working?  If so, can anyone point me to a How-to, or offer advice on setting it up?

Thanks in advance to the community.

---

### Post by El Rogueo on 2008-08-30
(Odds are you've solved your problem by now, but in case not, here goes)

It sounds like it's just a matter of how you stack things. If you install with both drives listed in software RAID, you should be able to simply drop encrypted lvm right on top of that. I'm not sure if the installer will let you do that, but you can certainly perform something along the same lines from command line within the installation after booting the first time.

---

