---
title: "Couldn't download all repository indexes"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by nsiva007 on 2010-08-18
Hi guys,
       this problem happened yesterday when i updated my system running Ubuntu 10.04 LTS,through update manager,everything was normal till i got an error message like this.....> Failed to fetch [http://apt.wxwidgets.org/dists/gutsy-wx/main/binary-i386/Packages.bz2](http://apt.wxwidgets.org/dists/gutsy-wx/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.I don't have an idea of what it is,can someone plz help... Does that mean my system is not upgrading??

---

### Post by nbkr on 2010-08-18
The errormessage lists a custom repository (one that is not maintained by the Ubuntu Community / Canonical). It seems that this repository is also meant for "Gutsy Gibbon" - an old version of Ubuntu.

The repository is probably not maintained any more and therefore shouldn't be used anymore.

The updater won't use this repository and won't update the packages out of this repository. The rest should be updated as normal.

---

### Post by nsiva007 on 2010-08-19
Hmm so it doesn't affect my update process right? Shall i remove gusty source from my software source list???

---

### Post by Cavsfan on 2010-08-19
> **nsiva007 said:**
> Hmm so it doesn't affect my update process right? Shall i remove gusty source from my software source list???

Yes, if you are not using Gutsy Gibbon, you should remove that entry and all will be fine.

---

### Post by nsiva007 on 2010-08-21
Thanks :-) .....! Got my doubt cleared ;-):-)

---

