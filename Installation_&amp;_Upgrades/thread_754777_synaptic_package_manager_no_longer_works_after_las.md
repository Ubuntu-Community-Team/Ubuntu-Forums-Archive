---
title: "synaptic package manager no longer works after last gutsy update"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by jazz612 on 2008-04-14
since the gutsy updates on 11 april or thereabouts i've been getting the following error messages when i try to install/reinstall packages, for example:

E: /var/cache/apt/archives/liblink-grammar4_4.2.2-4ubuntu0.7.10.1_i386.deb: Verification on package /var/cache/apt/archives/liblink-grammar4_4.2.2-4ubuntu0.7.10.1_i386.deb failed!
E: /var/cache/apt/archives/liblockfile1_1.06.2_i386.deb: Verification on package /var/cache/apt/archives/liblockfile1_1.06.2_i386.deb failed!
E: /var/cache/apt/archives/libversion-perl_1%3a0.7203-1_i386.deb: Verification on package /var/cache/apt/archives/libversion-perl_1%3a0.7203-1_i386.deb failed!
E: /var/cache/apt/archives/libnetaddr-ip-perl_4.007+dfsg-1_i386.deb: Verification on package /var/cache/apt/archives/libnetaddr-ip-perl_4.007+dfsg-1_i386.deb failed!
E: /var/cache/apt/archives/libnet-ip-perl_1.25-2_all.deb: Verification on package /var/cache/apt/archives/libnet-ip-perl_1.25-2_all.deb failed!
E: /var/cache/apt/archives/libnet-dns-perl_0.60-1ubuntu0.1_i386.deb: Verification on package /var/cache/apt/archives/libnet-dns-perl_0.60-1ubuntu0.1_i386.deb failed!
E: /var/cache/apt/archives/libmail-spf-perl_2.005-0ubuntu1_all.deb: Verification on package /var/cache/apt/archives/libmail-spf-perl_2.005-0ubuntu1_all.deb failed!
E: /var/cache/apt/archives/libneon25_0.25.5.dfsg-6build1_i386.deb: Verification on package /var/cache/apt/archives/libneon25_0.25.5.dfsg-6build1_i386.deb failed!
E: /var/cache/apt/archives/libogg-vorbis-header-perl_0.03-1_i386.deb: Verification on package /var/cache/apt/archives/libogg-vorbis-header-perl_0.03-1_i386.deb failed!
E: /var/cache/apt/archives/libsmokeqt1_4%3a3.5.7-1ubuntu4_i386.deb: Verification on package /var/cache/apt/archives/libsmokeqt1_4%3a3.5.7-1ubuntu4_i386.deb failed!
E: /var/cache/apt/archives/libqt0-ruby1.8_4%3a3.5.7-1ubuntu4_i386.deb: Verification on package /var/cache/apt/archives/libqt0-ruby1.8_4%3a3.5.7-1ubuntu4_i386.deb failed!
E: /var/cache/apt/archives/libraw1394-dev_1.2.1-3build1_i386.deb: Verification on package /var/cache/apt/archives/libraw1394-dev_1.2.1-3build1_i386.deb failed!

what is wrong?  or should i simply reinstall synaptic package manager using root privileges in terminal?  thanks!

---

### Post by Michael.Godawski on 2008-04-14
What happens if you run these commands in terminal, they should reconfigure broken and half installed packages:

```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

