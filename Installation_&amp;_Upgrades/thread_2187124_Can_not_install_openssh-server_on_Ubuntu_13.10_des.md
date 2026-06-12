---
title: "Can not install openssh-server on Ubuntu 13.10 desktop"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by rawender.guron on 2013-11-10
I downloaded and installed Ubuntu 13.10 desktop on my PC. When I try to install openssh-server, it does not work. It does not show up in Ubuntu Software Centre and it fails with message 'Package openssh-server is not available' when I run 'sudo apt-get install openssh-server' from command line. Can you please help as to what I need to do to get this installed.

Thanks
Rawender

---

### Post by deadflowr on 2013-11-10
What is the output for
```
sudo apt-get update
```

Any errors?

---

### Post by rawender.guron on 2013-11-10
I got it working, thanks. Your suggestion prompted me to enter proxy userid/password to /etc/apt.conf and that resolved the problem.

Thanks again
Raweder

---

