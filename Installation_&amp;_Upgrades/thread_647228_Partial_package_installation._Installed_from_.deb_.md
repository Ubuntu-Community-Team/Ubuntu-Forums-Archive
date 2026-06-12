---
title: "Partial package installation. Installed from .deb file"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by master5o1 on 2007-12-22
```
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package mfc665cwcupswrapper needs to be reinstalled, but I can't find an archive for it.'
```



Don't ask me how this happened. I still have the .deb file.

---

### Post by Partyboi2 on 2007-12-22
Have you tried uninstalling and reinstalling  the package?

---

### Post by Partyboi2 on 2007-12-22
Try this:
```
 dpkg --remove --force-remove-reinstreq mfc665cwcupswrapper
```

---

### Post by master5o1 on 2007-12-22
dastoney@Octrev:~/Desktop$ sudo  dpkg --remove --force-remove-reinstreq mfc665cwcupswrapper
[sudo] password for dastoney:
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 90524 files and directories currently installed.)
Removing mfc665cwcupswrapper ...
/var/lib/dpkg/info/mfc665cwcupswrapper.prerm: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error processing mfc665cwcupswrapper (--remove):
 subprocess pre-removal script returned error exit status 127
/var/lib/dpkg/info/mfc665cwcupswrapper.postinst: 3: /usr/local/Brother/Printer/mfc665cw/cupswrapper/cupswrappermfc665cw: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mfc665cwcupswrapper

---

### Post by master5o1 on 2007-12-22
E: The package mfc665cwcupswrapper needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by master5o1 on 2007-12-25
this is old but the problem STILL exists.

---

### Post by Partyboi2 on 2007-12-25
I  came across this Faq on the brothers website.
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#80](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#80)

---

