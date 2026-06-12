---
title: "Updates wont update...?"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by YoungD112 on 2010-03-11
Hey. well whenever I get the update notification I end up with this error screen:

Could not download all repository indexes
The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://tskariah.000webhost.com](http://tskariah.000webhost.com) ubuntu Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://tskariah.000webhost.com/ubuntu/dists/ubuntu/main/binary-amd64/Packages.bz2](http://tskariah.000webhost.com/ubuntu/dists/ubuntu/main/binary-amd64/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

...

Is this an important update I'm missing? And does anybody know how to fix this?

---

### Post by snowpine on 2010-03-11
[http://tskariah.000webhost.com](http://tskariah.000webhost.com) is **not** a default software source for Ubuntu. Maybe it's something you added for some reason?

---

### Post by YoungD112 on 2010-03-11
Hmm, going to that site, I don't remember downloading it...is there anyway to get rid of this then?

---

### Post by snowpine on 2010-03-11
You can edit your software sources with:

```
gksu gedit /etc/apt/sources.list
```

Type a # symbol at the beginning of the offending line; this will comment it out so the update manager skips it. Don't forget to save the changes! Then try the update again. :)

---

