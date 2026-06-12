---
title: "Corrupt .tar files for restricted drivers"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by pofigster on 2007-07-20
So, I just installed Ubuntu again (it's been a nightmare getting it installed!) and I was letting it update itself with the most current files and what not when I got this:

(Reading database ... 104679 files and directories currently installed.)
Unpacking linux-restricted-modules-2.6.20-16-generic (from .../linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.29_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.29_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.29_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I really can't install any other files or update anything until this gets installed (I'm trying to run a LAMP server and it complains about this not being installed).

Any pointers?  Is this just a temporary problem that'll get fixed?

---

### Post by pofigster on 2007-07-20
Ok, I figured out a solution.  Since the Synaptic Package manager was getting corrupt files, I just went to the Ubuntu website and searched for the package, ran it, it installed fine and now everything works.  Yay!

---

