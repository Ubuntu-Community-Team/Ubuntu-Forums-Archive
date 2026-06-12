---
title: "Mercurial installation problem"
date: 2014-05-21
forum: Installation &amp; Upgrades
---

### Post by adityamagadi on 2014-05-21
Hey guys,
            I have have installed mercurial using easy_install mercurial command, it has installed mercurial 3.0 version. However i have tortoiseHg that works with mercurial 2.8 version and therefore shows the following conflict:

 **This version of TortoiseHg requires Mercurial version 2.7.n to 2.8.n, but found 3.0**

now for this reason i want to install mercurial 2.8 and remove 3.0 version.

**sudo apt-get remove mercurial** does not seem to removing the 3.0 version. so now basically how can i get rid of the 3.0 version?

---

### Post by adityamagadi on 2014-05-21
pip uninstall <package-name> solved the problem.

---

