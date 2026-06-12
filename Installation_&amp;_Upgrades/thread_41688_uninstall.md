---
title: "uninstall"
date: 2005-06-14
forum: Installation &amp; Upgrades
---

### Post by belred on 2005-06-14
i posted in a while back how to uninstall a package and the answer posted was:

sudo aptitude install <pkgname>=<version>

this answered my question at the time how to go back to a previous version.  but now i want to uninstall a package, but not any of it's dependencies.  if i use kynaptic, it always wants to uninstall dependencies including kde_base or some other package i know i need.   is there a way to tell dpkg, or apt-get or aptitude or kynaptic... etc, to just uninstall a package and ignore dependencies?

thanks,

bryan

---

### Post by Xian on 2005-06-14
Usually this is Apt telling you that if you remove package_foo that package_goo will no longer work so it has to go as well. This will happen if they INTER-depend upon one another. Now, having said that please post what package it is that you want to remove and also provide what other things that Apt wants to remove. They might just be some meta-pkg headers that don't make any difference. By defualt, Apt (Synaptic) will not remove non-interdependent packages when you uninstall an application. So, my guess is that Apt is bluntly telling you that uninstalling them will result in the breakage of others, and this being the case they no longer should be on your system.

---

### Post by belred on 2005-06-14
hmmm... i installed ksysv and i just tried to uninstall it again and this time kynaptic showed no dependencies.  but i know i've installed some package where it didn't require a dependency during install, but i tried to uninstall it, it wanted to install kde_base.  thanks for your reply... if i see this behavior again i'll post then.

bryan

---

### Post by Xian on 2005-06-14
[QUOTE=belred]but i know i've installed some package where it didn't require a dependency during install, but i tried to uninstall it, it wanted to install kde_base.[/QUOTE]
Sounds like one of those meta-pkgs I was speaking about.
They are perfectly harmless to remove.

However, I'd still post back with the exact pkg name to be certain.

---

