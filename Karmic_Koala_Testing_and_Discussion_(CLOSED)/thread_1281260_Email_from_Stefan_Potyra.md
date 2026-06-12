---
title: "Email from Stefan Potyra"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Bert Mariën on 2009-10-03
Wouldn't it prevent many questions if you would make the email send by Stefan Potyra a sticky thread?

---+---
help fixing packages that fail to build from source


Hi folks,

the karmic changes in the toolchain (gcc-4.4, newer eglibc) have sadly 
produced a lot of fallout: The number of packages that failed to build during 
the latest rebuild test is enourmous. You can see the list at

<http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20090909-karmic.html>

The list is refreshed every two hours, marking uploaded packages in the 
superseded section.

Please help fixing these, and please also forward your changes to Debian.

A large number of issues can be dealt with easily. The most prominent ones 
are:

* C++ packages failing due to the new (ISO compliant) definitions of c string
  methods. In C, these functions receive a const char * and return a char *,
  hence allowing an implicit const-cast.
  g++-4.4 together with our new eglibc have overloaded counterparts, which
  - either use a char * as argument and return a char *
  - or use a const char * as argument and return a const char *.
  Often the solution is to simply add a const somewhere.

* Local definitions of getline: While getline used to be a GNU extension, it's
  nowadays part of POSIX, living in <stdio.h>. Sadly getline is quite a common
  name, and is defined in a number of packages.
  The solution here is likewise simple: Just rename the definition in the
  package.


Martin Michlmayr did a rebuild of unstable against gcc-4.4 (using an older 
eglibc than we have though), so a number of failures might already have 
patches sitting in BTS or are already fixed in unstable.
You can find the complete list of gcc-4.4 related bug reports from the 
unstable rebuild at

<http://bugs.debian.org/cgi-bin/pkgreport.cgi?users=debian-gcc@lists.debian.org;tag=ftbfs-gcc-4.4>

Please also take a look at the sponsors queues 

for main:
<https://bugs.launchpad.net/~ubuntu-main-sponsors/+subscribedbugs>
and for universe:
<https://bugs.launchpad.net/~ubuntu-universe-sponsors/+subscribedbugs>

and preferrably sponsor bugs fixing FTBFS issues.

Cheers,
   Stefan - on behalf of motu-release.



-- ubuntu-devel-announce mailing list [email]ubuntu-devel-announce@lists.ubuntu.com[/email] [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

---

