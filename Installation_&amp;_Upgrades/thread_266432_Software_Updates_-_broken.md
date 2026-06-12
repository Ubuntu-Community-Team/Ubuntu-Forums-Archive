---
title: "Software Updates - broken"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by cabber on 2006-09-27
I've had this error for a while and cannot figure out what the resolution is:

When I click the software update in the top right corner I get this message:

```
Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.
```

When I run sudo apt-get dist-upgrade, I get:

[HTML]Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  compiz-core
The following packages have been kept back:
  compiz
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/237kB of archives.
After unpacking 968kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 86362 files and directories currently installed.)
Unpacking compiz-core (from .../compiz-core_0.0.13.38-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/bin/compiz.real', which is also in package compiz
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace compiz-gnome 0.0.13-0quinn32 (using .../compiz-gnome_0.0.13.38-0ubuntu3_i386.deb) ...
Unapplying schemas...
Done.
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_0.0.13.38-0ubuntu3_i386.deb (--unpack):
 trying to overwrite `/usr/share/gnome/wm-properties/compiz.desktop', which is also in package compiz
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-core_0.0.13.38-0ubuntu3_i386.deb
 /var/cache/apt/archives/compiz-gnome_0.0.13.38-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]

---

### Post by cabber on 2006-09-27
I also unable to open Synaptic Manager

---

