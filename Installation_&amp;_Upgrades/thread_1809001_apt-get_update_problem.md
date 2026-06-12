---
title: "apt-get update problem"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by enemje on 2011-07-21
hello,
when I run apt-get update thru the terminal, along with a list of repositories 'fetched' i get the message:

```
W: Failed to fetch http://ppa.launchpad.net/ubuntugis/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntugis/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
```

Is there any solution?


Asus EeePC, Intel Atom Dual Core, Dual Boot, Ubuntu 11.04 and Win & Starter, 2GB RAM

---

### Post by tjavailable on 2011-07-21
> **enemje said:**
> hello,
when I run apt-get update thru the terminal, along with a list of repositories 'fetched' i get the message:

```
W: Failed to fetch http://ppa.launchpad.net/ubuntugis/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntugis/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
```

Is there any solution?


Asus EeePC, Intel Atom Dual Core, Dual Boot, Ubuntu 11.04 and Win & Starter, 2GB RAM
try sudo apt-get update
or
sudo apt-get upgrade

---

### Post by enemje on 2011-07-21
Thanks for responding.
even after trying with sudo, I still get those messages.

---

### Post by plucky on 2011-07-21
> **enemje said:**
> Thanks for responding.
even after trying with sudo, I still get those messages.

That is because there isn't a PPA for Natty

See [Here](http://ppa.launchpad.net/ubuntugis/ppa/ubuntu/dists/)

Open Software Sources and disable the PPA as a Source.

Good Luck

---

### Post by olgasmi on 2011-07-22
"An upgrade from 'janty' to 'lucid' is not supported with this tool"

??

---

