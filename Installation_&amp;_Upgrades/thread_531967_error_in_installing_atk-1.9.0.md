---
title: "error in installing atk-1.9.0"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by narenvenkat on 2007-08-22
hi frenz

i am a new user to ubuntu ,plzzz can anyone of u tell me how to get rid of this error when installing atk 1.9.0 for iNSpect tool for ns2, 

**********************************************************
checking for some Win32 platform... no
checking for native Win32 platform... no
checking for aclocal flags... 
c[B]hecking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.5.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.12.0, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files[/B]
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.
*****************************************************************************

thnx in advance
naren

---

### Post by W8eR_CZech on 2007-10-20
I've got the same problem. Begging for help

---

### Post by cepogue on 2008-01-30
You have to modify your /etc/ld.so.conf file.

su - (or use sudo)

vi /etc/ld.so.conf

Add the an entry of the path you installed glib.  For example, on my machine, downloaded the tarball to my desktop and copied it over to /usr/local/src.  From there, I unpacked the tarbal and installed glib.  So, my entry in ld.so.conf looks like this...

/usr/local/src

Once you make the modification, just type ldconfig from the command like to export your new change.

Kew?  Iorked fine for me after that modification.  If for some reason you forgot where you installed it, just do a search for the term glib...

find / -name glib

---

