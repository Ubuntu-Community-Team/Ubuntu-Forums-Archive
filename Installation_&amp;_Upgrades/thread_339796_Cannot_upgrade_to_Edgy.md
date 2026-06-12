---
title: "Cannot upgrade to Edgy"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by PaulFXH on 2007-01-16
Hi
I've been trying for nearly a week now but my upgrade attempts (dapper to edgy) have all failed, apparently due to inability to connect to the website [http://antesis.freecontrib.org](http://antesis.freecontrib.org) which appears in my sources list.

The errors I get are as follows:

>  Could not download all repository indexes

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.***.***). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.***.***). - connect (111 Connection refused)  

and

>  Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg) Could not connect to antesis.freecontrib.org:80 (213.251.***.***). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg) Could not connect to antesis.freecontrib.org:80 (213.251.***.***). - connect (111 Connection refused)  

Note that I do NOT have any network problem but the website mentioned is unreachable from a range of browsers either in IE7 or FF.

I believe that I may need to change my sources list but would appreciate getting confirmation on this (and anything else that might be of assistance to me in this regard) from somebody more conversant on these matters before going ahead.

Paul

---

### Post by taurus on 2007-01-16
Put a # in front of those third party repos in /etc/apt/sources.list before you try to upgrade to Edgy.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by PaulFXH on 2007-01-16
Taurus
That seems to have done the trick and I'm just about to start the upgrade.
Many thanks
Paul

---

