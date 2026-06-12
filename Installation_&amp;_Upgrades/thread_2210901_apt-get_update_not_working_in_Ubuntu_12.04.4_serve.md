---
title: "apt-get update not working in Ubuntu 12.04.4 server"
date: 2014-03-13
forum: Installation &amp; Upgrades
---

### Post by akash4 on 2014-03-13
[SIZE=4]**sudo apt-get update**[/SIZE] gives the following error:

[SIZE=3]Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg[/SIZE]
[SIZE=3]  Connection failed [IP: 91.189.88.149 80][/SIZE]
[SIZE=3]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg[/SIZE]
[SIZE=3]  Connection failed [IP: 91.189.91.13 80][/SIZE]
[SIZE=3]Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release[/SIZE]
[SIZE=3]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg[/SIZE]
[SIZE=3]  Connection failed [IP: 91.189.91.15 80]
[/SIZE]
I have changed **/etc/apt/sources** to ***archive.ubuntu.com*** from ***in.archive.ubuntu.com***

Please suggest a working repository for my version. i.e. **12.04.4**

---

