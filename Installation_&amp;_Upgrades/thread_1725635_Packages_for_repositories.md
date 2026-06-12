---
title: "Packages for repositories"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by AydSoTG on 2011-04-10
Hello all.

I have made a local repository. Everything works fine - i copy packges into it from /var/cache/apt/archives and then install them offline without any problem. But if a package is NOT copied from the /var/cache/apt/archives it is not installed.

I downloaded VirtualBox package for ubuntu from the official site. And then installed it with double click from gnome without any problem. Then i copied this pachage into my repositry for later offline installation with apt. But apt doesn't see the package as if it's not there. 
dpkg-scanpackges and apt-get update had been run beforehand. 

So, are special packges for repositories must be made?

---

