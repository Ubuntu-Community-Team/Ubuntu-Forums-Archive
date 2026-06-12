---
title: "dpkg --version vs dpkg -l dpkg"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by dwlocks on 2012-10-18
On an 11.04 (natty) install I've noticed this:
```
~# dpkg --version
Debian `dpkg' package management program version 1.15.8.10ubuntu1 (amd64).
This is free software; see the GNU General Public License version 2 or
later for copying conditions. There is NO warranty.
~# dpkg -l dpkg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  dpkg                          1.16.0~ubuntu7.1              Debian package management system
```Which version is the authoritative one?  I'm trying to programmatically check that dpkg is up to date, but it seems that there's actually more than one binary that reports "1.15.8" from --version.

Help?

---

### Post by drmrgd on 2012-10-18
That's quite strange indeed!  It's not that way on my 10.04 server:

```
$ dpkg --version
Debian `dpkg' package management program version 1.15.5.6ubuntu2 (amd64).
This is free software; see the GNU General Public License version 2 or
later for copying conditions. There is NO warranty.
See dpkg --license for copyright and license details.
```

```
$ dpkg -l dpkg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  dpkg                     1.15.5.6ubuntu4.5        Debian package management system
```

Nor on my 12.04 computer:

```
dpkg --version
Debian `dpkg' package management program version 1.16.1.2 (amd64).
This is free software; see the GNU General Public License version 2 or
later for copying conditions. There is NO warranty.

```

```
dpkg -l dpkg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  dpkg                     1.16.1.2ubuntu7          Debian package management system

```

Can you learn anything more with a status query (i.e. dpkg -s dpkg)?  I think I would tend to trust the package itself for accurate version reporting.  But, I could be wrong.

---

### Post by dwlocks on 2012-10-18
I don't have the problem on my 11.10 or 12.04 vms either.  

I just found this error documented in the Usage section:
[http://wiki.debian.org/Multiarch/HOWTO](http://wiki.debian.org/Multiarch/HOWTO)

dpkg 1.15.8 is the earliest Ubuntu dpkg version that supports multi-arch.  As a side note, your system does not have a multi-arch compliant dpkg.  It looks like there were some bugs in the process when a system is converted from single to multi-arch, so a release upgrade might be tricky.  I never do release upgrades, though.  These are just generic build machines for me.

However that doesn't explain the mismatch between dpkg --version and dpkg -l.  I'd bet it's just not that important of a bug.

My solution is going to use dpkg -l, because then I can safely determine multi-arch capability across ubuntu and debian releases with just the one number.  Otherwise I have to detect if it's debian or ubuntu, match distro release with the dpkg version that supports multi-arch, then compare installed dpkg versions.

Solved my own problem!  Thanks!

BTW here's the output of dpkg -s dpkg:
```
Package: dpkg
Essential: yes
Status: install ok installed
Multi-Arch: foreign
Priority: required
Section: admin
Installed-Size: 6464
Origin: debian
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: debbugs://bugs.debian.org
Architecture: amd64
Version: 1.16.0~ubuntu7.1
Pre-Depends: libbz2-1.0, libc6 (>= 2.11), libselinux1 (>= 1.32), zlib1g (>= 1:1.1.4), coreutils (>= 5.93-1), xz-utils
Suggests: apt
Breaks: apt (<< 0.7.7), aptitude (<< 0.4.7-1), dpkg-dev (<< 1.15.8), libdpkg-perl (<< 1.15.8), pinfo (<< 0.6.9-3.1), tkinfo (<< 2.8-3.1)
Conffiles:
 /etc/dpkg/dpkg.cfg f4413ffb515f8f753624ae3bb365b81b
 /etc/alternatives/README 69c4ba7f08363e998e0f2e244a04f881
 /etc/cron.daily/dpkg b6b8dc21210ea50db7cc4636f521758f
 /etc/logrotate.d/dpkg 782ea5ae536f67ff51dc8c3e2eeb4cf9
Description: Debian package management system
 This package provides the low-level infrastructure for handling the
 installation and removal of Debian software packages.
 .
 For Debian package development tools, install dpkg-dev.
Homepage: http://wiki.debian.org/Teams/Dpkg
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>

```

---

