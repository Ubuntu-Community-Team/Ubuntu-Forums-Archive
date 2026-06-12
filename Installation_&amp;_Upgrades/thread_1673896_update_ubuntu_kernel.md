---
title: "update ubuntu kernel"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by tusu on 2011-01-23
Hiee,
 I want to update my ubuntu kernel..
first i ran the command uname -r..i got the result

2.6.32-21-generic.

next i typed 
 
# yum update kernel     (yum is installed), i got the msg


No Match for argument: kernel
No package kernel available.
No Packages marked for Update

plz tell me.how can i update my kernel.????...

---

### Post by ajgreeny on 2011-01-23
I presume from your current kernel that you are running 10.04; correct?

If so, the easiest way to get a newer kernel is to add the ppa for ubuntu kernels to your sources.  Go to [https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa) for the details.

I am running kernel 2.6.37-12 in my gnome Lucid with no problems at the moment, but it may be different for you, so be prepared to try it and then un-install it if necessary.

---

### Post by eentonig on 2011-01-23
1. Why would you want to use yum on Ubuntu? Ubuntu is debian based and has it's own package manager.
2. When you upgrade though synaptic, new kernel updates are installed automatically. At least, the ones that were tested by the developpers. Do you have a specific reason to install a newer kernel?

---

