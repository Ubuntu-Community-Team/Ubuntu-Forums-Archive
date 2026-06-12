---
title: "apt-get: svn has no installation candidate"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by noloader on 2009-12-21
Hi All,

svn seems to be missing for my installation of Karmic. Google returned one hit for the message. Any help would be appreciated.

Jeff

$ svn checkout [https://svn.sourceforge.net/svnroot/cryptopp/trunk/c5](https://svn.sourceforge.net/svnroot/cryptopp/trunk/c5) cryptopp
Unknown command: 'svn'
...
$ sudo apt-get  install svn
...
Package svn is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package svn has no installation candidate
$

---

### Post by lewisforlife on 2009-12-21
Try:

```
sudo apt-get install subversion
```

Also, check out this info: [https://help.ubuntu.com/community/Subversion#Installation](https://help.ubuntu.com/community/Subversion#Installation)

---

