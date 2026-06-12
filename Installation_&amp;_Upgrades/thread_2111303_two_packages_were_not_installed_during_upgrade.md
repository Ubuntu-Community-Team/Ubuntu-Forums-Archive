---
title: "two packages were not installed during upgrade"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by marchelloUA on 2013-02-01
Hi all, 

I tried to upgrade system using 

# sudo apt-get upgrade

and got warning message saying that linux-headers-generic and linux-image-generic packages were not installed. 

What is wrong?

---

### Post by snowpine on 2013-02-01
Nothing wrong; this is the normal & expected behavior of the command you used (see 'man apt-get' for more details).

To install the new kernel:

```
sudo apt-get dist-upgrade
```

---

