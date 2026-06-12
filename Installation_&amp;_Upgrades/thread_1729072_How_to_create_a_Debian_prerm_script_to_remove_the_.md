---
title: "How to create a Debian prerm script to remove the distro likewise and replace with"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by jeforubu on 2011-04-14
How do I script the removal of likewise-open packages from the maverick distro and replace with the Likewise6 ?

so I have tried using prerm, preinst and postrm to remove the existing distro with a dpkg --purge of the packages:

Selecting previously deselected package likewise6.
(Reading database ... 343165 files and directories currently installed.)
Unpacking likewise6 (from .../likewise6_6.0.0.8336_all.deb) ...
preinst
dpkg: status database area is locked by another process
dpkg: error processing /tmp/lw6/likewise6_6.0.0.8336_all.deb (--install):
 subprocess new pre-installation script returned error exit status 2
remove from postrm
dpkg: status database area is locked by another process
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Errors were encountered while processing:
 /tmp/lw6/likewise6_6.0.0.8336_all.deb
johne@mylaptop:/usr/local$ dpkg -l|grep likew
ii  likewise-open                                         5.4.0.42111-2ubuntu2                                  Authentication services for Active Directory Domains
ii  likewise-open-gui                                     5.4.0.42111-2ubuntu2                                  Desktop utility for joining Active Directory domains
ii  likewise-open-server                                  5.4.0.42111-2ubuntu2                                  Likewise-CIFS and related server components
iHR likewise6                                             6.0.0.8336                                            (no description available)

---

