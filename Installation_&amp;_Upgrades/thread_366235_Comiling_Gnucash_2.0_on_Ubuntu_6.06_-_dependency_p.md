---
title: "Comiling Gnucash 2.0 on Ubuntu 6.06 - dependency problems"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by rwissner on 2007-02-20
(I'm sorry if this is the wrong category - I thought it was the most appropriate one)
I'm trying to install Gnucash 2.0.5 from source on a 6.06 installation since I would very much like to have Gnucash > 2 with the support for online banking enabled and would also like to use cryptsetup (which, as far as I know does not work properly with the startup scripts in Edgy) and therefore I can't update to Edgy.
I installed all the dependencies I could using the repositories; however, I got an error that Gnucash depends on GLIB >=2.4, with the version provided in the Dapper repository being 2.1. I compiled and installed (using checkinstall) the most recent version of GLIB (2.9.6 - might not have been the best idea...). However, the error message is now:

*** 'pkg-config --modversion glib-2.0' returned 2.9.6, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
 
Additonally, the version of Glib I compiled is not recognised as  version of the glib package, i.e. I cannot remove the old package without removing half of my installed software. Do you have any suggestions what I could do to solve this problem? Is there a way to install the "modern" version of the libraries along with the older versions (similarly to glib version 1.2 and 2.1 being installed)? Thanks for any help.

---

### Post by altonbr on 2008-03-31
Maybe there is a repository for GnuCash in 6.06... I'll look around.

---

