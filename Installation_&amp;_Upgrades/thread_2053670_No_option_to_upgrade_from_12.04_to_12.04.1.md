---
title: "No option to upgrade from 12.04 to 12.04.1"
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by kingkratos on 2012-09-05
I am wishing to upgrade to 12.04.1, but my package manager does not list an upgrade as available. I have tried running $sudo apt-get update and $sudo apt-get upgrade without any luck.

Anyone know what I need to do to upgrade to 12.04.1?

Kratos

---

### Post by mywai on 2012-09-05
In terminal, enter

lsb_release -a

if you have kept up with the updates, Description: will be "Ubuntu 12.04.1 LTS"

---

### Post by kingkratos on 2012-09-06
Interesting. I was unaware that the details page would not display this. Oh well. Thanks.

Kratos

---

