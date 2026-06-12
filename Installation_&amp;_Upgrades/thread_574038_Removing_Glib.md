---
title: "Removing Glib"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by jalirious on 2007-10-12
Hello, after a disaster that recursively wiped out my gtk files (don't ask) I am trying to install gtk+-2.8.20.

There is a catch. As gtk is gone I cannot get any new Xterms, browers or the synaptic package manager to open. When the computer shuts down it's game over.

So far I have installed various things the gtk compilation previously failed on (pango, cairo, atk, etc), via (./configure, make, make install, ldconfig) but am stuck on this point;

(after ./configure)

checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.8.5...
*** 'pkg-config --modversion glib-2.0' returned 2.8.5, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.8.5 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/pub/gtk/](ftp://ftp.gtk.org/pub/gtk/).

I think GLIB 2.10.3 came from an rpm package I tranferred into a debian package via alien, then forced into /usr/lib/ (smart move, eh)

The system (i.e locate, find -name, whereis) cannot find glib-2.10.3 apart from this compilation crash. I have tried installing the package again, configuring it with various prefixes, then 'sudo make uninstall'. No joy.

As for modifying my LD_LIBRARY_PATH, is this not done in bash_profile or bashrc? As I can't load a new Xterm this seems pointless.

yes, apt-get upgrade (update), apt-get aptitude build essential, etc -> Nothing.

Think I'm going to throw in the towel soon and do a fresh ubuntu install. Ideas?

---

### Post by jalirious on 2007-10-12
I got rid of this by compiling then make uninstall the 2.8.5, then installing the later glib version. It seems once ubuntu has seen a later version of glib it can never let go. Now onto the next 1000 errors...

---

### Post by W8eR_CZech on 2007-10-20
Hov exactly did jou uninstall the old version in GLIB? Thx in advance

---

### Post by jalirious on 2007-11-20
Don't remember, sorry. I did eventually manage to compile it from source without errors, but then my launchers didn't work -> Fresh install.

---

### Post by pazzypunk on 2007-11-24
I'm having a similar problem (trying to install xmms).

I installed 1.2.0 at first, *finally* got that to work, and then realized ... it was too old.
So then I installed 2.12 and tried to install xmms again. I still had the error that it was pointing to the old one.

So I go back to the old directory and do 'make uninstall', then for good measure, compile and re-install 2.12.

Now when I try to install xmms, I get this error message:

```
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```

I've gone into the Synaptic Package Manager and tried installing everything that had libglib-2.0-0 (dbg, cil, data, dev, doc). I'm still getting the same error message.

This is day number 2 with Xubuntu, so i am a total n00b. If anyone has any ideas how to fix this problem, I would appreciate it!

---

### Post by jalirious on 2007-11-30
Try reinstalling what you want rid of in synaptic, then 'complete uninstall' it. If you're on day 2, then a fresh install is your best bet I think. Ben.

---

