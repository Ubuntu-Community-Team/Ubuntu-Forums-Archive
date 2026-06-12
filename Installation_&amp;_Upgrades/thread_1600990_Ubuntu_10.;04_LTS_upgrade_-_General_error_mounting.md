---
title: "Ubuntu 10.;04 LTS upgrade - General error mounting filesystems"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by jlueke on 2010-10-19
Hi,

The upgrade didn't complete and now if I try run the newest kernel in any mode I get a kernel panic error.  I can get into the command shell on the third version of the kernel but I get the general file system error.  The upgrade is web based, I don't have a CD otherwise I would just restart.  

If I type apt-get upgrade it tells me dpkg was interrupted and I should manually run sudo dpkg --configure -a
If I try that it tells me unable to access dpkg Read-Only file system.

What are the correct steps for me to take to resolve this?

---

### Post by sikander3786 on 2010-10-19
If you are in root shell, don't use sudo infront of dpkg --configure -a as you already have got the previledges.

If the command prompt looks like

```
you@computename:-$
```

Then it is not the root shell, you'll need to add sudo in that case.

If it looks like

```
root@computername:-$
```

It is the root shell, hence sudo not needed.

---

### Post by jlueke on 2010-10-19
Without the sudo I get unable to access dpkg status area: Read-only file system

---

### Post by jlueke on 2010-10-20
I just created a CD of 10.04 and reinstalled.  I guess that's what back-ups are for.

---

