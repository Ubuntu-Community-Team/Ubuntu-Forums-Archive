---
title: "Kernel compilation problem"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by CelticWhisper on 2006-12-19
I'm trying to compile a reconfigured kernel and am running into the following error:

> root@DAUGHTER:/usr/src/linux# make-kpkg clean
exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean
/usr/share/kernel-package/ruleset/misc/version_vars.mk:123: *** Error.  The version number # # configuration written to .config # 2.6.19 is not all lowercase.  Since the version ends up in the package name of the kernel image package, this is a Debian policy violation, and the packaging system shall refuse to package the image. . Stop.

Any idea on what's causing this?  Thanks in advance for the help.

---

### Post by mxrten on 2007-01-01
I had the same problem until I added the symlink...
```
[INDENT]ln -s /usr/src/linux-2.6.19.1 /usr/src/linux[/INDENT]
```
...which I thought was unnecessary at the time.

---

