---
title: "Ubuntu System Image possible?"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by fallen1011 on 2011-10-20
when in windows if you make a system image it will image all software installed files etc, so once u install the image on a pc it will load it exactly what was on the os replacing the drive or current os, without actually having to reinstall windows kind of like a back up, can ubuntu do this at all ? because i want to install ubuntu on my other machine without actually havving to load the cd then install all my programs and then customs made themes and shortcuts etc i have set up the system the way i want, so if there is any other way please let me know. thank you in advance!!

---

### Post by Grenage on 2011-10-20
There are tools such as remastersys, or you can create a complete image using programs like CloneZilla.  dd would also work, and is what I often use.

---

### Post by vidtek on 2011-10-20
> **fallen1011 said:**
> when in windows if you make a system image it will image all software installed files etc, so once u install the image on a pc it will load it exactly what was on the os replacing the drive or current os, without actually having to reinstall windows kind of like a back up, can ubuntu do this at all ? because i want to install ubuntu on my other machine without actually havving to load the cd then install all my programs and then customs made themes and shortcuts etc i have set up the system the way i want, so if there is any other way please let me know. thank you in advance!!

fallen- I think maybe the linux tools grengage is talking about may be a little esoteric for a newbie, a little like grappling with Norton Ghost's command-line.

If you have any of the freebie DVD's which come with computer magazines, many have Acronis or Paragon backup's cut down or old versions, you will find these a lot easier to use.

One salient point though, these programmes are very dependent on architecture, you need to know how they are set up in your machine's bios.  There are 3 ways in which they may be listed:

1) raid
2) ahci
3) ide

Check in your bios to see how they are set up, if they are set to ide, most bootable discs used by Acronis and Paragon won't work (no drives will be seen).  They will only work for raid and ahci.

Best of luck, Tony.

---

