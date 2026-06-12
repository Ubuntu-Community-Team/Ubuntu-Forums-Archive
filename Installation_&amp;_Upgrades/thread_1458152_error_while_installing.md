---
title: "error while installing"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by KaiJordanDay on 2010-04-19
> kai@kai-laptop:~/acerhk-0.5.35$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/kai/acerhk-0.5.35 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'
Makefile:303: /usr/src/linux-headers-2.6.32-21-generic/scripts/Kbuild.include: No such file or directory
Makefile:538: /usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.32-21-generic/arch/x86/Makefile'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'
make: *** [acerhk.ko] Error 2


I don't get it. Tried so many ways... Need it for my wireless.

---

### Post by 2hot6ft2 on 2010-04-19
Makefile:538: /usr/src/linux-headers-2.6.32-21-generic**[COLOR="DarkRed"]/arch/[/COLOR]**x86/Makefile: No such file or directory

This is ubuntu which is debian. It is NOT Arch.

---

### Post by KaiJordanDay on 2010-04-20
Wheres the error then? How do I fix.

---

### Post by norseman-has-a-laptop on 2010-04-20
> **KaiJordanDay said:**
> Wheres the error then? How do I fix.

try a reinstall usually that fixes most errors on an install

---

### Post by KaiJordanDay on 2010-04-23
damn. Was hoping to avoid that.

Means reinstalling 9.04... upgrading. 9.10 disk and Beta 2 disks hate my pc :P

---

