---
title: "Upgrading automatically installed packages marks them as manually installed"
date: 2016-09-10
forum: Installation &amp; Upgrades
---

### Post by knuddeldrache on 2016-09-10
i upgraded a few packages, among those were some that were automatically installed. After the upgrade, they was marked as manually installed.

this does not make sense to me.  is there a way to explicitly upgrade a number of packages while preserving their automatically installed state?

---

### Post by ajgreeny on 2016-09-10
I suspect this is just a query related to your interpretation of what is meant by "manually installed".
What do you think it means?
Why do you want or need to know?

Also, what do you mean by, and where are you seeing an indication of which packages were automatically installed?

If I use the Status filter in the left hand pane of synaptic, which I often use for package management, to view the "Manually installed", I see everything that I have chosen to install following the OS installation, with, as far as I can make out, all the dependencies that were also installed. Nowhere can I see any list of "automatically installed" packages.

---

### Post by knuddeldrache on 2016-09-10
> I suspect this is just a query related to your interpretation of what is meant by "manually installed".
What do you think it means?

An automatically installed package is any package installation that did not come to my system by explicit user request. This definition means all packages that were installed only to satisfy a dependency.

therefore, a manually installed package is every package that is not automatically installed (i believe there is an apt-mark for automatically installed, but not for manually installed)

> Why do you want or need to know?
if i still need a package B after removing package A (that depended on Package B).  if Package B was installed only because Package A depended on it, then it should be marked as "automatically installed". If i remove Package A after installing it and its dependencies, i can remove Package B using autoremove. 

but if i Install Package A, then upgrade package B, then autoremove will not remove package B because it is no longer marked as automatically installed. 

i did not request Package B to be on my system.  I just requested that, if it needs to be installed, it should be a specific version

> Nowhere can I see any list of "automatically installed" packages.
there is a marking that synaptic can apply to packages: "automatically installed". i believe this also affects the lower levels of package management, including the command line tools. 

you can see that synaptic knows about automatically installed packages by subtracting the count of manually installed packages from the total number of installed packages

---

### Post by mc4man on 2016-09-11
I believe it would depend on how the auto package was upgraded.
So package A caused package B to be installed, B is marked as auto installed.

If both A & B get an upgrade & upgrading A causes B to be upgraded then B stays marked auto.
If one upgrades B & that causes A to upgraded then  B  loses it's auto status.

If upgrading A doesn't cause B to be upgraded then B loses it's auto status when individually upgraded
If only B gets an upgrade it loses status when upgraded.

---

### Post by ian-weisser on 2016-09-11
It would perhaps help us a lot if you could provide a specific example that we could duplicate in a test system.
I cannot triage a bug like this if I cannot reproduce it in a test system.

---

### Post by knuddeldrache on 2016-09-14
> **ian-weisser said:**
> It would perhaps help us a lot if you could provide a specific example that we could duplicate in a test system.
I cannot triage a bug like this if I cannot reproduce it in a test system.

1. wait for ANY automatically installed package to be ready for an upgrade
2. explicitly mark it for upgrade in synaptic
3. click apply


Expected results:
the package is still marked automatically installed after the operation

actual results: 
the package is no longer marked automatically installed after the operation

---

