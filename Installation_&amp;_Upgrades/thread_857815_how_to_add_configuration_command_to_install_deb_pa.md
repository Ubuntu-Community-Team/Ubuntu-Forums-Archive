---
title: "how to add configuration command to install deb package using apt-get"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by pegasusmd on 2008-07-12
Hi all, 

I need to configure a deb package with some options(eg. -fPIC)
I can use apt-get install to install directly but dont know where to add this options. 

how can I use apt-get to configure like this? 

or are there other ways to do this and then install. 

Thanks, 

Dan

---

### Post by logos34 on 2008-07-13
Use **dpkg**

see 

man dpkg

[B]dpkg [options] action

[/B]sudo dpkg -i[other options] whatever.deb

---

