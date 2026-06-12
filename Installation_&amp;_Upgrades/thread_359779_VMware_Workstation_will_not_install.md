---
title: "VMware Workstation will not install"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by jam'ez on 2007-02-12
I had VMware Player installed but decided to upgrade to the Workstation.
Every time I try to install, I get this:

```
root@tux:/home/james/Desktop# export CC=/usr/bin/gcc-3.4 && cd vmware-distrib && sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

```

I believe to have removed VMware software via synaptic off my laptop, what else could it be?

Thank you in advance,

James

---

### Post by jam'ez on 2007-02-12
Still no luck at all, I cant see where my VMware software installed could be to stop this from installing?

---

### Post by jam'ez on 2007-02-12
Ok I solved the problem with removing all files in /etc/vmware
:)

---

### Post by morphet on 2007-02-14
Thanks, jam'ez! you just ended a long search. :)

---

