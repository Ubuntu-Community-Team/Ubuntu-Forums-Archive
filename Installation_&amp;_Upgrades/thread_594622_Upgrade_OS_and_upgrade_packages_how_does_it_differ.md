---
title: "Upgrade OS and upgrade packages: how does it differ?"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by grigory.soid on 2007-10-28
Hey there!

Could not somebody explain me how does it differ? What will ubuntu do when I upgrade OS from (e.g.) 7.04 to 7.10? And what will ubuntu do when I just install all updates?

---

### Post by por100pre1 on 2007-10-29
Welcome to the forums! Usually in Ubuntu, you get some updates, those are for fixing small bugs and patching security breaches. No big version changes are done to programs because they could cause some breakage. When Ubuntu release is upgraded, the latest software stable packages are installed, that represent huge changes that need some additional tweaks the upgrade takes care of. The repositories sources list is changed; the packages of the new default installation and new versions of all the software you already have installed are downloaded; that includes some new packages if the new release has new functionalities. Any incompatible software will be removed for good, if it was from the official repositories (that's why using packages from the official repos is so important). Some files will need new configuration files and you could be asked to replace some of them. The mess in finally cleaned y you end up with a new OS.
:guitar:

Hope this helps. :)

---

