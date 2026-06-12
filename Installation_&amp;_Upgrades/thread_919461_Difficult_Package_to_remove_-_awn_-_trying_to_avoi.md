---
title: "Difficult Package to remove - awn - trying to avoid reinstalling ubuntu"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by ironwolfe on 2008-09-14
I am running Gutsy on AMD machine and am having some serious problems removing avant-window-navigator-bzr.  When I try to remove it get the following errors:

```
E: avant-window-navigator-bzr: subprocess pre-removal script returned error exit status 250
E: awn-core-applets-bzr: subprocess pre-removal script returned error exit status 250
```

I also get the following:

```
dmbuch@dmbuch-desktop:~$ sudo apt-get remove awn-core-applets-bzr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-alsaaudio python-awn-bzr python-libgmail
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  awn-core-applets-bzr
0 upgraded, 0 newly installed, 1 to remove and 17 not upgraded.
Need to get 0B of archives.
After unpacking, 15.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145977 files and directories currently installed.)
Removing awn-core-applets-bzr ...

(gconftool-2:19903): GConf-WARNING **: Failed to load source "xml:readwrite:/var/lib/gconf/defaults": Couldn't resolve address for configuration source: Can't read from or write to the XML root directory in the address "xml:readwrite:/var/lib/gconf/defaults"

GConf-ERROR **: file gconftool.c: line 918 (main): assertion failed: (err == NULL)
aborting...
dpkg: error processing awn-core-applets-bzr (--remove):
 subprocess pre-removal script returned error exit status 250
Errors were encountered while processing:
 awn-core-applets-bzr
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried 

```
dmbuch@dmbuch-desktop:~$ sudo dpkg --configure -a
dmbuch@dmbuch-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

```

and no luck.  I think the info file prerm script is hosed, I can't even find it... Any help would be much appreciated... Is there anyway to remove this package without synaptic?

I can't run any upgrades as well....

I get an error saying 
"The configuration defaults for GNOME Power Manager have not been installed correctly.  Please contact your administrator"

life sucks... help please...

---

### Post by Pumalite on 2008-09-14
Comment out the corresponding lines in your sources.list and try the removal again.

---

