---
title: "Updating Kernel"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by Baconfatty on 2009-12-04
Hey at the moment I am trying to update from 2.6.31-15-generic to 2.6.32-020632rc6-generic.

However when I go into terminal and type in

```

sudo apt-get install linux-image-2.6.32.020632rc6

```
I get

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.32-020632rc6-generic

```

I know the files are here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

but don't know how to tell ubuntu where they are, can someone give me a hand here?

---

### Post by byStanderone on 2009-12-04
...it is not advisable to update kernels from ppa, simply do an update:
system>administration>update manager...clik on check for updates and install.

---

### Post by ptn107 on 2009-12-04
```
sudo dpkg -i <filename>.deb
```

---

### Post by laceration on 2009-12-04
1. To add software from a ppa you need to add the ppa repository to your sources
2. This is not a ppa repository.  ppa repositories come from launchpad addresses.

To find kernel ppas go here and search
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

