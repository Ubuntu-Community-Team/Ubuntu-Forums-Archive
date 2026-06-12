---
title: "problems with synaptic"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by biatchslappa on 2005-12-04
k i installed lilypond-data on ubuntu 5.10 with synaptic.  apparently the package has some conflicts and i cant reinstall it, uninstall it or install anything new without getting a bunch of problems.
installed version is latest version 2.5.3-9~breezy1

when i try and uninstall it i get this:
dpkg: error processing lilypond-data (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid

E: lilypond-data: Package is in a very bad inconsistent state - you should

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

so i run 'dpkg --configure -a' to correct the problem.

if i try and reinstall it i get this

Preconfiguring packages ...
Selecting previously deselected package lilypond-data.
(Reading database ... 172131 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb

E: /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: subprocess new post-removal script returned error exit status 1

get back into synaptic and its still there.  i dont really mind having it wasting space, but everytime i go to install something new it tries to reinstall it
anyway if somebody could tell me how to get synaptic to quit trying to install it everytime i go to upgrade or install other software id appreciate it.  this is the first problem ive run into with debians package system that i couldn't figure out.
thanx in advance.
will



 get back into synaptic and its still there.  i dont really mind having it wasting space, but everytime i go to install something new it tries to reinstall it

---

### Post by Leif on 2005-12-04
this is unrelated, but your nick (unless it's just my gutter mind and I'm reading it wrong) is offensive and violates the code of conduct for these forums.

---

### Post by biatchslappa on 2005-12-04
sorry about the choice of names, ill change it if i post again.

---

