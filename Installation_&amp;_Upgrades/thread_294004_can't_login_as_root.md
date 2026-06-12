---
title: "can't login as root"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by gaaslight on 2006-11-06
after installing ubuntu edgy and setting up user accounts, downloading the updates and adding my favorite programs, i ran the 'sudo oem-config-prepare' as instructed from the command line. 
after which, i was able to login as any of the user accounts i created, but not as root. after reinstalling 3 times with the same results, i reinstalled a 4th time but did not remove the oem account.
am i missing something? is this a bug? or am i not supposed to have access to the root account?

---

### Post by buebo on 2006-11-06
> **gaaslight said:**
> 
am i missing something? is this a bug? or am i not supposed to have access to the root account?

The root account is disabled per default.

Either use sudo or enable it with 'sudo passwd root'

---

### Post by aysiu on 2006-11-06
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

