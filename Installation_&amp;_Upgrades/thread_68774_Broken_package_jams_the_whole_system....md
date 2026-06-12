---
title: "Broken package jams the whole system..."
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by Skebaristi on 2005-09-24
So, I tried to install BOINC from a debian package... BIG mistake. It didn't work and when i tried to uninstall it, it didn't do that either. Now I'm stuck with all the package managers only telling me to fix the broken package (boinc-daemon), but none of them will reinstall or remove it. I get an error message like this:
```
riku@RikuHQ:~/paketit/boinc$ sudo dpkg -r boinc-daemon
dpkg: error processing boinc-daemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 boinc-daemon
``` 


I try to force it and I get this:
```
riku@RikuHQ:~/paketit/boinc$ sudo dpkg -r --force-remove-reinstreq boinc-daemon
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 106635 files and directories currently installed.)
Removing boinc-daemon ...
rm: tiedostoa "/etc/rc0.d/K07boinc" ei voi poistaa: Tiedostoa tai hakemistoa ei ole
dpkg: error processing boinc-daemon (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 boinc-daemon
```

I'm desperate to get any help at the moment   ](*,)

EDIT: Oh, and "tiedostoa "/etc/rc0.d/K07boinc" ei voi poistaa: Tiedostoa tai hakemistoa ei ole" means "file "/etc/rc0.d/K07boinc" cannot be removed: File or directory doesn't exist"

---

### Post by fordfan753 on 2005-09-24
It said to try reinstalling before you remove it...did you try to reinstall it through synaptic?

---

### Post by Skebaristi on 2005-09-24
[QUOTE=fordfan753]It said to try reinstalling before you remove it...did you try to reinstall it through synaptic?[/QUOTE]

It won't let me... I get an error message (again  :roll: ) that says: "Problems cannot be solved, broken packages have been 'built'" (don't exactly know how it should be translated from the finnish word "pystytetty")

---

### Post by Skebaristi on 2005-09-24
I'm in deep trouble here... I can't install anything before the problem gets fixed.

---

### Post by Skebaristi on 2005-09-25
Ok, I managed to fix things by commenting some lines from the boinc-daemon.postrm-script so that when being removed it doesn't care about the files that don't exist. Everything's in working order now :)

Thank's to the guys at #debian.se @freenode

---

