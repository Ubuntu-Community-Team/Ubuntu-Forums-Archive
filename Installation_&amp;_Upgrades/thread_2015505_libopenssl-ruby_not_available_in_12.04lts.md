---
title: "libopenssl-ruby not available in 12.04lts?"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by swduncan on 2012-07-03
I'm trying to get passenger running, and it's telling me to install libopenssl-ruby, but when I try to do that apt-get tells me:


Note, selecting 'libruby' instead of 'libopenssl-ruby'


I've edited sources.list to uncomment repositories, but still no go. Also did apt-get update as well. 

Any ideas on where to find libopenssl-ruby for 12.04 and how to get it installed?

---

### Post by thiago.project on 2012-08-01
Have you uncommented the "universe" source repositories?

It should be something like this, in your /etc/apt/sources.list file:

```

deb http://www.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://www.archive.ubuntu.com/ubuntu/ precise universe
deb http://www.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://www.archive.ubuntu.com/ubuntu/ precise-updates universe

```

Be sure to update your cache again, by doing an apt-get update, then try to install the package one more time.

---

