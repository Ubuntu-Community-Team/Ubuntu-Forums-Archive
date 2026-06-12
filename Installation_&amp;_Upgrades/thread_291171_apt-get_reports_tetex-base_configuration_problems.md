---
title: "apt-get reports tetex-base configuration problems"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by jnoreiko on 2006-11-02
Since I upgraded to Dapper, every time I use apt-get I get a warning:
```
4 not fully installed or removed.

```

apt-get then tries to install these four packages, and fails. It basically says this:

```
dpkg: error processing tetex-base (--configure):
 subprocess post-installation script returned error exit status 1

```
and then the packages that depend on tetex-base fail too ( tetex-bin,  tetex-extra,  jadetex).

The log file tetex-base produces is massive. This is the bit with an error message:

```
fmtutil: running `etex -ini   -jobname=jadetex -progname=jadetex &latex jadetex.ini' ...
This is pdfeTeX, Version 3.141592-1.21a-2.2 (Web2C 7.5.4) (INITEX)
---! /var/lib/texmf/web2c/latex.fmt was written by tex
(Fatal format file error; I'm stymied)
```

I have no idea at all what to do.
I'd like to upgrade to Edgy, but I'm concerned this unresolved issue could cause worse problems.
Is there a way to fix this, other than do a clean install of Edgy from CD?

---

### Post by rrwo on 2006-11-02
I had the same problem when upgrading.

There is a conflict with existing LaTeX class/style files.  Backup your existing files in /usr/share/texmf, then uninstall tetex-base, tetex-bin, tetex-extra, tex-common, and any other latex packages (using apt-get remove).  Then re-install those packages after the upgrade.

---

### Post by jnoreiko on 2006-11-06
Thanks, that seems to have worked.
I get no dependency errors any more :)

I've not reinstalled those packages anyway. I have no idea why they were there.

---

### Post by rrwo on 2006-11-11
> **jnoreiko said:**
> Thanks, that seems to have worked.
I get no dependency errors any more :)

I've not reinstalled those packages anyway. I have no idea why they were there.

There were probably part of the base install.  But some postscript and PDF manipulation tools may require them.

---

