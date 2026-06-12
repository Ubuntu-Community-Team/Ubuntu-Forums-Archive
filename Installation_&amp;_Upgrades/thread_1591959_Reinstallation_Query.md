---
title: "Reinstallation Query"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by mkris23 on 2010-10-10
I'm presently running 10.04 32 bit on my Core 2 Duo. I thought i'll install the 64 bit version once 10.10 comes out. I've made two partitions (excluding swap) with / on a 10gb partition and /home mounted on the rest of the space. My doubt is, when i reinstall in such a manner, will the configartion files for most of my applcations remain the same,, or will they change?? what exactly do i need to back up to ensure that my transition is without any problems??

thanks in advance

---

### Post by CharlesA on 2010-10-10
1) Backup.
2) Backup.
3) Backup.
4) Read the release notes
5) Boot off a livecd to check compability
6) Install and select "advanced partitioning" during installation and choose not to format the current /home

But yeah, just backup the entire /home directory and you should be ok backup wise.

As for conf files changing, I suppose it really depends on the application.

---

