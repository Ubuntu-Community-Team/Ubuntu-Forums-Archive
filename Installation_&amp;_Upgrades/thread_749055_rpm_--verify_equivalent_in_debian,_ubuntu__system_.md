---
title: "rpm --verify equivalent in debian, ubuntu ? system integrity check"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by michelh on 2008-04-08
Allo all,
I'm looking for an equivalent of rpm --verify in ubuntu (could be a dpkg / apt / synaptic command ... )
What rpm --verify  does is finding the md5sums of all installed files for a package and complains if something was modified : a great way to find if some files in packages were corrupted by a violent fsck for example.

For those of you who have never used rpm, here's an example
# rpm --verify bash
....L...  d /usr/share/man/man1/sh.1.gz                  # destination of symlink changed
S.5.....  d /usr/share/man/man1/ulimit.1.gz             # size and md5sum of file changed
.....UG.  d /usr/share/man/man1/umask.1.gz          # owner and group changed
.M.....T  d /usr/share/man/man1/unset.1.gz            # mode and modification times changed
missing   d /usr/share/man/man1/wait.1.gz             # file removed

I see there is a /var/lib/dpkg/info/$$$$$.md5sums 
and /var/lib/dpkg/info/$$$$$.list so some of the needed info is there.
Is there a command to do a check ?
I just did a 
pkg=bash; (cd / ; md5sum --check --status /var/lib/dpkg/info/$pkg.md5sums || echo $pkg )
is there somehing more serious in debian / ubuntu ?

---

### Post by kellemes on 2008-04-08
[debsums]("http://www.opensourcemanuals.org/manual/debsums/")
Can't remember ever using it myself so can't give a howto.

---

