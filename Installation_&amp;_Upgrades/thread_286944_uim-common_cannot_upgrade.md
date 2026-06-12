---
title: "uim-common cannot upgrade"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by leohart on 2006-10-28
I was trying to upgrade from Dapper to Edgy with the official upgrade method.

However, apt-get spits out problem. 

Dpkg warning - old pre-removal script killed by signal (interrupt)
The dpkg stops so had to hit Ctrl-C

Now my GUI wouldn't get in and it says the "greeter application fails to load".

What should I do now? a bunch of uim packages depends on uim-common and it keeps spitting out error on me when I try to run apt-get dist-upgrade.

---

### Post by satellite360 on 2006-10-30
I also have a problem with uim-common following the upgrade to Edgy.  The update-manager failed to update uim-common so I ran 'sudo apt-get install -f' in the terminal and got the following:
> 
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  uim-common
The following packages will be upgraded:
  uim-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/819kB of archives.
After unpacking 336kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 106239 files and directories currently installed.)
Preparing to replace uim-common 1:1.0.0-1ubuntu1 (using .../uim-common_1%3a1.2.1-3ubuntu2_all.deb) ...
ERROR: unbound variable (errobj is-set-ugid?)

*backtrace*
>>(is-set-ugid?)
>>(if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ()))))
>>(define uim-plugin-lib-load-path (if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ())))))
>>(require "plugin.scm")
>>(require "init.scm")
>>(*catch (quote errobj) (require "init.scm"))
>>(eq? (quote *init.scm-loaded*) (*catch (quote errobj) (require "init.scm")))

ERROR: unbound variable (errobj custom-reload-customs)

ERROR: unbound variable (errobj custom-choice-rec-sym)

ERROR: unbound variable (errobj plugin-alist)

ERROR: wta to car (errobj t)

The terminal hung.  When I hit Ctrl+C I got the following:

> dpkg: error processing /var/cache/apt/archives/uim-common_1%3a1.2.1-3ubuntu2_all.deb (--unpack):
 dpkg: warning - old pre-removal script killed by signal (Interrupt)

Errors were encountered while processing:
 /var/cache/apt/archives/uim-common_1%3a1.2.1-3ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

After a reboot I can no longer log in.  Keep getting the following message:
> The greeter application appears to be crashing. Attempting to us a different one.

---

### Post by plumcreek on 2006-10-30
I'm also getting the same error. No ideas yet on how to fix it, but it is definitely an annoying problem.

---

### Post by plumcreek on 2006-10-30
Here's the solution:
[https://launchpad.net/distros/ubuntu/+source/uim/+bug/63431](https://launchpad.net/distros/ubuntu/+source/uim/+bug/63431)

---

### Post by satellite360 on 2006-10-31
lifesaver - thanks plumcreek

---

### Post by Hiroshima on 2007-11-24
> **plumcreek said:**
> Here's the solution:
[https://launchpad.net/distros/ubuntu/+source/uim/+bug/63431](https://launchpad.net/distros/ubuntu/+source/uim/+bug/63431)

The advice there was:

go to /var/lib/dpkg/info/uim-common.prerm, put exit 0 right after the comments (lines beginning with '#')

will see how it works.

Hiroshima

---

### Post by Hiroshima on 2007-11-24
Yep, it worked for me as well.

step by step:

> cd /var/lib/dpkg/info
sudo gedit uim-common.prerm

then insert the "exit 0" after the commented areas
I could not remove uim-common from synaptic even after that, so:

> sudo apt-get remove uim-common

I haven't reinstalled uim-common yet, I will wait until I have finished upgrading, however, the first step to 6.10 is done.

---

