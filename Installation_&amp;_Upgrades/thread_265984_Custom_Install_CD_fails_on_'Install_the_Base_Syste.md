---
title: "Custom Install CD fails on 'Install the Base System'"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by jharr on 2006-09-26
I followed the install cd customizations as described in the wiki article [InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization"). I built the CD with very little modification, just wanted to get a baseline custom install CD built before I started actually doing customizations. Setup went fine until I got to just after the "Enter a username" prompt. Then it came up with this:

[IMG]http://grickle.org/ubuntu/screencaps/10-fail-vc1.png[/IMG]

... and on VC4:

[IMG]http://grickle.org/ubuntu/screencaps/10-fail-vc4.png[/IMG]

The syslog wasn't much help:

```

Sep 26 09:04:54 main-menu[2136]: DEBUG: virtual package created-fstab  
Sep 26 09:04:55 base-installer: info: Execution hook before debootstrap
Sep 26 09:04:55 base-installer: info: Running /usr/lib/base-installer.d/01save-logs
Sep 26 09:04:55 apt-install: Queueing package installation-report for later installation
Sep 26 09:04:55 base-installer: info: Running /usr/lib/base-installer.d/40netcfg
Sep 26 09:04:57 debootstrap: usage: /usr/lib/debootstrap/pkgdetails PKGS mirror packagesfile pkgs..
Sep 26 09:04:57 debootstrap:    or: /usr/lib/debootstrap/pkgdetails FIELD field mirror packagesfile pkgs..
Sep 26 09:04:57 debootstrap:    or: /usr/lib/debootstrap/pkgdetails GETDEPS packagesfile pkgs..
Sep 26 09:04:57 debootstrap:    or: /usr/lib/debootstrap/pkgdetails WGET% low high end reason
Sep 26 09:04:58 debootstrap: ar: 
Sep 26 09:04:58 debootstrap: Short read
Sep 26 09:04:58 debootstrap: 
Sep 26 09:04:58 debootstrap: zcat: 
Sep 26 09:04:58 debootstrap: Short read
Sep 26 09:04:58 debootstrap: 
Sep 26 09:04:58 debootstrap: chroot: 
Sep 26 09:04:58 debootstrap: cannot execute mount
Sep 26 09:04:58 debootstrap: : No such file or directory
Sep 26 09:05:36 init: ^MStarting pid 2080, console /dev/vc/2: '/bin/sh'
```

When I looked around, the /target folder did get mounted, but there wasn't anything in it besides etc, dev, proc, and some stuff in var.

I've posted various other things like screen caps (vc1 and vc4), syslog stuff, file listings, dmesg info, etc to a folder in case that helps anyone: [http://grickle.org/ubuntu]("http://grickle.org/ubuntu")

I'm going to skip a few steps in building the installer to see where my problems are (like customizing the repository, creating the extras folder, etc). If someone could provide some insight though, that'd save me boat loads of time (remastering ISO's in vmware takes some time).

Thanks,
James

---

