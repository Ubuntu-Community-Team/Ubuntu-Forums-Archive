---
title: "Problems with dselect"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by cpickering on 2008-04-28
Morning guys,

Sorry for my first post being a request for help, I've been everywhere to fix this issue..

I like to use dselect, and have attempted to run dselect to install some packages, but I'm getting the following error:
```
Building dependency tree
Reading state information... Done
The following packages have unmet dependencies:
  mount: Breaks: nfs-common (< 1:1.1.0-7) but 1:1.0.10-6+etch.1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Internal error, problem resolver broke stuff
Some errors occurred while unpacking. I'm going to configure the
packages that were installed. This may result in duplicate errors
or errors caused by missing dependencies. This is OK, only the errors
above this message are important. Please fix them and run [I]nstall again
Press enter to continue.

```

Software: Ubuntu 7.10
Uname Output: 2.6.18-028stab053.10

I must stress, that this is a VPS, and not installed on VMWare or a dedicated box.. 

Thank you

Carl

---

### Post by cpickering on 2008-04-28
BTW: This error is simply generated when I run dselect, and select 'install'. I haven't got to the point to select any packages

---

### Post by cpickering on 2008-04-30
Anyone? :(

---

