---
title: "Package autoconf has no installation candidate"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by ale88.. on 2010-03-13
When I run the command:
 
"sudo apt-get install build essential autconf automake libxmu -dev"
 
I go the following error:
 
"E: Package autoconf has no installation candidate"
 
In the cd-rom there is no any autconf package, so I don't know how to solve this problem. Any idea?
 
Thanks!

---

### Post by Enigmapond on 2010-03-13
That's probably because there is no package "autconf" but there IS an "autoconf"...might this be the issue??

[http://packages.ubuntu.com/search?suite=karmic&section=all&arch=any&searchon=names&keywords=autoconf](http://packages.ubuntu.com/search?suite=karmic&section=all&arch=any&searchon=names&keywords=autoconf)

---

