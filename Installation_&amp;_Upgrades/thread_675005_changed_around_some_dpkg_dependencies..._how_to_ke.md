---
title: "changed around some dpkg dependencies... how to keep synaptic from bugging me?"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by miatawnt2b on 2008-01-22
OK, so I needed to compile the latest release of parted/libparted to solve a bug I was experiencing.  I downloaded the latest source of parted (1.8.8 ) compiled and installed.  Only to find out that gparted was still using the gusty build 1.7.  In my attempt to remove the ubuntu build I found a metapackage ubuntu-standard depended on parted.

Horse Hockey I thought, I am installing a new build of this, so I am going to tweak the ubuntu-standard dependency so that I can remove teh old parted/libparted versions.

So I edited /var/lib/dpkg/status file and removed parted from the ubuntu-standard dependency list, reloaded synaptic and removed the old versions of libparted and parted.

compiled and installed new builds of parted and gparted and went on my merry way.  However, update manager is wanting to update the old versions of libparted, parted and ubuntu-standard.

Ummmkay, so how do I tell it not to bother me about this any longer since parted and libparted ver 1.8.8 are installed, yet are not listed under synaptic since I built from source?

thanks,
-J

---

### Post by Shazaam on 2008-01-22
Open up Synaptic, find and highlight the offending package(s), go to "Package" in the toolbar and check "Lock Version" for each one. You won't be reminded to update said package(s) again.
To re-enable reminders look for and highlight the "Pinned" section on the left and you will be presented with a list. Highlight a package, go to "Package" again and uncheck "Lock version".

---

