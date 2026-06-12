---
title: "[Solved] File input to apt-get install"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by nbday on 2014-08-30
I'd like to pipe a text file containing the names of packages to install to the apt-get command.  I've read man apt-get and don't see any obvious help there.  "apt-get install < file.txt" doesn't work.

---

### Post by sbnwl on 2014-08-30
Could this work for you
```
*sudo apt*-*get* -s *install* $(cat file.txt)
```

The 'bash' is sometimes useful in this regard!

---

### Post by nbday on 2014-08-30
Thanks!  "sudo apt-get install -y $(cat file.txt)" works perfectly.

---

