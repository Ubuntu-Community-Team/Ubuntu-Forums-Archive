---
title: "linux-generic vs . linux-image-generic vs. linux-image-2.6.31-22-generic"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by littlebigman on 2010-08-25
Hello

While running "aptitude search generic" on a 9.10 or 10.04 hosts, I notice there seem to be three options to upgrade a host to a newer kernel:

[LIST]
[*]linux-generic
[*]linux-image-generic
[*]linux-image-2.6.31-22-generic
[/LIST]

What's the difference? Which should I choose?

Thank you.

---

### Post by arubislander on 2010-08-25
Go with linux-generic. You'll get everything that it depends on including linux-image-generic and its dependency linux-image-2.6.31-22-generic.

If you want to know what dependencies linux-generic further has, fire up synaptic, select the package, pull up the properties and perview the dependency tab.

The idea is to help with automatich upgrades of the kernel. The linux-generic package is a meta package that will always depend on the latest version of the linux-image-generic, which in its turn will always depend on the latest linux-image-x.x.x-yy-generic package

---

### Post by littlebigman on 2010-08-25
Thanks for the info. Running "apt-file show linux-image-2.6.31-22-generic | less" shows what the package contains (kernel + bunch of modules).

---

