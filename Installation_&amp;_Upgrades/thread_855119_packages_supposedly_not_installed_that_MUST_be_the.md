---
title: "packages supposedly not installed that MUST be there"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by ghira on 2008-07-10
I upgraded from dapper to hardy shortly after hardy was released.

I've only noticed recently that my package manager claims a few
things which seem like they can't be true. For instance, I tried
to add a package which said it would need to install gnome
(and a bunch of other things) to work. But I already run gnome.

And I'm running the generic kernel, but the package manager
claims I have linux-386 but not linux-generic installed.

Is any of this evidence that something's a bit wrong somewhere?
Should I tell the package manager to install gnome and linux-generic
or would that be a really really bad idea?

---

### Post by Pumalite on 2008-07-10
Run:
sudo apt-get autoremove
sudo apt-get -f install
uname -a

---

### Post by ghira on 2008-07-10
Thanks. I'll try this.

---

### Post by ghira on 2008-07-10
well,

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdns32 linux-headers-2.6.24-16-generic linux-headers-2.6.24-16

which doesn't seem quite enough to be a problem

---

### Post by ghira on 2008-07-10
-f install doesn't change anything

uname -a says
Linux ubuntu 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

as usual (yes, it says I'm running generic)

---

