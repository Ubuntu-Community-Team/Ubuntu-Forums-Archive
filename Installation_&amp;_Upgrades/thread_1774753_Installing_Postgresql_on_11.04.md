---
title: "Installing Postgresql on 11.04"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by pv13 on 2011-06-03
Hi all
I am a beginner to Ubuntu. I am trying to install postgres on my system. The software center doesnt have postgres listed. Am I missing something?

Please help!

Thanks so much!

---

### Post by denisk on 2011-06-04
I guess you should do
```
sudo add-apt-repository ppa:pitti/postgresql
```
first ([this]("https://launchpad.net/~pitti/+archive/postgresql") is the original repository page), then follow [this guide]("https://help.ubuntu.com/community/PostgreSQL"). Note that 8.4 version mentioned there is quite old, you might opt for 9.0 instead

---

