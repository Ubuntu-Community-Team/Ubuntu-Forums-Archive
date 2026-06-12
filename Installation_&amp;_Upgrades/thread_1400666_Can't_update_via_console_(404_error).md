---
title: "Can't update via console (404 error)"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by Cybermage on 2010-02-07
Hi There,

about two days ago my apt broke. At least I think so.

I can update my sources via synaptic, but when i try via console I get 404 errors. To narrow the problem down, I striped my sources.list to only one line
```
deb http://archive.ubuntu.com/ubuntu/ karmic main
```

Then apt-get update gives me
```
Ign http://archive.ubuntu.com karmic Release.gpg
Ign http://archive.ubuntu.com karmic/main Translation-en_US
Ign http://archive.ubuntu.com karmic Release
Ign http://archive.ubuntu.com karmic/main Packages
Ign http://archive.ubuntu.com karmic/main Packages
Err http://archive.ubuntu.com karmic/main Packages
  404  Not Found
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

If i try to download Packages.gz manually, everything works fine
```
--2010-02-07 13:37:29--  http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz
Resolving archive.ubuntu.com... 91.189.88.40, 91.189.88.45, 91.189.88.46, ...
Connecting to archive.ubuntu.com|91.189.88.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1736742 (1.7M) [application/x-gzip]
Saving to: `Packages.gz'

100%[======================================>] 1,736,742   3.02M/s   in 0.5s    

2010-02-07 13:37:30 (3.02 MB/s) - `Packages.gz' saved [1736742/1736742]
```

Any hints how i can fix my apt-get?

---

