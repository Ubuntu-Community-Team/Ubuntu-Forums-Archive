---
title: "apt-get update fails for trusty"
date: 2014-05-16
forum: Installation &amp; Upgrades
---

### Post by andrea31 on 2014-05-16
Hi there,

something strange happened here. I installed a new server and, when I try to install new software using apt-get (also using apt-get update) I get this error message:

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
[.....]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

I didn't change anything on apt source.list and I'm able to reach the WAN (I can download some software). 

Any suggestion? It's a really issue for me and I'm blocked! 

thanks,
Andrea

--- UPDATE ---
the problem was related to the proxy configuration.

---

