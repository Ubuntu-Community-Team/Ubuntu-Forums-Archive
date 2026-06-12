---
title: "i have an update that don't want to install binutils why is that?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-31
"The following packages have been kept back:
binutils"

synaptic said  Depends: binutils (>=2.20.1-4) but 2.20.1-3ubuntu1 install

thanks in advance.

---

### Post by Didius Falco on 2010-03-31
> **aviramof said:**
> "The following packages have been kept back:
binutils"

synaptic said  Depends: binutils (>=2.20.1-4) but 2.20.1-3ubuntu1 install

thanks in advance.

It's telling you that the version of binutils that has been held back isn't in the repository yet. You already have version 2.20.1-3ubuntu1 installed.

Just wait and it'll turn up...

---

### Post by kansasnoob on 2010-03-31
I mentioned that here:

[https://bugs.launchpad.net/ubuntu/+source/binutils/+bug/548451](https://bugs.launchpad.net/ubuntu/+source/binutils/+bug/548451)

> 

When attempting to upgrade this package the following error message appears in Synaptic:

Could not mark all packages for installation or upgrade.

The following packages have unresolvable dependencies. Make sure that all required repos are added and enabled.

binutils:
  Depends: binutils (>=2.20.1-4) but 2.20.1-3ubuntu1 is to be installed

I'm reluctant to try and "force version".


---

### Post by aviramof on 2010-03-31
thanks for the information problem solved.

---

