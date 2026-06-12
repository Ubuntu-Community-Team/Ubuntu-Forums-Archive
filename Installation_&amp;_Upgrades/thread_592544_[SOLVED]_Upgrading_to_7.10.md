---
title: "[SOLVED] Upgrading to 7.10"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by 1205919 on 2007-10-26
Im trying to upgrade to Ubuntu 7.10 (from 7.04), the distr. upgrade runs fine (seemingly) almost through the first step (preparing the upgrade), then fails with the following error:

**Error during update**

A problem occured during the update. This is usually some sort of network problem, please check your network connection an retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_ZA.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_ZA.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


My network connection seems fine as I connect to the www and download mails without any prob

Please help

---

### Post by Mark Phelps on 2007-10-26
Not an expert -- but can see a couple of problems here.  First, you're upgrading to Gutsy, so why are you going to Feisty locations to get stuff? Second, none of the links worked for me -- all gave me Not Found errors.  So, maybe the links got replaced with Gutsy links, instead.  Suggest you check the Wine site.

---

### Post by 1205919 on 2007-10-26
Might sound foolish as I dont know that much, but the upgrade go to those sites on its own, theres no input from my side at all, so I dont know how to prevent it to go look for those

---

### Post by Fire_Chief on 2007-10-26
I had a somewhat similar error while trying to upgrade my system from Feisty to Gusty. I checked the Software Sources to make sure there were not any third party repositories listed (I had one in there which was the same as the one causing the error). The installer should warn you that those repositories will be removed automatically but still...doesn't hurt to check.

---

### Post by Eddie Wilson on 2007-10-26
I tried an online update to Gusty and the upgrade would not finish. This was due to server problems. What I did was to download the alt. cd. That way I was able to upgrade and not lose anything. I had a few minor things to fix but I expected that. Overall the upgrade went very well. Don't forget to backup important data. Good luck.
Eddie

---

### Post by Vencislago on 2007-10-26
I'm facing almost the same problem here.

```
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz 404 Not Found
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz 404 Not Found

```

I'll try it later or wait for the CD.

---

