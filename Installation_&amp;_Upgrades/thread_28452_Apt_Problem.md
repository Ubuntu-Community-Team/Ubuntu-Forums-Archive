---
title: "Apt Problem"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by Slalomsk8er on 2005-04-20
I realy start to hate apt.

After 1 hour of search (google, man apt und man apt-get) and trying I found no way to install a downloaded package (/home/xxx/xxx/gourmet_0.8.3.3-1_i386.deb).

Please tell me a way to install a single downloaded package.

If there is no way to do this (what I don't think), then apt is worst then rpm.

Thanks,
Dominik

---

### Post by edubarr on 2005-04-20
You can use the dpkg command. Basically all you need is to type dkpg --install gourmet_0.8.3.3-1_i386.deb and it will install the package for you. If you have any other questions you can refer to the man pages (man dpkg).

Hope this helps :-)

---

### Post by Slalomsk8er on 2005-04-20
Thanks, this was what I needed.

---

