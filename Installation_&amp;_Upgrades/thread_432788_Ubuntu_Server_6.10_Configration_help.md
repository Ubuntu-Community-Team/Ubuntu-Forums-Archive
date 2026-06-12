---
title: "Ubuntu Server 6.10 Configration help"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by Dave_57204 on 2007-05-04
Hello, I am new to Linux, and I am currently at school working on this project, We have to build a Linux server. Now we got it built and Ubuntu Server 6.10 installed. So now I need to know how to set it up so our windows computers and connect to it. Any help is greatly appreciated.

---

### Post by ohgod on 2007-05-04
Are you looking to share files with the Ubuntu box?  If so, install samba & swat (there are some good howtos on this site).

To remotely administer it via ssh, you'll need to install openssh-server like so:
```

sudo apt-get install openssh-server

```

---

