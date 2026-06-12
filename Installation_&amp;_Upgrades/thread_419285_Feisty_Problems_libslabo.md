---
title: "Feisty Problems: libslabo"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by spyke01 on 2007-04-22
After upgrading to feisty from dapper i am having the following issue. If i run sudo apt-get upgrade i get this:
```

spyke01@phoenix:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  apport: Depends: python-apport (>= 0.43) but it is not installed
  apport-gtk: Depends: python-apport (>= 0.45) but it is not installed
  gnome-control-center: Depends: libslab0 but it is not installed
E: Unmet dependencies. Try using -f.

```

So of course i run sudo apt-get -f install i get the following errors:
```

spyke01@phoenix:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libslab0 python-apport
The following packages will be REMOVED:
  python-apport-utils
The following NEW packages will be installed:
  libslab0 python-apport
0 upgraded, 2 newly installed, 1 to remove and 222 not upgraded.
5 not fully installed or removed.
Need to get 0B/229kB of archives.
After unpacking, 524kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 189494 files and directories currently installed.)
Unpacking libslab0 (from .../libslab0_1%3a2.18.1-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libslab0_1%3a2.18.1-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libslab.so.0.0.0', which is also in package gnome-main-menu
Errors were encountered while processing:
 /var/cache/apt/archives/libslab0_1%3a2.18.1-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas on this issue?

---

### Post by spyke01 on 2007-04-23
*bump*

---

### Post by spyke01 on 2007-04-23
dpkg -r gnome-main-menu fixed this issue

---

### Post by wyth on 2007-04-23
You could try removing the offending packages and then upgrading.  Make a note of them though, and maybe reinstall.

To completely remove, do sudo apt-get -p <package name>

---

