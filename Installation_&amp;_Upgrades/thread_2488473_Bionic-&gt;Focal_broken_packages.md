---
title: "Bionic-&gt;Focal broken packages"
date: 2023-07-05
forum: Installation &amp; Upgrades
---

### Post by mdfishere on 2023-07-05
After a do-release-upgrade the system failed to upgrade. Here's what it says.

Any suggestions?

```
  $ sudo apt install -y --fix-brokenReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libc-bin libc6
Suggested packages:
  glibc-doc
Recommended packages:
  libidn2-0
The following packages will be upgraded:
  libc-bin libc6
2 upgraded, 0 newly installed, 0 to remove and 464 not upgraded.
6 not fully installed or removed.
Need to get 0 B/3,356 kB of archives.
After this operation, 1,470 kB of additional disk space will be used.
debconf: Perl may be unconfigured (Can't load '/usr/lib/x86_64-linux-gnu/perl/5.26/auto/List/Util/Util.so' for module List::Util: /usr/lib/x86_64-linux-gnu/perl/5.26/auto/List/Util/Util.so: invalid ELF header at /usr/share/perl/5.26/XSLoader.pm line 96.
 at /usr/lib/x86_64-linux-gnu/perl/5.26/List/Util.pm line 23.
Compilation failed in require at /usr/lib/x86_64-linux-gnu/perl/5.26/Scalar/Util.pm line 23.
Compilation failed in require at /usr/lib/x86_64-linux-gnu/perl/5.26/Hash/Util.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/x86_64-linux-gnu/perl/5.26/Hash/Util.pm line 9.
Compilation failed in require at /usr/share/perl/5.26/fields.pm line 124.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 106839 files and directories currently installed.)
Preparing to unpack .../libc6_2.31-0ubuntu9.9_amd64.deb ...
Can't load '/usr/lib/x86_64-linux-gnu/perl/5.26/auto/List/Util/Util.so' for module List::Util: /usr/lib/x86_64-linux-gnu/perl/5.26/auto/List/Util/Util.so: invalid ELF header at /usr/share/perl/5.26/XSLoader.pm line 96.
 at /usr/lib/x86_64-linux-gnu/perl/5.26/List/Util.pm line 23.
Compilation failed in require at /usr/lib/x86_64-linux-gnu/perl/5.26/Scalar/Util.pm line 23.
Compilation failed in require at /usr/lib/x86_64-linux-gnu/perl/5.26/Hash/Util.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/x86_64-linux-gnu/perl/5.26/Hash/Util.pm line 9.
Compilation failed in require at /usr/share/perl/5.26/fields.pm line 124.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing archive /var/cache/apt/archives/libc6_2.31-0ubuntu9.9_amd64.deb (--unpack):
 new libc6:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.31-0ubuntu9.9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2023-07-05
The references to 'perl 5.26' and '464 not upgraded' suggest that your attempt to release-upgrade was only partially successful.

Back up your data and reinstall.

---

