---
title: "Sylpheed-Claws Version 1.0.4-1 Universe"
date: 2005-08-26
forum: Installation &amp; Upgrades
---

### Post by JBE on 2005-08-26
Hi All,

I can see Sylpheed Claws 1.0.4-1 here:

[http://archive.ubuntu.com/ubuntu/pool/universe/s/sylpheed-claws/](http://archive.ubuntu.com/ubuntu/pool/universe/s/sylpheed-claws/)

I have  universe in my sources.lst:

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


However, when I type 'sudo apt-get install -f sylpheed-claws=1.0.4-1' the response is:

> Reading package lists... Done
Building dependency tree... Done
E: Version ‘1.0.4-1’ for ‘sylpheed-claws’ was not found

Why?

Thanks.

---

