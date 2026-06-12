---
title: "an unexpected problem in updating!"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by iceman_sean on 2008-05-17
every time i try to update my ubuntu 8.04, a disgusting problem 'll come up. could anyone tell me what the bloody hell it is?

~@~:sudo apt-get update
......................
......................
......................
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/sarge/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/sarge/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/sarge/main/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/sid/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/sid/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/sid/main/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/etch/main/binary-i386/Packages.gz: No such file or directory  '
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Bubba64 on 2008-05-17
> **iceman_sean said:**
> every time i try to update my ubuntu 8.04, a disgusting problem 'll come up. could anyone tell me what the bloody hell it is?

~@~:sudo apt-get update
......................
......................
......................
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/sarge/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/sarge/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/sarge/main/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/sid/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/sid/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/sid/main/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/etch/main/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian-marillat/dists/etch/main/binary-i386/Packages.gz: No such file or directory  '
Some index files failed to download, they have been ignored, or old ones used instead.

Have you gone into software sources via administrative or synaptic to make sure what repositories you want are ticked and that you have the key to any that are shown in 3rd party.

---

### Post by NightwishFan on 2008-05-17
Make sure the hardy cd option is unchecked as well, also perhaps change to another server. There is an autoconfig to find the fastest one under software sources.

---

### Post by akudewan on 2008-05-17
Hi,

You have 3rd party repositories. Remove these before upgrading.

A word of advice: Using stuff like the Opera browser repository is OK, because it gives you only one package: Opera. On the other hand, including a Debian repository is bound to give you conflicts while upgrading. You'll almost certainly end up with a broken system after the upgrade, if you've been using this repository regularly. I would recommend a fresh install instead of an upgrade.

---

### Post by zvacet on 2008-05-17
Remove all that repos from your source list.You don´t want to have mixed repos.If you want Opera download it from their site and pick Opera 9.5 beta,because that one doesn´t have problems with flash.

---

### Post by iceman_sean on 2008-05-17
hi, Bubba64, NightwishFan, akudewan, zvacet, thank u all!
i removed all third - party software from software sources and it seems working now. cheers!

---

### Post by NightwishFan on 2008-05-17
Great glad we could help. Until next time.

---

