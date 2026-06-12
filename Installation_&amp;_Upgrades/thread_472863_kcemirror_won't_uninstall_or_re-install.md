---
title: "kcemirror won't uninstall or re-install"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by smilliken on 2007-06-13
am trying to set up SynCE and have run into a snag. I can't install kcemirror nor uninstall it. I've tried using kpackage and synaptic. These are the error messages I get:

Removal
The following packages will be REMOVED:
kcemirror
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 340kB disk space will be freed.
dpkg: error processing kcemirror (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
what(): basic_string::_S_construct NULL not valid
Aborted
RESULT=134

Re-install
kcemirror is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/88.2kB of archives.
After unpacking 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
kcemirror
Authentication warning overridden.
Selecting previously deselected package kcemirror.
(Reading database ... 79253 files and directories currently installed.)
Preparing to replace kcemirror 0.1.4-3ubuntu1 (using .../kcemirror_0.1.4-3ubuntu1_i386.deb) ...
Unpacking replacement kcemirror ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing /var/cache/apt/archives/kcemirror_0.1.4-3ubuntu1_i386.deb (--unpack):
subprocess new post-removal script returned error exit status 1
touch: missing file operand
Try `touch --help' for more information.
dpkg: error while cleaning up:
subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
/var/cache/apt/archives/kcemirror_0.1.4-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
RESULT=100


I've re-booted several times and this seems to do nothing,

Also tried:

dpkg –remove –force-remove-reinstreq kcemirror

with the following results:

root@1[Scott]# dpkg --remove --force-remove-reinstreq kcemirror


dpkg - warning, overriding problem because --force enabled:
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
(Reading database ... 79277 files and directories currently installed.)
Removing kcemirror ...
touch: missing file operand
Try `touch --help' for more information.
dpkg: error processing kcemirror (--remove):
subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
kcemirror

Any help, much appreciated.

Scott

---

