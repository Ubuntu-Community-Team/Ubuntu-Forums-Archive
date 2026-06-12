---
title: "Update failure : 404  Not Found [IP: 91.189.91.23 80]"
date: 2014-12-13
forum: Installation &amp; Upgrades
---

### Post by risva on 2014-12-13
Hello all,

while doing my ubuntu update through update manager ar apt-get update, i'm getting error 404 :

```
W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.23 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

i'm able to ping and telnet the 91.189.91.23 from my machine, rest of the sites are also available as expected....
i tired changing the source servers as well, i'm clueless how to resolve the issue...:sad:

please advice.

---

### Post by QIII on 2014-12-13
Which release of Ubuntu are you using?

The two urls are for Raring Ringtail (13.04), which has passed its EOL.

If you are using that release, you should upgrade to a supported release.  If not, those should be removed from your sources list.

---

### Post by risva on 2014-12-17
Thanx QIII,

never realised it! done!!

---

