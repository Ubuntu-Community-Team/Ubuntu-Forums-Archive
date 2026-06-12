---
title: "Configuring emacs24 on Ubuntu 14.04"
date: 2014-10-02
forum: Installation &amp; Upgrades
---

### Post by dunn3 on 2014-10-02
Howdy! Since I installed Ubuntu 14.04, my update manager always says if failed.  When it first happened, it did say it something about emacs24, that it couldn't configure or that it wasn't configured.

I have tried a number of times to fix this, but to no avail.  I know I have run the ppa command from [this thread]("http://ubuntuforums.org/showthread.php?t=1807615").  I have started emacs but that didn't help (I don't use emacs for editing).

Now, I am trying to install [pandoc]("http://johnmacfarlane.net/pandoc/installing.html"), which needs Haskell, which needs emacs, which needs emacs24. I can't seem to do it. I would also like to be reassured that I am getting the correct updates so I would like to get rid of those errors.

Sorry to ask, but I've been trying on and off for a few weeks.

Here are some attempts:

```

dunnamin@a:~$ sudo apt-get install haskell-platform
Reading package lists... Done
Building dependency tree       
Reading state information... Done
haskell-platform is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up emacs24 (24.3+1-2ubuntu1) ...
Install cmake-data for emacs24
install/cmake-data: Byte-compiling for emacs24
ln: failed to create symbolic link ‘/usr/share/emacs24/site-lisp/cmake-data/cmake-mode.el’: File exists
Wrote /usr/share/emacs24/site-lisp/cmake-data/cmake-mode.elc
Install emacsen-common for emacs24
emacsen-common: Handling install of emacsen flavor emacs24
Wrote /etc/emacs24/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs24/site-lisp/debian-startup.elc
Install gforth for emacs24
install/gforth: Byte-compiling for emacsen flavour emacs24

In toplevel form:
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
ERROR: install script from gforth package failed
dpkg: error processing package emacs24 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs24 | emacs24-lucid | emacs24-nox; however:
  Package emacs24 is not configured yet.
  Package emacs24-lucid is not installed.
  Package emacs24-nox is not installed.

dpkg: error processing package emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 emacs24
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)

dunnamin@a:~$ sudo apt-get install emacs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emacs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up emacs24 (24.3+1-2ubuntu1) ...
Install cmake-data for emacs24
install/cmake-data: Byte-compiling for emacs24
ln: failed to create symbolic link ‘/usr/share/emacs24/site-lisp/cmake-data/cmake-mode.el’: File exists
Wrote /usr/share/emacs24/site-lisp/cmake-data/cmake-mode.elc
Install emacsen-common for emacs24
emacsen-common: Handling install of emacsen flavor emacs24
Wrote /etc/emacs24/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs24/site-lisp/debian-startup.elc
Install gforth for emacs24
install/gforth: Byte-compiling for emacsen flavour emacs24

In toplevel form:
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
ERROR: install script from gforth package failed
dpkg: error processing package emacs24 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs24 | emacs24-lucid | emacs24-nox; however:
  Package emacs24 is not configured yet.
  Package emacs24-lucid is not installed.
  Package emacs24-nox is not installed.

dpkg: error processing package emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 emacs24
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)

dunnamin@a:~$ sudo apt-get install emacs24
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emacs24 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up emacs24 (24.3+1-2ubuntu1) ...
Install cmake-data for emacs24
install/cmake-data: Byte-compiling for emacs24
ln: failed to create symbolic link ‘/usr/share/emacs24/site-lisp/cmake-data/cmake-mode.el’: File exists
Wrote /usr/share/emacs24/site-lisp/cmake-data/cmake-mode.elc
Install emacsen-common for emacs24
emacsen-common: Handling install of emacsen flavor emacs24
Wrote /etc/emacs24/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs24/site-lisp/debian-startup.elc
Install gforth for emacs24
install/gforth: Byte-compiling for emacsen flavour emacs24
In toplevel form:
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
gforth.el:742:18:Error: Don't know how to compile nil
ERROR: install script from gforth package failed
dpkg: error processing package emacs24 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs24 | emacs24-lucid | emacs24-nox; however:
  Package emacs24 is not configured yet.
  Package emacs24-lucid is not installed.
  Package emacs24-nox is not installed.

dpkg: error processing package emacs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          E: Sub-process /usr/bin/dpkg returned an error code (1)

dunnamin@a:~$ sudo apt-get install --reinstall emacs24
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for emacs24:i386

dunnamin@a:~$ sudo apt-get install --reinstall emacs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for emacs:i386

```

Thanks!
-- dunn

---

