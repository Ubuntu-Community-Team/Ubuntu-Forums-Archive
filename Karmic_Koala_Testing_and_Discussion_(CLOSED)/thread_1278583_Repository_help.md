---
title: "Repository help"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-29
I found a bunch of repos from [http://ubuntuforums.org/showthread.php?p=5469046](http://ubuntuforums.org/showthread.php?p=5469046), but when I try and imput them (clicking on each for karmic, I get GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8Failed to fetch [http://ppa.launchpad.net/bruce89/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/bruce89/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mozillateam/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/thielmann/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/thielmann/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Arent they all for Karmic if I edit them to Karmic?

---

### Post by qwerty800 on 2009-09-29
```
GPG error: http://ppa.launchpad.net karmic
Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6GPG
error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
Failed to fetch http://ppa.launchpad.net/bruce89/ppa...86/Packages.gz 404 Not Found
Failed to fetch http://ppa.launchpad.net/mozillateam...86/Packages.gz 404 Not Found
Failed to fetch http://ppa.launchpad.net/openoffice-...86/Packages.gz 404 Not Found
Failed to fetch http://ppa.launchpad.net/thielmann/p...86/Packages.gz 404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```
For the public key, this is not of a big deal.
You can still download the packages, but you may not want to trust them, since they aren't signed.

And for the package not founds, verify your package sources.

---

### Post by sports fan Matt on 2009-09-29
Actually even though irs not a big deal, it has disabled updating in karmic because of that mesaage..I seem to recall an easy way to insert keys without trying to hunt for the signatures..Does something like this exist?

---

### Post by DougieFresh4U on 2009-09-29
> **sox fan Matt said:**
> Actually even though irs not a big deal, it has disabled updating in karmic because of that mesaage..I seem to recall an easy way to insert keys without trying to hunt for the signatures..Does something like this exist?
Here ya go

[http://d0od.blogspot.com/2009/09/automatically-install-missing-ppa-gpg.html](http://d0od.blogspot.com/2009/09/automatically-install-missing-ppa-gpg.html)

---

### Post by sports fan Matt on 2009-09-29
Thanks dougie but it still threw up the errors even running through that webpage...W:Failed to fetch [http://ppa.launchpad.net/bruce89/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/bruce89/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/thielmann/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/thielmann/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by DougieFresh4U on 2009-09-29
> **sox fan Matt said:**
> Thanks dougie but it still threw up the errors even running through that webpage..
Sorry. Seems that your problem is not key related. I have the mozilla repo and no problem with it

---

