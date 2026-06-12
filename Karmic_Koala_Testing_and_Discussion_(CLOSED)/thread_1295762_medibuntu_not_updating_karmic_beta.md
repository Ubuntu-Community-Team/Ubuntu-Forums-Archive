---
title: "medibuntu not updating? karmic beta"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cjxc92 on 2009-10-19
Hey guys,

I was trying to watch a dvd earlier and was getting an error that Totem couldn't read the resource which was odd because it had been working yesterday.  I checked and couldn't find the libdvdcss2 package in synaptic, and after some investigating I found the following error in the Update Manager:

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/karmic/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/karmic/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/karmic/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/karmic/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/karmic/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/karmic/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Which I think is related to my problem playing dvds (considering it regards a failure to find medibuntu).  Is anyone else having a problem like this?  

Thanks in advance

---

### Post by cor2y on 2009-10-19
No the medibuntu repos for karmic were working fine as of last week.
If they fail to connect on your end you can individually download the packages that you need manually.
[http://packages.medibuntu.org/](http://packages.medibuntu.org/) just select your distro.
If they are down in time they will be back up

---

