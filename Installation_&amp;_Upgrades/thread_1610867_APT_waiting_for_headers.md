---
title: "APT waiting for headers"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by artie_effim on 2010-11-01
When doing apt updates and upgrades I found that I was getting  "Waiting for headers" errors.  In all cases I was behind a proxy, but one that did not require authentication.  Looking around I found this page: [http://muffinresearch.co.uk/archives/2010/03/30/linux-fix-for-apt-get-update-waiting-for-headers/](http://muffinresearch.co.uk/archives/2010/03/30/linux-fix-for-apt-get-update-waiting-for-headers/) which helped for me.

tl;dr

echo 'Acquire::http::Pipeline-Depth "0";' >> /etc/apt/apt.conf.d/99http

[edit] - disabled smilies ;p

---

