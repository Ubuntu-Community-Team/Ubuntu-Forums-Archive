---
title: "apt-cache: Unmet dependencies but not installed ?!"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by mathiasv on 2005-11-29
Hi, after a messy upgrading, hoary to breezy, with manual installation of some packages I get this reaction on "apt-cache stats":
```
 
Total package names : 22513 (901k)
  Normal packages: 17614
  Pure virtual packages: 278
  Single virtual packages: 1051
  Mixed virtual packages: 171  
  Missing: 3399
  ...

```
In order to get more detailed information I try "apt-cache unmet", and in the end of a long output about many packages I get, as an example:
```

...
Package openoffice.org-l10n-nb version 1.1.5-0ubuntu1 has an unmet dep:
 Suggests: openoffice.org-hyphenation-nb
 Suggests: openoffice.org-thesaurus-nb
 Suggests: openoffice.org-help-nb
Package education-main-server version 0.803ubuntu1 has an unmet dep:
 Suggests: ncs
 Suggests: webmin-cupsadmin-skolelinux
 Suggests: webmin-dhcpd3

```
Then I try to remove the openoffice dictionary by "apt-get remove openoffice.org-l10n-nb" and get this:
```
Reading package lists... Done
Building dependency tree... Done
Package openoffice.org-l10n-nb is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
It seems apt is contradicting itself, and "apt-get --purge remove openoffice.org-l10n-nb" causes the same message. The problematic packages are shown as uinstalled also in synaptics.  "dpkg --purge openoffice.org-l10n-nb" gives me this:
```

dpkg - warning: ignoring request to remove openoffice.org-l10n-nb which isn't installed.

```

I have tried to install and remove the mentioned packages in synaptics and in apt, but they still end up being unmet but also uninstalled. Is there a package list in apt-cache to reset?

Thanks, 
Mathiasv

---

### Post by Xian on 2005-11-29
You are really, really confused. 
Okay, first of all here is my output of the command:

```
$ apt-cache stats
Total package names : 22523 (901k)
  Normal packages: 17644
  Pure virtual packages: 285
  Single virtual packages: 1047
  Mixed virtual packages: 175
  Missing: 3372
```

Looks very similar to your's.... :)

The pkgs listed with the 'apt-cache unmet' command generally are designated as such because they are not installed and therefore are missing deps which would be present if the parent application were actually on your system.

For example, try and install your mysterious pkg.
You'll notice it will begin pulling in those missing deps.

```
$ sudo apt-get install openoffice.org-l10n-nb
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libneon23 openoffice.org openoffice.org-bin openoffice.org1-debian-files
Suggested packages:
  openoffice.org-help ooqstart-gnome oooqs-kde unixodbc cupsys-bsd prelink
  openoffice.org-hyphenation openoffice.org-thesaurus openoffice.org-mimelnk
  openoffice.org-gtk-gnome openoffice.org-kde openoffice.org-gnomevfs
  xlibmesa-gl libgl1 openclipart myspell-dictionary-nb
  openoffice.org-hyphenation-nb openoffice.org-thesaurus-nb
  openoffice.org-help-nb
The following NEW packages will be installed:
  libneon23 openoffice.org openoffice.org-bin openoffice.org-l10n-nb
  openoffice.org1-debian-files
```

---

### Post by mathiasv on 2005-11-30
Well, I am in a low state of confusion compared to other times working with Ubuntu :-)

But I don't want to install for example "openoffice.org-l10n-nb", so is there a way to remove it and the rest of them from apt-cache? Otherwise apt will keep complaining about uninstalled packages.

---

### Post by Xian on 2005-11-30
[QUOTE=mathiasv]But I don't want to install for example "openoffice.org-l10n-nb", so is there a way to remove it and the rest of them from apt-cache? Otherwise apt will keep complaining about uninstalled packages.[/QUOTE]
Where is it complaining about unistalled packages?
Do an -f install command...does it list any heldback or needed pkgs?

$ sudo apt-get -f install

---

### Post by mathiasv on 2005-12-01
I mean, apt is complaining about missing (uninstalled) packages for packages which are not installed either :confused: 

Unforunately, "apt-get -f install" does not change anything.

---

