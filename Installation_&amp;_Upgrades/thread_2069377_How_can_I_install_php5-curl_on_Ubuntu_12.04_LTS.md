---
title: "How can I install php5-curl on Ubuntu 12.04 LTS ?"
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by timkoop on 2012-10-10
I have a working server running Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-generic x86_64), including apache and php. Now I want to add curl support for php by running this:

```
apt-get install php5-curl
```
Sounds simple? No. I get this response:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic : Depends: linux-image-3.2.0-26-generic but it is not going to be installed
 php5-curl : Depends: libcurl3 (>= 7.16.2-1) but it is not going to be installed
             Depends: php5-common (= 5.3.10-1ubuntu3.4) but 5.3.10-1ubuntu3.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

It looks like I have to upgrade to a new kernel (3.2.0-26) just to get php-curl working. I would prefer to not have to do this.

Is there some way I can install php curl for my kernel version which is 3.2.0-24?

Thanks.

---

### Post by timkoop on 2012-10-10
Here is the answer:

I had thought that it simply wanted to upgrade the kernel.  It turns out that there was actually a real problem with dependencies, which occurred as a result of the partition running out of space.  After a bit of deleting, I found some more space and installed the new kernel.  Now everything works great.

---

