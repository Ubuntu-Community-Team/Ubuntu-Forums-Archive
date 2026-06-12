---
title: "update and new software will not install"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by stuart221 on 2008-07-22
When ever I go to update or install software I get the following massage
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Cheershttp://ubuntuforums.org/images/icons/icon7.gif

---

### Post by iaculallad on 2008-07-22
> **stuart221 said:**
> When ever I go to update or install software I get the following massage
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Cheershttp://ubuntuforums.org/images/icons/icon7.gif

Open your terminal and input the command below as the message says:

```
sudo dpkg --configure -a
```

---

