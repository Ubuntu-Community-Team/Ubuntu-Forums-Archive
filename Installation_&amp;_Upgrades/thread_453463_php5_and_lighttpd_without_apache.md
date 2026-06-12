---
title: "php5 and lighttpd without apache"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by sanctus on 2007-05-24
If I want to install php5, the package manager request apache2 as a dependency. But I only want lighttpd. 

Is it possible not to install apache2?

Thank you

---

### Post by kidders on 2007-05-25
Hi there,

I'm not altogether sure where the Apache dependency is creeping in. I don't see it on *my* system...

```
$ apt-cache depends php5-cgi
php5-cgi
  Depends: libbz2-1.0
  Depends: libc6
  Depends: libcomerr2
  Depends: libdb4.3
  Depends: libgdbm3
  Depends: libkrb53
  Depends: libpcre3
  Depends: libssl0.9.8
  Depends: libxml2
  Depends: zlib1g
  Depends: mime-support
  Depends: php5-common
  Depends: libmagic1
  Suggests: php-pear
  Conflicts: <php3>
```

I could be missing something ... I've never used lighttpd, so I wouldn't be surprised!

[SIZE=1][COLOR=Silver][*[UAResolved]*]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR][/SIZE]

---

