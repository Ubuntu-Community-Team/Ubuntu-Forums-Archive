---
title: "Problem Installing k3b"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by gwinston99 on 2007-09-06
I am running Kubuntu Feisty.  After an update the other day, k3b stopped working.  I did an apt-get remove on it and then tried to reinstall.  I have been unsuccessful after a couple of days.  Here is the output when I try to reinstall:

gregg@finance1:~$ sudo dpkg --configure -a
gregg@finance1:~$ sudo apt-get install k3b
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  k3b: Depends: kdelibs4c2a (>= 4:3.5.7-1) but 4:3.5.7-0ubuntu1~feisty2 is to be installed
       Depends: libart-2.0-2 (>= 2.3.18) but 2.3.17-1 is to be installed
       Depends: libdbus-1-3 (>= 1.1.1) but 1.0.2-1ubuntu4 is to be installed
       Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1.1 is to be installed
       Depends: libgcc1 (>= 1:4.2-20070516) but 1:4.1.2-0ubuntu4 is to be installed
       Depends: libk3b3 (>= 1.1~svn20070723.0411+r691290) but it is not going to be installed
       Depends: libmusicbrainz4c2a (>= 2.1.5) but 2.1.4-1ubuntu2 is to be installed
       Depends: libstdc++6 (>= 4.2-20070516) but 4.1.2-0ubuntu4 is to be installed
       Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
E: Broken packages


Please help.

Thanks,

Gregg

---

### Post by frank95com on 2007-09-06
Is the new version you are triing to install different form ubuntu's repository one?
Had you create a new deb package from source (or snapshot)? If yes had you create a sigle package?
Maybe you had downloaded the k3b deb but you didn't downloaded the lib3kb3 package so the program can't work without its libraries.
:)

---

