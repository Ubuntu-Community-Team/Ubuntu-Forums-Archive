---
title: "Ubuntu 16.04 za.archive upgrade error"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by DanieW on 2016-04-26
I have a local upgrade error to 16.04 that terminated the upgrade process from version 15.10 4.2.0-35-generic Mar 15 22:15:45 x86_64, Wily Werewolf

A "Not Found [IP:197.155.77.2 80]" error on the za.archive.ubuntu.com domain I seem to have **not resolved by including the corresponding uk.archive.ubuntu.com **domain for [B]xenial universe. I now also have Connection failed [IP: 91.189.88.149 80]

[/B]I saw errors on [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) for xenial/universe Sources
i.e. for:
 - > Error during update

 - > W:Failed to fetch
 - > [http://za.archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-amd64/Packages/](http://za.archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-amd64/Packages/) 
 - > 404 Not Found []
I found that I can find Packages.gz and Packages.xz at these locations. (Just not unpacked)

And similarly for
[http://za.archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-i386/Packages/](http://za.archive.ubuntu.com/ubuntu/dists/xenial/universe/binary-i386/Packages/) 
there are actually Packages.gz and Packages.xz

And similarly for
[http://za.archive.ubuntu.com/ubuntu/dists/xenial/universe/source/Sources/](http://za.archive.ubuntu.com/ubuntu/dists/xenial/universe/source/Sources/) 
there are actually Sources.gz and Sources.xz

[New edit]
Despite above, the latest attempt has proceeded without a hitch.
  - i.e. Resolved.:)

---

