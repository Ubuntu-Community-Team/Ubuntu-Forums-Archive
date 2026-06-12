---
title: "Edgy &gt; Feisty, MySQL fails to process replacement"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by starkruzr on 2007-05-18
I got this when running apt-get dist-upgrade:

Preparing to replace mysql-client-5.0 5.0.24a-9ubuntu2 (using .../mysql-client-5.0_5.0.38-0ubuntu1_i386.deb) ...
Unpacking replacement mysql-client-5.0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server_5.0.38-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I would post the log, which I would hope would tell me what actually happened, but I can't find it in /var/log or /var/log/dist-upgrade :-|

---

### Post by starkruzr on 2007-05-20
Bump.

Someone who knows what they're doing please pay attention to this?  Pretty please?  :-/

---

### Post by hernan43 on 2007-05-21
If I were in your situation, I would de-install and then re-install the client. Maybe that would work.

---

