---
title: "KPackageKit can't download anything any more"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by TwoBit on 2012-01-19
A year ago I was able to use KPackageKit to download packages, but when I try it today I just get "The package download failed" errors for anything I try to download. My Internet connection is fine. How do I diagnose the problem? The problem "details" text is simply "download failed."

Thanks.

---

### Post by WthIteh on 2012-01-19
Package managers usually download files somewhere in /var/cahce before installing them and a corrupted file there makes them to think the file could not be downloaded.
Take a look at /var/cache/PackageKit to find unusual files (files with size zero) and remove them. Then "update" packages list and try again.

---

### Post by TwoBit on 2012-01-20
There's just a single Downloads folder in /var/cache/PackageKit which is owned by root. Deleting it doesn't solve the problem. I'm starting to think that the problem is that I'm running 9.04 and it's not supported any more and the error message isn't reflecting that.

---

### Post by raja.genupula on 2012-01-20
sudo apt-get update

give me the output of that .

---

