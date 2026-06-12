---
title: "Repositories broken?"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by struggling on 2007-12-25
Trying to get multimedia working on my just installed 7.10 Kubuntu system.

When I try to install codecs I get;
"
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
"

Is there something I can do to fix this or do I just wait for the files on the repositories to be fixed?

---

### Post by taurus on 2007-12-25
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

