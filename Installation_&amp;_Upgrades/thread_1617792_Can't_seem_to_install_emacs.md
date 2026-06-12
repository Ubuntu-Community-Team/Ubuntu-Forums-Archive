---
title: "Can't seem to install emacs"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by BobvanderPoel on 2010-11-09
I'm going quite crazy here. Trying to install (well reinstall!) emacs here on my 10.10 meerkat.

I've tried installing emacs23 and emacs-snapshot and keep getting dependency errors during the install. I just tried dpkg --configure -a and that spews a bunch of errors and the suggestion that I report an error ... of course I have no idea to whom to report!

Here's the last dpkg stuff:

 bob$ sudo dpkg --configure -a
Setting up emacs-snapshot (1:20090909-1) ...
Byte-compiling add-on packages, please wait... failed.

!! Byte-compilation for emacs-snapshot failed!
!! This indicates a bug in one of the add-on packages
!! installed on your system, or a bug in Emacs itself.
!! Please file a bug report against emacs-snapshot
!! and attach the file /tmp/emacs-snapshot.sCBfxT
dpkg: error processing emacs-snapshot (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up emacs23-lucid (23.1+1-4ubuntu7) ...
emacs-install emacs23
install/a2ps: Handling install for emacsen flavor emacs23
Wrote /usr/share/emacs23/site-lisp/a2ps/path.elc
install/auctex: Setting up for emacs23 (log file: /usr/share/emacs23/site-lisp/auctex//CompilationLog)... done.
update-auctex-elisp[5686]: Further output will appear in: /var/log/auctex-emacs23.log.
install/dictionaries-common: Byte-compiling for emacsen flavour emacs23
>>Error occurred processing debian-ispell.el: File error (("Opening input file" "no such file or directory" "/usr/share/emacs23/site-lisp/dictionaries-common/debian-ispell.el"))
>>Error occurred processing ispell.el: File error (("Opening input file" "no such file or directory" "/usr/share/emacs23/site-lisp/dictionaries-common/ispell.el"))
>>Error occurred processing flyspell.el: File error (("Opening input file" "no such file or directory" "/usr/share/emacs23/site-lisp/dictionaries-common/flyspell.el"))
emacs-install: /usr/lib/emacsen-common/packages/install/dictionaries-common emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 4.
dpkg: error processing emacs23-lucid (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of auctex:
 auctex depends on emacs23 | emacs22 | emacs21 | emacs-snapshot; however:
  Package emacs23 is not installed.
  Package emacs23-lucid which provides emacs23 is not configured yet.
  Package emacs22 is not installed.
  Package emacs21 is not installed.
  Package emacs-snapshot is not configured yet.
dpkg: error processing auctex (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs-snapshot-gtk:
 emacs-snapshot-gtk depends on emacs-snapshot; however:
  Package emacs-snapshot is not configured yet.
dpkg: error processing emacs-snapshot-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs-snapshot
 emacs23-lucid
 auctex
 emacs-snapshot-gtk

Driving me nuts !!

I've tried removing all the emacs packages and then installing again. No difference.

Hope someone can help.

---

### Post by Cheesehead on 2010-11-09
Please file a bug report at [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) against the **emacs-snapshot package**.

If you still have the file /tmp/emacs-snapshot.sCBfxT, please attach it to the bug report - that's the add-on that failed to byte-compile, and that's what the Bug Squad needs to track down the problem. If you don't have it, try installing again, and look for a filename in the !! part of the error message, and attach that file.

Also, of course, please attach the entire error report to the bug, just like you did here.

There have been several similar bug reports filed, but none seem to have been helpful in tracking down the problem because the reporters did not have those /tmp files that failed to byte-compile.

Thanks for helping to make Ubuntu better. Your assistance may be key to finally squashing this bug once and for all.

---

### Post by BobvanderPoel on 2010-11-09
Okay ... I've never had much luck in getting results from the bug system ... but I'll try again. Reported as Bug #673350

BTW, here is the error log:

bob$ sudo cat /tmp/emacs-snapshot.sCBfxT
[sudo] password for bob: 
emacs-install emacs-snapshot
install/a2ps: Handling install for emacsen flavor emacs-snapshot
>>Error occurred processing *.el: File error (("Opening input file" "no such file or directory" "/usr/share/emacs-snapshot/site-lisp/a2ps/*.el"))
Wrote /usr/share/emacs-snapshot/site-lisp/a2ps/path.elc
emacs-install: /usr/lib/emacsen-common/packages/install/a2ps emacs-snapshot failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 4.

I'm guessing that there is some kind of permissions issue. I did have this installed as an update from 10.04, but that was giving me a few minor problems. So, I removed all the emacs and tried again. Even to the point of manually removing the various directories in /usr/share/emacs* and /etc/emacs*

Hope this can be figured out!

Thanks.

---

