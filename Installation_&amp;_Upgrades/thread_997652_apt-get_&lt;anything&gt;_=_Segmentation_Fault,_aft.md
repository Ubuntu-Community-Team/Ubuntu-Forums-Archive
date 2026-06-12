---
title: "apt-get &lt;anything&gt; = Segmentation Fault, after new install"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by SqueakyDog on 2008-11-30
Fresh install of 8.10 Server.  Output from /var/log/messages:

apt-get[6963] general protection ip:7f4a56611eb0 sp:7fff5e8265f0 error:0 in ld-2.8.90.so[7f4a5660a000+1f000]

I've deleted the /var/cache/apt files

Not sure how to proceed?

---

### Post by SqueakyDog on 2008-12-01
I did a MemTest86+ and got errors, reseated the ram module and re-installed.  This was the issue.

---

