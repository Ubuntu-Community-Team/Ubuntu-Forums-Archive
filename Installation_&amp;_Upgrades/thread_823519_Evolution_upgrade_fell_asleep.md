---
title: "Evolution upgrade fell asleep"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by oygle on 2008-06-09
There were 3 updates today, all for evolution. It downloaded the files okay, then the update just sat there, for over 30 minutes. As the longest update has been about 5 mins, I cancelled it with a Ctrl-C.  Here is the log 

> 
2008-06-09 22:13:01 startup archives unpack
2008-06-09 22:13:13 upgrade evolution 2.12.1-0ubuntu1.1 2.12.1-0ubuntu1.3
2008-06-09 22:13:13 status half-configured evolution 2.12.1-0ubuntu1.1
2008-06-09 22:13:53 status unpacked evolution 2.12.1-0ubuntu1.1
2008-06-09 22:13:54 status half-installed evolution 2.12.1-0ubuntu1.1
2008-06-09 22:13:57 status half-installed evolution 2.12.1-0ubuntu1.1
2008-06-09 22:14:00 status unpacked evolution 2.12.1-0ubuntu1.3
2008-06-09 22:14:00 status unpacked evolution 2.12.1-0ubuntu1.3
2008-06-09 22:14:01 upgrade evolution-common 2.12.1-0ubuntu1.1 2.12.1-0ubuntu1.3
2008-06-09 22:14:01 status half-configured evolution-common 2.12.1-0ubuntu1.1
2008-06-09 22:14:01 status unpacked evolution-common 2.12.1-0ubuntu1.1
2008-06-09 22:14:01 status half-installed evolution-common 2.12.1-0ubuntu1.1
2008-06-09 22:14:08 status half-installed evolution-common 2.12.1-0ubuntu1.1
2008-06-09 22:14:09 status unpacked evolution-common 2.12.1-0ubuntu1.3
2008-06-09 22:14:09 status unpacked evolution-common 2.12.1-0ubuntu1.3
2008-06-09 22:14:10 upgrade evolution-plugins 2.12.1-0ubuntu1.1 2.12.1-0ubuntu1.3
2008-06-09 22:14:10 status half-configured evolution-plugins 2.12.1-0ubuntu1.1
2008-06-09 22:14:10 status unpacked evolution-plugins 2.12.1-0ubuntu1.1
2008-06-09 22:14:10 status half-installed evolution-plugins 2.12.1-0ubuntu1.1
2008-06-09 22:14:10 status half-installed evolution-plugins 2.12.1-0ubuntu1.1
2008-06-09 22:14:10 status unpacked evolution-plugins 2.12.1-0ubuntu1.3
2008-06-09 22:14:10 status unpacked evolution-plugins 2.12.1-0ubuntu1.3
2008-06-09 22:14:13 startup packages configure
2008-06-09 22:14:13 configure evolution-common 2.12.1-0ubuntu1.3 2.12.1-0ubuntu1.3
2008-06-09 22:14:13 status unpacked evolution-common 2.12.1-0ubuntu1.3
2008-06-09 22:14:13 status half-configured evolution-common 2.12.1-0ubuntu1.3
2008-06-09 22:32:17 startup packages configure
2008-06-09 22:32:17 configure evolution-common 2.12.1-0ubuntu1.3 2.12.1-0ubuntu1.3
2008-06-09 22:32:17 status half-configured evolution-common 2.12.1-0ubuntu1.3
2008-06-09 22:37:05 status installed evolution-common 2.12.1-0ubuntu1.3
2008-06-09 22:37:05 configure evolution 2.12.1-0ubuntu1.3 2.12.1-0ubuntu1.3
2008-06-09 22:37:05 status unpacked evolution 2.12.1-0ubuntu1.3
2008-06-09 22:37:05 status unpacked evolution 2.12.1-0ubuntu1.3
2008-06-09 22:37:05 status half-configured evolution 2.12.1-0ubuntu1.3
2008-06-09 22:37:44 status installed evolution 2.12.1-0ubuntu1.3
2008-06-09 22:37:44 configure evolution-plugins 2.12.1-0ubuntu1.3 2.12.1-0ubuntu1.3
2008-06-09 22:37:44 status unpacked evolution-plugins 2.12.1-0ubuntu1.3
2008-06-09 22:37:44 status half-configured evolution-plugins 2.12.1-0ubuntu1.3
2008-06-09 22:37:44 status installed evolution-plugins 2.12.1-0ubuntu1.3


Where it hung was on the plugins, it just sat there for a very long time. I don't actually use Evolution, but may use it in the future, I simply installed it sometime ago, to view the features.

---

### Post by dstew on 2008-06-09
It looks like it finished OK. The last message says "status installed evolution-plugins". Maybe the install script just did not exit. Does Evolution work?

---

### Post by oygle on 2008-06-09
Yes, Evolution works. Must have been like you stated, the script just didn't exit, for some reason.

Thanks !!

---

