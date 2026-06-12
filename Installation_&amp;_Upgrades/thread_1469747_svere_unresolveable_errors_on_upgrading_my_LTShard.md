---
title: "svere unresolveable errors on upgrading my LTS/hardy to LTS/lucid, due to  dpkg/perl"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by floogy on 2010-05-02
I got svere unresolveable errors on upgrading my LTS/hardy to LTS/lucid lynx, due to apt-list-bugs (workaround) and dpkg/perl issue:
```

~$ sudo dpkg -i /var/cache/apt/archives/perl_5.10.1-8ubuntu2_amd64.deb     
(Reading database ... 524393 files and directories currently installed.)
Preparing to replace perl 5.10.1-8ubuntu2 (using .../perl_5.10.1-8ubuntu2_amd64.deb) ...
Unpacking replacement perl ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
Aborted
~$ sudo dpkg -i /var/cache/apt/archives/libio-stringy-perl_2.110-4_all.deb 
(Reading database ... 524391 files and directories currently installed.)
Preparing to replace libio-stringy-perl 2.110-3 (using .../libio-stringy-perl_2.110-4_all.deb) ...
Unpacking replacement libio-stringy-perl ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
Aborted
~$ sudo dpkg -i /var/cache/apt/archives/libarchive1_2.8.0-2_amd64.deb 
(Reading database ... 524391 files and directories currently installed.)
Preparing to replace libarchive1 2.2.4-1ubuntu1 (using .../libarchive1_2.8.0-2_amd64.deb) ...
Unpacking replacement libarchive1 ...
Setting up libarchive1 (2.8.0-2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
~$ sudo dpkg -i /var/cache/apt/archives/libarchive-zip-perl_1.30-2_all.deb 
(Reading database ... 524393 files and directories currently installed.)
Preparing to replace libarchive-zip-perl 1.30-2 (using .../libarchive-zip-perl_1.30-2_all.deb) ...
Unpacking replacement libarchive-zip-perl ...
dpkg: dependency problems prevent configuration of libarchive-zip-perl:
 libarchive-zip-perl depends on perl; however:
  Package perl is not installed.
 libarchive-zip-perl depends on perl (>= 5.10.1) | libcompress-raw-zlib-perl (>= 2.017); however:
  Package perl is not installed.
  Package libcompress-raw-zlib-perl is not configured yet.
dpkg: error processing libarchive-zip-perl (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libarchive-zip-perl
~$ sudo dpkg -i /var/cache/apt/archives/libcompress-raw-zlib-perl_2.023-1_amd64.deb 
(Reading database ... 524393 files and directories currently installed.)
Preparing to replace libcompress-raw-zlib-perl 2.023-1 (using .../libcompress-raw-zlib-perl_2.023-1_amd64.deb) ...
Unpacking replacement libcompress-raw-zlib-perl ...
dpkg: dependency problems prevent configuration of libcompress-raw-zlib-perl:
 libcompress-raw-zlib-perl depends on perl (>= 5.10.0-24ubuntu4); however:
  Package perl is not installed.
dpkg: error processing libcompress-raw-zlib-perl (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcompress-raw-zlib-perl
~$ locale
LANG=de_DE.utf8@euro
LANGUAGE=de_DE.utf8@euro
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=C
~$ sudo debconf-show
/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Text/Iconv/Iconv.so: undefined symbol: Perl_Tstack_sp_ptr

```
[https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/573598](https://bugs.launchpad.net/ubuntu/+source/update-manager-core/+bug/573598)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/573696](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/573696)

This results in:
```
~$ sudo do-release-upgrade -d -m desktop
Checking for a new ubuntu release
No new release found
~$ sudo dpkg --configure -a
[...]
Processing was halted because there were too many errors.
~$ sudo apt-get -f install
[...]
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
~$ sudo apt-get dist-upgrade
[...]
E: Unmet dependencies. Try using -f.
~$ sudo aptitude full-upgrade
[...]
2937 packages upgraded, 970 newly installed, 279 to remove and 0 not upgraded.
Need to get 11.6MB/3583MB of archives. After unpacking 3305MB will be used.
The following packages have unmet dependencies:
[...]
Resolving dependencies...
open: 5312; closed: 4927; defer: 0; conflict: 77                                                                                                                   ONo solution found within the allotted time.  Try harder? [Y/n]
Resolving dependencies...
open: 10651; closed: 9992; defer: 0; conflict: 91                                                                                                                  .No solution found within the allotted time.  Try harder? [Y/n]n
Abandoning all efforts to resolve these dependencies.
Abort.

~$ sudo aptitude unhold cinepaint-data enblend freeglut3-dev libglut3-dev libplot-dev libxaw-headers  libxaw7-dev
Reading package lists... Done
[...]
Resolving dependencies...
E: I wasn't able to locate file for the libio-stringy-perl package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:
[...]
Score is 2412

Accept this solution? [Y/n/q/?] 
The following packages are unused and will be REMOVED:
[...]
47 packages upgraded, 15 newly installed, 24 to remove and 2955 not upgraded.
Need to get 0B/8566kB of archives. After unpacking 27.1MB will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Error!
E: I wasn't able to locate file for the libio-stringy-perl package. This might mean you need to manually fix this package.

```

```
~$ aptitude search "~ahold" | grep "^.h"
~$ 
```

Formerly the packages cinepaint-data enblend freeglut3-dev libglut3-dev libplot-dev libxaw-headers  libxaw7-dev were in the status 'hold', but I changed the status with the aptitude 'unhold' option...

I highly apreciate any help to solve the error
**dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.**

---

