---
title: "Package manager won't open"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by shaviro on 2011-05-05
The other day I successfully upgraded to Natty on my Asus EeePC netbook. But now the package manager does not work, I am unable to look for, much less install, upgrades. There's a permanent message in my title bar:
-------------------------------
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
-----------------------------------

Any suggestions on what I need to do to correct this?

thanks

---

### Post by dino99 on 2011-05-05
delete it:

sudo rm /var/cache/apt/archives/*

or sudo apt-get autoremove

(might be a corrupt package index on the us.archive)

---

### Post by shaviro on 2011-05-05
Thanks, I deleted the corrupt files and everything now works again.

---

### Post by orangep on 2011-05-07
> **dino99 said:**
> delete it:

sudo rm /var/cache/apt/archives/*

or sudo apt-get autoremove

(might be a corrupt package index on the us.archive)

Sorry, but 
rm /var/cache/apt/archives/*

will just delete all of the downloaded .deb packages.
We want:

sudo rm /var/lib/apt/lists/* -vf

Which will get rid of the bad list.

---

