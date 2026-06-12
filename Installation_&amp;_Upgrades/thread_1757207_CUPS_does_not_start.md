---
title: "CUPS does not start"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by rosanna.sordo on 2011-05-13
Hi, after upgrading to natty cups does not start, either at the boot or manually. 
I tried uninstall cups (and all related package, as much as possible) and reinstall it, but nothing. 

This is the error message I have from apt-get whe I try to install cups (cups-driver-gutenprint is requested by apt-get):

...
Setting up cups (1.4.6-5ubuntu1) ...
profile has merged rule with conflicting x modifiers
Failing on accept perms 1
ERROR processing regexs for profile /usr/sbin/cupsd, failed to load
start: Job failed to start
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups-driver-gutenprint:
 cups-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
dpkg: error processing cups-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 cups
 cups-driver-gutenprint
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone help?

---

### Post by rosanna.sordo on 2011-07-04
no help? really? still  without CUPS!!

---

### Post by troudobus on 2011-08-17
Hi Rosanna and readers,

 I encounter exactly the same problem, though it did not appear right after upgrading.
Did you manage to solve it?

Thanks for reading

---

### Post by troudobus on 2011-08-17
Fixed:

- I had tried the package reinstallation in synaptics. It did not solve.
- Just tried to remove completely within synaptics then install the proposed package via Update Manager.

Seems a solution, it worked nicely and I have no more error messages when I install packages or run Update manager.

---

### Post by rosanna.sordo on 2011-08-26
I tried to uninstall/reinstall several times (purging and so on) cups&co, no improvement.
I decided for a fresh install of natty: my system was very stable, but was installed in 2006 (edgy --> ... --> natty), so perhaps it was time.

---

### Post by tshirtdr1 on 2011-08-27
Did you install or upgrade edubuntu with this? I recently installed edubuntu and broke CUPS. I uninstalled edubuntu and CUPS is working again. Wanted to post this error. Uninstall Edubuntu.

---

