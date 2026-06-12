---
title: "getting this error"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by saurabh_nnegi on 2010-08-19
"W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)"

Any feedback for this error.....

---

### Post by plucky on 2010-08-19
> **saurabh_nnegi said:**
> "W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)"

Any feedback for this error.....

Post output from a terminal window for ```
cat /etc/apt/sources.list
```

The problem is that you have two entries in your sources.list for the **partner** repository.

---

