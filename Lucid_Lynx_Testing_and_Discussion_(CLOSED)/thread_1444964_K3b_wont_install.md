---
title: "K3b wont install"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by arnab_das on 2010-04-02
[B]sudo apt-get install k3b
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k3b: Depends: kdebase-runtime (>= 4:4.3.95) but it is not going to be installed
       Depends: libk3b6 (= 1.91.0~rc2-0ubuntu1) but it is not going to be installed
       Depends: libkcddb4 (>= 4:4.2.96) but it is not going to be installed
E: Broken packages

-------------

any solutions? i presume dependencies are supposed to be installed alongwith the app.

---

### Post by dcstar on 2010-04-03
> **arnab_das said:**
> [B]sudo apt-get install k3b
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k3b: Depends: kdebase-runtime (>= 4:4.3.95) but it is not going to be installed
       Depends: libk3b6 (= 1.91.0~rc2-0ubuntu1) but it is not going to be installed
       Depends: libkcddb4 (>= 4:4.2.96) but it is not going to be installed
E: Broken packages

-------------

any solutions? i presume dependencies are supposed to be installed alongwith the app.

Make sure you do not have old repositories in your Software Sources.

---

