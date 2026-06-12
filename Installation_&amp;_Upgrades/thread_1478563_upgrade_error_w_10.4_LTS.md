---
title: "upgrade error w/ 10.4 LTS"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by groogruxking40 on 2010-05-09
doing an upgrade from 10.4 to 10.4 LTS and got this error:

Could Not Calculate Upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'skype' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

so anyone know how to fix this?

would love to see the new 10.4 LTS

---

### Post by lemming465 on 2010-05-10
One possible ploy would be to remove skype by hand, do the upgrade, then reinstall it.  Probably you installed skype from medibuntu repositories?  It might also help to temporarily disable any non-ubuntu repositories (synaptic -> Settings -> Repositories).

I'm not sure how much, if any, configuration you might lose with a skype uninstall / reinstall.

---

### Post by groogruxking40 on 2010-05-10
> **lemming465 said:**
> One possible ploy would be to remove skype by hand, do the upgrade, then reinstall it.  Probably you installed skype from medibuntu repositories?  It might also help to temporarily disable any non-ubuntu repositories (synaptic -> Settings -> Repositories).

I'm not sure how much, if any, configuration you might lose with a skype uninstall / reinstall.

did that.. now getting this error

Third party sources disabled

Some third party entries in your sources.list were disabled. You can re-enable them after the upgrade with the 'software-properties' tool or your package manager.

---

### Post by lemming465 on 2010-05-11
"Third party sources" disabled is a warning notice, not an error.  It's OK to continue past it.

---

