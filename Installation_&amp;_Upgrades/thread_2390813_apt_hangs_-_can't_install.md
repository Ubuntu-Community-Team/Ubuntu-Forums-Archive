---
title: "apt hangs - can't install"
date: 2018-05-02
forum: Installation &amp; Upgrades
---

### Post by Coriander Redgoat on 2018-05-02
I'm on 16.04

apt hangs. For instance:

```
Need to get 75.9 kB/3,080 kB of archives.After this operation, 14.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
86% [Connecting to us.archive.ubuntu.com (2001:67c:1562::19)]
```

It just hangs there and does nothing.

What's happening? How do I fix it?

---

### Post by Coriander Redgoat on 2018-05-02
apt update did seem to go through eventually and gave this at the end:

```
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:50 and /etc/apt/sources.list.d/xenial-partner.list:4



```

Thanks!

---

