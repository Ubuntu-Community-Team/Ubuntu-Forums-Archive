---
title: "Software sources are messing up my upgrade, I just need someone to walk me through it"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2007-10-20
This is by far the most complicated upgrade I've gone through so far, and I have no idea why.
The people in the #ubuntu channel said to get rid of all third-party sources I have. Well, I'm not exactly an expert on this stuff, and now I'm all lost as to what I have enabled, commented out, etc. AND now I have a ton of updates available, but I don't know if I'm supposed to install them after messing around with my stupid software sources for the past half hour.

This is my sources.list as of now: [http://paste.ubuntu-nl.org/41407/](http://paste.ubuntu-nl.org/41407/)
I have multiverse, universe, and restricted enabled in my Software Sources winidow, along with these reops that I didn't see in my sources.list (so I unchecked them anyway):
> [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
[http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free (Source Code)
[http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
[http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts (Source Code)
WineHQ - Ubuntu 7.04 "Feisty Fawn"
WineHQ - Ubuntu 7.04 "Feisty Fawn" (Source Code)

Please, someone explain to me what I need to do, I'm so LOST.

---

### Post by rainwalker on 2007-10-20
Okay, this is the FOURTH time I've tried to upgrade. The FOURTH time.
I keep getting this error:
> Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz) Bad header line

This is the second time it's given me this error, but if you look in my sources.list, you can clearly see that it is NOT enabled. What's going wrong?!

---

### Post by rainwalker on 2007-10-20
Great.
So I decided to just screw it and upgrade some other time, and I changed everything to how (I thought) it was, and now this is what I get from the update manager: [http://paste.ubuntu-nl.org/41413/](http://paste.ubuntu-nl.org/41413/)
As well as this, something about GPG key: [http://paste.ubuntu-nl.org/41416/](http://paste.ubuntu-nl.org/41416/)

---

### Post by rainwalker on 2007-10-21
Alright, I changed everything back to how it originally was, but now I get this:> Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found
Do I need to re-add the GPG key for the medibuntu repos?

---

