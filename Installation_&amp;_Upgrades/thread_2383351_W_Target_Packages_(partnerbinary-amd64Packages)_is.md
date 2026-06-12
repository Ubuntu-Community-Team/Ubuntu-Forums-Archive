---
title: "W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in"
date: 2018-01-23
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2018-01-23
I have somehow gotten into the following situation with Ubuntu 16.04 just doing normal upgrades.

```
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:37 and /etc/apt/sources.list.d/xenial-partner.list:4
```

How do I get out of this problem?

Thank you, John

---

### Post by deadflowr on 2018-01-23
Looks like you have the same entry for Canonical Partners in both the main /etc/apt/sources.list file and in a secondary file /etc/apt/sources.list.d/xenial-partner.list file.
You need to either remove one of entries (perhaps by deleting the xenial-partners.list file) or see if one can be removed through the Software and Updates program.
In Software and Updates (also known as software sources) in the Other Software tab, it may show double entries for Canonical Partners (not source code), if it does you should be able to simply disable or remove one of them.

---

### Post by cigtoxdoc on 2018-01-24
Thank you for your help.  Removing the xenial-partners.list file solved the problem.

John

---

