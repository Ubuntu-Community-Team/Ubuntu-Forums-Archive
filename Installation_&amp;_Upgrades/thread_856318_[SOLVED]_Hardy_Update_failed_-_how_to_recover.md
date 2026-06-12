---
title: "[SOLVED] Hardy Update failed - how to recover?"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by Bill Roberts on 2008-07-11
I was applying updates and the process failed.  The message indicated I should run dpkg --configure -a

This is the result:
xxxxx@desktop:~$ sudo dpkg --configure -a
[sudo] password for xxxxx: 
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.24-19-generic)
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-19-generic; however:
  Package linux-restricted-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.19.21); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

I have tried several times to install these packages singly or together.  The result is always the same.

This seems to be the basis:
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.24-19-generic)
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2

/boot contains this file: vmlinuz-2.6.24-16-generic

Any suggestions will be greatly appreciated.

---

### Post by hypest on 2008-08-01
Same problem here! Quite frustrating...

In my case, a probable cause may be that during the update, the /boot directory (separate partition) did not have enough space, but then again, I'm not sure this fact really was the reason..

please advise :)

---

