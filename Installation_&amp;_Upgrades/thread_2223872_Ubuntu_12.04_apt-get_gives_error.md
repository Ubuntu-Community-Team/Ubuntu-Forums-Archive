---
title: "Ubuntu 12.04: apt-get gives error"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by tbeck on 2014-05-13
Dear all,

I have some troubles with apt-get. Somehow after updating, sudo apt-get update gives me the following errors:

```

......
Ign http://gb.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://gb.archive.ubuntu.com quantal-updates/universe Translation-en_US
W: Failed to fetch http://ppa.launchpad.net/mok0/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mok0/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mok0/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

I have tried to comment out most of the lines in /etc/apt/sources.list, but that makes no difference.

Any idea what the error could indicate?

Thanks, Tobias.

---

### Post by grahammechanical on 2014-05-13
You need to remove that PPA from your software sources list. If software Updater still has the PPA listed as a software source or repository it may be overwriting any changes that you make by editing the sources.list file directly. I have also noticed that when we edit system files then Gedit will make a backup copy with the same name but with a tilde ( ~ ) character added which makes the file a hidden file. I have also noticed that these backup copies may still be read by the OS and so preventing any edited changes from taking effect.

By the way, Ubuntu 12.10 is about to reach end of life (16th). I know that your thread title says 12.04 but you have as a repository quantal-updates which is 12.10. If you really are using 12.04 then you should not have that repository there either. It will cause other updating problems within a few weeks. On the other hand if it is 12.10 that you are using then think seriously about upgrading to 14.04 by doing a fresh install. Ubuntu 13.04 is out of life already and Ubuntu 13.10 will become out of life by the end of July 2014. A fresh install will avoid a complicated upgrade path to 14.04.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Regards.

Regards.

---

