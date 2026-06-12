---
title: "compiz-kde has unmet dependencies with Hardy+KDE3.5.10"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by pansz on 2008-09-23
I installed Kubuntu 8.04.1 and backports the KDE 3.5.10, when I install compiz-kde I got the following:

$ sudo apt-get install compiz-kde
[sudo] password for poet:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-kde: Depends: compiz-core (= 1:0.7.4-0ubuntu6) but 1:0.7.4-0ubuntu7 is to be installed
              Depends: compiz-plugins (= 1:0.7.4-0ubuntu6) but 1:0.7.4-0ubuntu7 is to be installed
E: Broken packages

$


It seems that someone had upgraded compiz-core and compiz-plugins and forget to upgrade compiz-kde pacakge. Anyway to solve that problem?

---

### Post by pansz on 2008-09-23
bump, any hints?

---

### Post by pansz on 2008-09-29
bump again, really no solution?

---

