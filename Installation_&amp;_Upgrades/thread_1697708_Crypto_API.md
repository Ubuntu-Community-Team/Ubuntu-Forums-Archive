---
title: "Crypto API"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by chrysti on 2011-03-01
Hello,

This is a beginners question ! :)
I open a console and type : ```
cat /proc/crypto
```so I could check the algorithms that are actually embedded into the kernel I use and the only results that I see are the followings :
```
$ cat /proc/crypto 
name         : crc32c
driver       : crc32c-generic
module       : crc32c
priority     : 100
refcnt       : 2
selftest     : passed
type         : shash
blocksize    : 1
digestsize   : 4

name         : stdrng
driver       : krng
module       : kernel
priority     : 200
refcnt       : 1
selftest     : passed
type         : rng
seedsize     : 0

name         : md5
driver       : md5-generic
module       : kernel
priority     : 0
refcnt       : 1
selftest     : passed
type         : shash
blocksize    : 64
digestsize   : 16

```I am using this version of the kernel :
```
$ uname -a
Linux test-pc 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

```I would like to know how I can add more algorithms to the kernel.

Thanks in advance !

---

### Post by gube on 2012-03-09
Bump!

---

### Post by raja.genupula on 2012-03-09
not exact one but help you a bit 
[http://lwn.net/Articles/401548/](http://lwn.net/Articles/401548/)

look foir crypto in this
[http://kernelnewbies.org/LinuxChanges#head-06b2813f8fa50c2552002922ac7d8e48fdad4dbe](http://kernelnewbies.org/LinuxChanges#head-06b2813f8fa50c2552002922ac7d8e48fdad4dbe)

---

