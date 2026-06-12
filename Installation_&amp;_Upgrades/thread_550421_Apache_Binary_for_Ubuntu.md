---
title: "Apache Binary for Ubuntu"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by resume-writer on 2007-09-13
I'm don't know how to build a binary from source code. I'm sure that this skill is common in this forum, but I'm just a writer that would like to create a wiki. So, is there a way to get an Apache binary for Ubuntu. Is it in this list:

[http://www.apache.org/dist/httpd/binaries/](http://www.apache.org/dist/httpd/binaries/)

I don't see anything that says ubuntu, but maybe I can us another binary?

Thank you,

Angela

---

### Post by Pumalite on 2007-09-13
[https://launchpad.net/ubuntu/gutsy/+package/apache2](https://launchpad.net/ubuntu/gutsy/+package/apache2)

---

### Post by resume-writer on 2007-09-13
Thank you. Say, I went to that site, but I don't see any package that looks like it will run on Intel Core 2 Duo.

---

### Post by Pumalite on 2007-09-13
You'll have to wait and see; won't you?

---

### Post by avik on 2007-09-13
Isn't it in the repos?  Check in synaptic.

---

### Post by scxtt on 2007-09-13
sudo aptitude install apache2
```
:> aptitude show apache2
Package: apache2
State: not installed
Version: 2.2.3-3.2ubuntu0.1
Priority: optional
Section: web
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 86.0k
Depends: apache2-mpm-worker (>= 2.2.3-3.2ubuntu0.1) | apache2-mpm-prefork (>= 2.2.3-3.2ubuntu0.1) |
         apache2-mpm-event (>= 2.2.3-3.2ubuntu0.1)
Provided by: apache2-mpm-event, apache2-mpm-itk, apache2-mpm-prefork, apache2-mpm-worker
Description: Next generation, scalable, extendable web server
 Apache v2 is the next generation of the omnipresent Apache web server. This version - a total rewrite -
 introduces many new improvements, such as threading, a new API, IPv6 support, request/response filtering, and
 more.
```

> Say, I went to that site, but I don't see any package that looks like it will run on Intel Core 2 Duo.you would use i386 for that CPU ... unless it's 64-bit, which would use amd64.

---

### Post by resume-writer on 2007-09-13
That command worked. That was easy. Cool. Thank you!

---

