---
title: "cpp update"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by ounas on 2008-06-04
For some day's now I have had problems in upgrading the cpp package

This is the error I get:

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  cpp
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 34.5kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) hardy-updates/main cpp 4:4.2.3-1ubuntu5 [34.5kB]
Fetched 34.5kB in 3s (9369B/s)
(Reading database ... 268652 files and directories currently installed.)
Preparing to replace cpp 4:4.2.3-1ubuntu3 (using .../cpp_4%3a4.2.3-1ubuntu5_i386.deb) ...
update-alternatives: unknown argument `--quiet'

Usage: update-alternatives --install <link> <name> <path> <priority>
       update-alternatives --remove <name> <path>
       update-alternatives --help
<link> is the link pointing to the provided path (ie. /usr/bin/foo).
<name> is the name in /usr/lib/ipkg/alternatives/alternatives (ie. foo)
<path> is the name referred to (ie. /usr/bin/foo-extra-spiffy)
<priority> is an integer; options with higher numbers are chosen.

dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
update-alternatives: unknown argument `--quiet'

Usage: update-alternatives --install <link> <name> <path> <priority>
       update-alternatives --remove <name> <path>
       update-alternatives --help
<link> is the link pointing to the provided path (ie. /usr/bin/foo).
<name> is the name in /usr/lib/ipkg/alternatives/alternatives (ie. foo)
<path> is the name referred to (ie. /usr/bin/foo-extra-spiffy)
<priority> is an integer; options with higher numbers are chosen.

dpkg: error processing /var/cache/apt/archives/cpp_4%3a4.2.3-1ubuntu5_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-alternatives: unknown argument `--quiet'

Usage: update-alternatives --install <link> <name> <path> <priority>
       update-alternatives --remove <name> <path>
       update-alternatives --help
<link> is the link pointing to the provided path (ie. /usr/bin/foo).
<name> is the name in /usr/lib/ipkg/alternatives/alternatives (ie. foo)
<path> is the name referred to (ie. /usr/bin/foo-extra-spiffy)
<priority> is an integer; options with higher numbers are chosen.

dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/cpp_4%3a4.2.3-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Anyone have any idea to repair this problem, I have tried to
manually install the cpp_4.2.3-1ubuntu5_i386.deb

---

### Post by oly on 2008-10-14
Not figured out why the --quiet parameter is missing or how to fix, but removing it from the filed fixes the problem.

the below commands will remove the --quiet parameter from all postinst files, you could run it against a single file but i found this issue effected a lot of my installs.

use at your own risk, worked fine for me though in intrepid ibex.

sudo su
cd /var/lib/dpkg/info/
find ./ -name "*.postinst" | xargs perl -pi -e 's/update-alternatives --quiet/update-alternatives/g'
find ./ -name "*.prerm" | xargs perl -pi -e 's/update-alternatives --quiet/update-alternatives/g'

---

