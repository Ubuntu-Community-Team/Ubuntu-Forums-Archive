---
title: "Update Problems"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by 36plymouth on 2008-03-10
I am having trouble getting system updates to load & install, 143 of them.
Get a message "Fix Broken Packages First"  I am using Ubuntu 7.10
I have no problem getting new programs and installing them.
I think I have all necessary check boxes checked in repositories.
Thanks for helping.:confused:

---

### Post by milton1 on 2008-03-10
In a terminal, try the following:

```
sudo apt-get install -f
```
```

sudo apt-get update
sudo apt-get upgrade

```
This should fix your broken packages and then upgrade your system.

---

### Post by 36plymouth on 2008-03-10
Thanks!,
I will give it a try tonight.

---

### Post by 36plymouth on 2008-03-11
That did the trick.  Thanks for your help!

---

