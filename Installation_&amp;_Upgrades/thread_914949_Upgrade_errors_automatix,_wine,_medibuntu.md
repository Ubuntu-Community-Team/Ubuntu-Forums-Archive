---
title: "Upgrade errors: automatix, wine, medibuntu"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by jordan28 on 2008-09-09
Hello, I'm trying to upgrade from fiesty to gutsy. I'd like to eventually come up to speed with hardy or intrepid. Through update manager I get the following failed-to-fetch errors:

> 
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg)  Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2)  Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz)  Could not resolve 'wine.lowvoice.nl'

I've tried to uninstall medibuntu and automatix through synaptic. And my browser won't connect to wine.lowvoice.nl - How can I work around this to proceed with my upgrade?  Thanks

---

### Post by cdtech on 2008-09-09
Try a different server in your "System > Administrator > Software sources"

---

### Post by jordan28 on 2008-09-09
I've tried one from within my own country, a NL server, and the default U.S. Server. Should I try somewhere else?

---

