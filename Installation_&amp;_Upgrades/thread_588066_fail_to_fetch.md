---
title: "fail to fetch"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by wademunkey on 2007-10-23
I am trying to update to 7.10 from 7.04.   I am using the automatic update.  It gets the application, then stats downloading.  I am not sure how complete it is since the bar keeps starting over, but I get the message that 5 files are being failed to fetch and the update shuts itself down after giving me the error.  I have uninstalled automatix, and changed my server to the computer chosen fastest.  
Here is what the error says.
Failed to fetch [http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/Release.gpg](http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/Release.gpg) Could not resolve 'mtfs-3gsitesweetsite.info'
Failed to fetch [http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2) Could not resolve 'mtfs-3gsitesweetsite.info'
Failed to fetch [http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/main-all/i18n/Translation-en_US.bz2](http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/main-all/i18n/Translation-en_US.bz2) Could not resolve 'mtfs-3gsitesweetsite.info'
Failed to fetch [http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) Could not resolve 'mtfs-3gsitesweetsite.info'
Failed to fetch [http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://mtfs-3gsitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) Could not resolve 'mtfs-3gsitesweetsite.info'
I am at a loss as to what to do.
I have also checked that my computer is up to date, and I am mostly up to date, but 4 or 5 files cannot be downloaded. I can get this exact message if it will help.  
I am new to linux programming, but would love to learn, so send me anything you think might help.
thanks
Andrew

---

### Post by jonno on 2007-10-23
This is a more relevant thread than the previous one I posted in. Sorry for the duplication.

I have a very similar problem but with the following errors:
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found

Internet works fine. Everything else is updated. Any ideas?

---

### Post by Pete Kingston on 2007-10-23
I have the exact same issue....

---

### Post by Pete Kingston on 2007-10-24
I got it to upgrade. 

You also need to disable offending source in System, Administration, Software Sources, Third-Party Software tab, un-check the items that are stopping your upgrade, and then try again.

---

### Post by wademunkey on 2007-10-24
pete's tip worked perfectly
thanks
Yall

---

