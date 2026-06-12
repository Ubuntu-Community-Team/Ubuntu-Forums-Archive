---
title: "error in /usr/bin directory"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by sijran on 2010-09-06
I cannot find dpkg directory in /usr/bin folder and while installing mysql server it gives the following error 
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Please how can I install phpmyadmin too in such conditions.

---

### Post by aysiu on 2010-09-07
What happens when you paste in this? ```
sudo apt-get -f install
```

---

