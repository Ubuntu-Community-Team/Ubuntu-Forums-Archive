---
title: "Gutsy update problem: libc6_2.6.1-1 (Segmentation fault)"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by charming-butcher on 2007-09-15
I have problems updating libc6/feisty to libc6/gutsy. Also if I use apt-get I get the following error message:

```

root@idea:/home/usr/Desktop dpkg -i /var/cache/apt/archives/libc6_2.6.1-1ubuntu4_amd64.deb

(Reading database ... 244960 files and directories currently installed.)
Preparing to replace libc6 2.5-0ubuntu14 (using .../libc6_2.6.1-1ubuntu4_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.6.1-1ubuntu4_amd64.deb (--install):
 dpkg: warning - old post-removal script killed by signal (Segmentation fault)

dpkg: error while cleaning up:
 subprocess pre-installation script killed by signal (Segmentation fault)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.6.1-1ubuntu4_amd64.deb
root@idea:/home/usr/Desktop dpkg -i /var/cache/apt/archives/libc6_2.6.1-1ubuntu4_amd64.deb
(Reading database ... 244960 files and directories currently installed.)
Preparing to replace libc6 2.5-0ubuntu14 (using .../libc6_2.6.1-1ubuntu4_amd64.deb) ...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.6.1-1ubuntu4_amd64.deb (--install):
 dpkg: warning - old post-removal script killed by signal (Segmentation fault)

dpkg: error while cleaning up:
 subprocess pre-installation script killed by signal (Segmentation fault)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.6.1-1ubuntu4_amd64.deb

```


Is there a way to install libc6/gutsy?

---

