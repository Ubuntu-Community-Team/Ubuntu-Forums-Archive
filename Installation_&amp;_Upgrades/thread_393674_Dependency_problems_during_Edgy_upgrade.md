---
title: "Dependency problems during Edgy upgrade"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by ricardisimo on 2007-03-26
I was only planning on making Edgy a temporary pit-stop on my way to Feisty Beta for this, my home computer. But then I started getting this problem, first in an error popup:

[SIZE="3"]! An error occurred

The following details are provided:[/SIZE]
```
E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

```
So, I close that, and now Update Manager's "Changes applied" terminal:

```
Errors were encountered while processing:
acpid
acpi-support
ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...
 * Starting ACPI services...
invoke-rc.d: initscript apcid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on acpid; however:
  Package acpid is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
```

My guess is that I should get ubuntu-desktop functioning properly before either moving on to Feisty or staying put in Edgy. I already tried reinstalling all three packages via synaptic, but no dice. Any ideas? Thanks in advance.

---

### Post by ricardisimo on 2007-03-26
P.S. - libggi2 and mplayer updates are also clearly visible in Update Manager, but I can't select or deselect them. I imagine it's related, and that they both also depend upon acpid, but maybe not.

---

### Post by ricardisimo on 2007-03-26
Many thanks to BorgHunter for the [solution.]("http://www.ubuntuforums.org/showpost.php?p=2076766&postcount=4") I ran aptitude instead of apt-get, but either way does the trick.

---

### Post by DrJ00 on 2007-03-26
This fixed a problem for me after repair of a botched fiesty upgrade. Thanks for finding that.

---

