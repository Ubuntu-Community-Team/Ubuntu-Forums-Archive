---
title: "Apt - Dependencies - Apparent Inconsisteny Between RDepends and Depends"
date: 2021-03-07
forum: Installation &amp; Upgrades
---

### Post by Alan5127 on 2021-03-07
Hi All,

If I want to check the reverse dependencies of a package, I can use, for example:

```
$ apt-cache rdepends virt-viewer
```

which lists the following reverse dependencies:

```
virt-viewer
Reverse Depends:
  libspice-client-glib-2.0-8
  virtinst
  virt-manager
  virtinst
  virt-manager
```


I am guessing that means that, if I ask for the dependencies of each of:

libspice-client-glib-2.0-8
virtinst
virt-manager

then their lists would each include 'virt-viewer'?

However, if I ask for the dependencies of 'virt-manager', the dependencies list does not include 'virt-viewer', rather it is listed under the 'Suggests' list:

```
$ apt show virt-manager

Package: virt-manager
Version: 1:2.2.1-3ubuntu2.1
Priority: optional
Section: universe/admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Libvirt Maintainers <pkg-libvirt-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 6,515 kB
Depends: gir1.2-appindicator3-0.1, gir1.2-gtk-3.0 (>= 3.10), gir1.2-gtk-vnc-2.0, gir1.2-gtksource-4, gir1.2-libosinfo-1.0, gir1.2-libvirt-glib-1.0, gir1.2-vte-2.91, librsvg2-common, python3-dbus, python3-gi, python3-gi-cairo, python3-libvirt (>= 0.7.1), virtinst (>= 1:2.2.1-3ubuntu2.1), dconf-gsettings-backend | gsettings-backend, python3:any
Recommends: gir1.2-spiceclientglib-2.0, gir1.2-spiceclientgtk-3.0, libvirt-daemon-system (>= 1.2.7)
Suggests: gir1.2-secret-1, gnome-keyring, python3-guestfs, ssh-askpass, virt-viewer
Homepage: http://virt-manager.org/
Download-Size: 864 kB
APT-Sources: http://nz.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages
Description: desktop application for managing virtual machines
 It presents a summary view of running domains and their live performance &
 resource utilization statistics. A detailed view presents graphs showing
 performance & utilization over time. Ultimately it will allow creation of new
 domains, and configuration & adjustment of a domain's resource allocation &
 virtual hardware.  Finally an embedded VNC client viewer presents a full
 graphical console to the guest domain.
 .
 NOTE: the GUI is still considered experimental.


```


I had understood that, if a package is listed as a reverse dependency (rdepends) then it followed that the reverse dependency would list the package as a dependency.

This seems inconsistent to me, but my experience tells me that it is more likely that I just don't get it!

Please can someone help me understand?


Thanks,

Alan.

---

### Post by rsteinmetz70112 on 2021-03-07
I don't know the actual answer but it seems to me that if  'virt-manager' suggests 'virt-viewer' then 'virt-manager' is required for 'virt-viewer' but 'virt-viewer' is not required for 'virt-manager'. 
That is 'virt-manager' will run without 'virt-viewer' but 'virt-viewer' will not run without 'virt-manager'.

---

### Post by Alan5127 on 2021-03-07
> **rsteinmetz70112 said:**
> I don't know the actual answer but it seems to me that if  'virt-manager' suggests 'virt-viewer' then 'virt-manager' is required for 'virt-viewer' but 'virt-viewer' is not required for 'virt-manager'. 
That is 'virt-manager' will run without 'virt-viewer' but 'virt-viewer' will not run without 'virt-manager'.

The definitions / criteria for Depends, Recommends, Suggests (and also Enhances, and Pre-Depends) can be found here:

[https://www.debian.org/doc/debian-policy/ch-relationships.html](https://www.debian.org/doc/debian-policy/ch-relationships.html)

In particular, Section 7.2 expands on each.

'Suggests' is fairly weak, at least compared to depends and recommends, being:

> This is used to declare that one package may be more useful with one or more others. Using this field tells the packaging system and the user that the listed packages are related to this one and can perhaps enhance its usefulness, but that installing this one without them is perfectly reasonable. 


My reading of that would suggest that something seems inconsistent as per my OP?


i have read the man page for apt-cache, but I probably need to re-read it - I'm sure the way this works is correct - I must have just missed something.

Thanks,

Alan.

---

### Post by Alan5127 on 2021-03-07
Okay, I just re-read the apt-cache man pages.

The command has a number of options, including:

--no-pre-depends
--no-depends
--no-recommends
--no-suggests
--no-conflicts
--no-breaks
--no-replaces
--no-enhances

By default apt-cache -rdepends lists ALL dependencies, but you can restrict it with the above options.


All makes sense now.

Thanks,

Alan.

---

### Post by rsteinmetz70112 on 2021-03-07
I think the quote above is consistent with my suggestion that  'virt-manager' is required for 'virt-viewer' but 'virt-viewer' is not required for 'virt-manager'. 
That would mean that 'virt-viewer' depends on 'virt-manager' as 'rdepends' says, but 'virt-manager' does not depend on 'virt-viewer'. 
Try removing virt-viewer and see what other packages are to be removed.```
 sudo apt remove virt-viewer --simulate
```
I suspect the only package to be removed would be 'virt-viewer'.

---

