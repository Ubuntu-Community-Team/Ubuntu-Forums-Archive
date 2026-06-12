---
title: "tetex upgrade problem"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by DW5 on 2005-10-14
Upgraded to Breezy and can't resolve the last set of upgrade issues:

The root of the problem seems to be with tetex:

Error reads:

```
Running initex. This may take some time
/usr/bin/fmutil: line 253: -ini: command not found
Error: '-ini  -jobname=q -progname=q ' failed
```

line 253 of the fmutil file reads

```
  $mktexfmtMode && ${1+"$@"} >&2 || ${1+"$@"} 
```

then it, fmutil, installs a bunch of stuff in /var/lib/texmf/web2c

the failure of that subprocess wrecks the installation of tetex-base, and thus creates dependency problems for rest of package, ultimately of lyx.  I uninstalled lyx and tetex with dpkg --purge, tried to reinstall with synaptic, but to no avail.

Anybody had or resolved this problem?

---

