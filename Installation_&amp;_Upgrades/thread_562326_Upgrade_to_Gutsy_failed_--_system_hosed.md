---
title: "Upgrade to Gutsy failed -- system hosed"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by mail480697 on 2007-09-28
I tried to upgrade my feisty to gutsy today.  No luck!  I did this:

Alt-F2 -- entered command update-manager -d

after the "do you really want to do this?" prompt, things took off.

After downloading all the stuff, it started to install.  I started getting messages like:

"<pakage> may be in a not working state"

I could not (easily) abort the install, so I clicked the only button available, "Close" which just closed the error message and continued.

After about 25 of these (I lost count), the upgrade just stopped.  I tried to restart Gnome, but it wouldn't restart.  Eventually I ran apt-get <anything> and was told to run dpkg --configure -a

I tried that and got lots of dependency errors.  So I ran dpkg -C and got:
================
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 shared-mime-info     FreeDesktop.org shared MIME database and spec
 libgnomevfs2-common  GNOME virtual file-system (common files)
 metacity-common      Shared files of lightweight GTK2 based Window Manager
 libgnome2-common     The GNOME 2 library - common files
 ubuntu-artwork       Ubuntu themes and artwork
 emerald              Decorator for beryl
 gnome-screensaver    a screen saver and locker
 gnome-applets        Various applets for GNOME 2 panel - binary files
 feisty-wallpapers    Feisty Wallpapers
 gnome-power-manager  frontend for gnome-powermanager

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:

<every package on my system>


The following packages need to do processing triggered by other
package(s).  This processing can be requested with
dpkg --triggers or the configure menu option in dselect:
 libc6                GNU C Library: Shared libraries

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 desktop-file-utils   Utilities for .desktop files
 capplets-data        configuration applets for GNOME 2 - data files
 gnome-media-common   GNOME media utilities - common files
 nautilus-data        data files for nautilus
 python2.5            An interactive high-level object-oriented language (versi

The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 gnome-cups-manager   CUPS printer admin tool for GNOME

The following packages have been triggered, but the trigger processesing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 libc6                GNU C Library: Shared libraries
=============

So, now my system is hosed. I can't go forward to gutsy.  I can't go backward to feisty.  What should I do?

Even 

sudo apt-get -f install

fails with:

Removing gnome-cups-manager ...
update-desktop-database: symbol lookup error: update-desktop-database: undefined symbol: g_option_context_new
dpkg: error processing gnome-cups-manager (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-cups-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2007-09-28
Save your data and do a fresh install.

---

