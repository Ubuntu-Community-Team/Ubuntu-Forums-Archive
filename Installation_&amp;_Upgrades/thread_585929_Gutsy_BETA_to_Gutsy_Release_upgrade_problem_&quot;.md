---
title: "Gutsy BETA to Gutsy Release upgrade problem &quot;Failed to fetch&quot;"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Kalrog on 2007-10-21
I have been trying to get my PC to upgrade from the Beta version of Gutsy that I have been using for the past 2+ months (since Alpha) to the released version and am having some problems.  Every time I go into Adept and fetch updates, it mentions that there is an upgrade available, but every time I try to perform that upgrade I get the same error message: "Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release](http://archive.canonical.com/ubuntu/dists/gutsy/Release) Unable to find expected entry commercial/binary-amd64/Packages in Meta-index file (malformed Release file?)"

I have done some searching and found that some sources information might need to be updated, but nothing I have tried has improved the situation.  I have opened a but on this, but haven't gotten any response on that one.

Relevant information: Kubuntu 7.10 (Gutsy Gibbon beta) AMD 64 version.

I'll supply other information as requested.  Thanks!

---

### Post by Kalrog on 2007-10-22
*bump*

Searching hasn't revealed anything else with a "failed to fetch" error (at least to my ignorant eyes).  Anyone have any ideas?  Even WAGs at this point would be helpful.

---

### Post by TNakos on 2007-10-22
I dont even have the option to upgrade.... bump:confused:

---

### Post by Kalrog on 2007-10-22
> **TNakos said:**
> I dont even have the option to upgrade.... bump:confused:

This one I might be able to help with.  When you go into Adept and fetch updates, do you then have an upgrade option at the top (far right)?

---

### Post by Seisen on 2007-10-22
Here is the official way to update Kubuntu

[https://help.ubuntu.com/community/GutsyUpgrades?highlight=%28gutsy%29%7C%28upgrade%29]("https://help.ubuntu.com/community/GutsyUpgrades?highlight=%28gutsy%29%7C%28upgrade%29")

---

### Post by Kalrog on 2007-10-22
I followed those directions exactly... Still failed.

---

### Post by jonno on 2007-10-23
Trying to upgrade from Feisty to Gutsy and I get the following:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found

Internet works great. Any ideas?

---

### Post by L115A1 on 2007-10-23
I'm having a similar problem too. 

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

If anyone has any solutions please feel free to share.

Thanks.

---

### Post by Kalrog on 2007-10-23
> **L115A1 said:**
> I'm having a similar problem too. 

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

If anyone has any solutions please feel free to share.

Thanks.

Can you ping wine.lowvoice.nl ?

---

### Post by Kalrog on 2007-10-23
> **jonno said:**
> Trying to upgrade from Feisty to Gutsy and I get the following:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found

Internet works great. Any ideas?

Something moved on you.  Did you manually add the sos-sts.com repos?  The 404 errors simply mean that the sources.gz and packages.gz files aren't at that path.

---

