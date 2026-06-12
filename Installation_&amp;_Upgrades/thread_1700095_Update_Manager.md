---
title: "Update Manager"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Linux35 on 2011-03-04
I get this message when I run it

W:Failed to fetch [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

There is nothing wrong with my connection.  Anybody know?

---

### Post by Frogs Hair on 2011-03-04
Hi and Welcome,

Go to Accessories > Terminal and run```
sudo apt-get update
``` You may have to run it more than once before you connect to your sources. When you can run this with no errors , try the update manager again.

---

### Post by coffeecat on 2011-03-04
> **Linux35 said:**
> I get this message when I run it

```
W:Failed to fetch [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

You have a malformed URL to the PPA you're trying to download from. That probably should be:

```
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/maverick/main/source/Sources.gz]("http://ppa.launchpad.net/ubuntu-win/ppa/ubuntu/dists/maverick/main/source/Sources.gz")
```ubuntu-wine, not ubuntu-win. Ditto for the second one. How did you add that PPA?

---

