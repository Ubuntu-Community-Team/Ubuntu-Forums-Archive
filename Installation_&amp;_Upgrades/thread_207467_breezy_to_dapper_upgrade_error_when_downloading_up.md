---
title: "breezy to dapper upgrade error when downloading upgrades"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by The Pinny Parlour on 2006-07-01
Hi all,

I get this when attempting to upgrade my breezy to dapper:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found


I can't update at all, it just hits the wall.

Any info on what I maybe able to do would be great.

TIA
Ian

---

### Post by rcarring on 2006-07-01
You should comment out any repo sites not in the standard list.

In your case comment out all of the four sites you mention with a ##

Alternatively if the us.archive.... site is slow, change the us to uk and try that.

NB remember to copy your sources.list to sources.list.old

---

### Post by The Pinny Parlour on 2006-07-02
Hi rcarring,

Thanks mate.  Tried what you said and got things working  for the upgrade.

Most went well, just xchat failed after the upgrade process, but it was easy to reinstall/update via SPM.

Cheers
One happy Dapper User.  :D

---

