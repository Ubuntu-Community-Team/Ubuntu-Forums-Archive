---
title: "change update source mirror before upgrade"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by owise1 on 2010-06-05
Hi can you help - I am about to upgrade from Karmic to Jaunty and wonder if it is possible to select a different mirror for the upgrade.  I note that for Australia Karmic does not have the Telstra ISP Bigpond as a software source but I gather that it is available.  Lucid does however.  Been able to use bigpond would allow me un-metered download for the update which is a big saving when you have 4 machines and hit the 25G limit each month!

Cheers

Dave

---

### Post by davidmohammed on 2010-06-05
if you are worried about bandwidth I would download the alternate CD first and then pass that round to each PC to upgrade.  It will save the bandwidth.

Be-aware if you are on 9.04 - you'll need to download also the 9.10 alternate CD before you got to 10.04.

---

### Post by owise1 on 2010-06-06
Yep I suppose that will work and the bigpond file mirror will allow unmetered download as well - what about the packages that are not on the CD - will the upgarde process grab them from the web?

---

### Post by wilee-nilee on 2010-06-06
> **owise1 said:**
> Yep I suppose that will work and the bigpond file mirror will allow unmetered download as well - what about the packages that are not on the CD - will the upgarde process grab them from the web?

The live cd and the alternate both have the same stuff on them for install, the alternative is for installing if you have low ram or want to upgrade with saving some things, although I have never used it to do this sort of upgrade. Both will have a lot of upgrade to catch up.

I would download the live cd if you have at least 512 ram just to make sure that it's going to run, with no immediate graphic card problems....etc. Karmic is grub2 and ext4 so things are a little different. You said karmic to jaunty but I think you meant the other way around. Or do you mean Karmic to lucid.

---

### Post by davidmohammed on 2010-06-06
> **owise1 said:**
> Yep I suppose that will work and the bigpond file mirror will allow unmetered download as well - what about the packages that are not on the CD - will the upgarde process grab them from the web?

the alternate will upgrade all packages that existing in the standard canonical repositories.  If you've installed packages from other repositories and ppa's, then during upgrade it will have disabled those repositories (software sources).  You will need to manually edit those software sources - point them to lucid equivalents and then do a standard update-manager check.

---

