---
title: "[AMD64] Upgrading - ia32-libs error"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by np_ on 2005-11-16
Following [these upgrade notes](https://wiki.ubuntu.com/BreezyUpgradeNotes), I get the following.

```
Unpacking replacement ia32-libs
Replacing files in old package ia32-libs-openoffice.org
dpkg: error processing /cdrom/pool/main/i/ia32-libs/ia32-libs_1.4ubuntu4_amd64.
deb (--unpack)
unable to create './usr/lib32/libGL.so.1.2': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace base-passwd 3.5.9 (using .../base-passwd_3.5.10_amd64.deb)...
Unpacking replacement base-passwd...
Errors were encountered while processing:
   /cdrom//pool/main/i/ia32-libs/ia32-libs_1.4ubuntu_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Upon reboot, x doesn't start. The log is helpfully asks to show me is blank.

---

### Post by gratefulfrog on 2005-11-25
I got the same problem, and don't know what to do now that my machine is in some incoherent state...

I filed a bug: 20105, and am hoping...

---

### Post by np_ on 2005-11-25
I ended up backing up my home folder to a different partition and doing a fresh install of 5.10.

---

### Post by gratefulfrog on 2005-11-25
Here's the workaround solution:

```
$ sudo apt-get remove xorg-driver-fglrx
$ sudo apt-get -f install
$ sudo apt-get install xorg-driver-fglrx
```

and everything is beautiful again!

Please reply here with your results!

---

