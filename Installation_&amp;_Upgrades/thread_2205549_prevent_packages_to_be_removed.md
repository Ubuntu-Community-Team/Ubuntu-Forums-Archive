---
title: "prevent packages to be removed"
date: 2014-02-14
forum: Installation &amp; Upgrades
---

### Post by Ubi_one_2014 on 2014-02-14
Hi

because i own a Brother DCP-585CW all in 1 i had to install ia32 libs, in order to install the ubuntu/debian driver packages

now, everytime, after an apt-get dist-upgrade i see a list of packages that ubuntu no longer needed, included the required packages for the drivers

how do i prevent  a package to be removed?

i just need to fix a package, so it never got deleted.
how do i do that??

Thanks

---

### Post by Dennis N on 2014-02-14
You can use Synaptic Package Manager to do that:
1) select the package from the window
2) in the menu, Package > Lock Version
This will prevent it from being updated.
It won't be removed unless you mark it for removal, or authorize it for autoremoval when it is suggested.

---

### Post by ian-weisser on 2014-02-14
> **Ubi_one_2014 said:**
> how do i prevent  a package to be removed?

There are several ways on the command line to change a package from autoremovable to non-autoremovable.
Apt tracks this property as "auto" or "manual" marking. 
'auto' means that it can be seen by autoremove.
'manual' means that you specified that you want it.

The easiest way is: **sudo apt-get install <package>**
Since the package is already installed, apt will simply change the marking. It won't otherwise change anything.

The other way is: **sudo apt-mark manual <package>**

---

