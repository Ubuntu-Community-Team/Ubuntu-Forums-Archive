---
title: "apt-get update exits with error"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by meeiw on 2005-10-16
I have done an upgrade from hoary to breeze with apt-get dist-upgrade. apt-get is giving me some error though when i try to run apt-get update. The packages gets downloaded and installed but when the packages are getting configured,  I get the following error:

... (omissions)
 
```
Configure openssl (0.9.7g-1ubuntu1.1) ...

Error was found when handeling:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
(I have translated the error messages from swedish to english ;) )

---

