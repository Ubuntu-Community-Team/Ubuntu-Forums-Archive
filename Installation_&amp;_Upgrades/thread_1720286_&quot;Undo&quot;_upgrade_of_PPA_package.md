---
title: "&quot;Undo&quot; upgrade of PPA package?"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by carlotheman on 2011-04-03
Hi,

I recently upgraded a program from a PPA to the latest version and there seems to be a regression.

How can I revert back to the version I had installed, now the second-but-latest version from PPA?

Thanks, Carlo

---

### Post by beew on 2011-04-03
Depending on whether you want to keep the ppa.

1) If you want to keep the ppa. Open Synaptic, find the program, highlight it and on the tab "Package" choose "force version". Then you will find the next lower version available and click it. After you have downgraded the program, highlight it and choose Packages > lock version. That way it wouldn't be upgraded. You can upgrade it when you know that the regression is resolved in the ppa.

2) If you don't want the ppa. use ppa purge.[ http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/]("http://bigbrovar.aoizora.org/index.php/2010/01/10/how-to-safely-remove-ppa-repository-from-ubuntu/")

When ppa-purge removes a ppa, it will automatically safely downgrade all packages installed from the ppa to the next lower available version.

You can also purge the ppa with a GUI tool using Ubuntu Tweak if you have it installed.

---

### Post by carlotheman on 2011-04-03
Hi feew! Thanks for your help!

It appears that only the latest version is available in the PPA, so they seem to be removing the old versions...

I am in contact with the PPA maintainer and could let him know how to keep older versions available in the PPA.

What would he have to do?

Carlo

---

