---
title: "Avoiding updates in preseeded install"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by JJar on 2013-07-01
I have a working preseeded install that boots off of a network using PXE. The install is entirely interaction free, and boots me up to a nice, functional 12.04LTS system. However, there is a particular update I wish to avoid. I can't seem to find any way of either disabling the precise-updates channel, or specifying that particular packages be frozen at a particular version in order to ensure that the system comes up in the state that I want. Is it possible to do this in a relatively simple way, or is it unsupported?

Thanks,
JJar

---

### Post by ajgreeny on 2013-07-01
You can pin any package so that it does not show in your update notifications.

To pin a package version add these lines to  /etc/apt/preferences:
```
Package: name
Pin: version # (number from repos that you currently have)
Pin-Priority: 1001
```

---

### Post by JJar on 2013-07-02
That could be a useful mechanism, if I can apply these sorts of restrictions during install time. The problem is that the installer us automatically updating from the precise-updates repo, and installing a version that I don't want. While I could attempt to automate a manual downgrade and clean up post-install, it would be nicer to be able to specify versions. Specifically it would be nice to just specify that precise-updates isn't touched at all, so that I can do elective upgrades after the install. This seems a reasonable strategy considering that this repo shouldn't contain any security updates.

---

### Post by ajgreeny on 2013-07-02
You do not have to accept the "Install updates when installing" option that is offered, along with installing multimedia codecs, early in the installation procedure; just remove the tick from the box or boxes, and continue.

---

### Post by JJar on 2013-07-03
When doing an interactive installation that would be the solution. However, it seems that when doing a preseeded network installation (so there are no interactive dialogue boxes of any kind, unless you count ones that only offer "Cancel" as an interaction), that the installer takes the core repository and distribution and automatically installs from <distro>-updates and <distro>-security.

---

### Post by ajgreeny on 2013-07-03
In which case, I haven't a clue.  Sorry!

---

