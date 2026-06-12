---
title: "unable to install upgrades or software"
date: 2015-01-29
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2015-01-29
A few days ago I tried to install the package ESS Emacs Speaks Statistics.
The installation returned several error messages, but the software seems to work correctly.
Ever since, I've been unable to install software or updates.
As an example, I tried to install the package build-essential; it failed:

```
cavu{asb}153: sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essentials
cavu{asb}154: sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up emacs23 (23.4+1-4.1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/emacs23-x because link group emacs is broken
update-alternatives: warning: not replacing /usr/bin/emacs with a link
Install emacsen-common for emacs23
emacsen-common: Handling install of emacsen flavor emacs23
>>Error occurred processing /etc/emacs23/site-start.d/00debian-vars.el: File error (("Opening input file" "no such file or directory" "/etc/emacs23/site-start.d/00debian-vars.el"))
Wrote /usr/share/emacs23/site-lisp/debian-startup.elc
ERROR: install script from emacsen-common package failed
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: error processing package emacs23 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ess:
 ess depends on emacs23 | emacs22 | emacs21 | emacsen; however:
  Package emacs23 is not configured yet.
  Package emacs23-lucid which provides emacs23 is not installed.
  Package emacs22 is not installed.
  Package emacs21 is not installed.
  Package emacsen is not installed.
  Package emacs23-lucid which provides emacsen is not installed.
  Package emacs23 which provides emacsen is not configured yet.
  Package emacs24 which provides emacsen is not installed.
  Package emacs24-lucid which provides emacsen is not installed.

dpkg: error processing package ess (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs23
 ess
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I get the same error messages when I try to install the automatic updates.
It seems that the bug in ESS has added superfluous dependencies, so subsequence installations fail.
What can I do?  I'd like to be able to use ESS, but installing updates and other software is more important.

---

### Post by ian-weisser on 2015-01-29
> **asb3 said:**
> 
It seems that the bug in ESS has added superfluous dependencies, so subsequence installations fail.
What can I do?  I'd like to be able to use ESS, but installing updates and other software is more important.

Not superfluous dependencies. Apt remembers what you wanted to install, and keeps trying until you tell it to stop.

You can try 'sudo apt-get remove ess' to tell apt that you no longer want it.

If that doesn't work, there are other things to try.

---

### Post by asb3 on 2015-01-30
I don't want to remove ESS; it works correctly.  I just want to have apt-get stop returning the error messages.  What can I try?

---

### Post by ian-weisser on 2015-01-30
The blocker is: 
```
Package emacs23 is not configured yet.
```
because of
```
>>Error occurred processing /etc/emacs23/site-start.d/00debian-vars.el: File error (("Opening input file" "no such file or directory" "/etc/emacs23/site-start.d/00debian-vars.el"))
Wrote /usr/share/emacs23/site-lisp/debian-startup.elc
ERROR: install script from emacsen-common package failed
```

You can either fix the emacs23 install/config, or you can uninstall everything that depends upon that package, or you can live with apt broken.
Your choice.

---

