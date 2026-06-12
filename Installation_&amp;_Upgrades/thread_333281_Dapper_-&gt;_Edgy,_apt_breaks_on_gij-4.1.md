---
title: "Dapper -&gt; Edgy, apt breaks on gij-4.1"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by Enfenion on 2007-01-07
I have two computers running ubuntu... I updated one of them to edgy when it was new, and wanted to update the other one now. I used the ```
sudo update-manager -c
```but now the installation exited on a package called gij-4.1.

I've tried to run sudo apt-get install -f, and some other commands, but I only get the same error.
I've also tried to install the package with dpkg...
```
enfenion@enfopc:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gij-4.1 libasound2 libgcj7-0 xutils-dev
Suggested packages:
  gcj-4.1 java-gcj-compat libasound2-plugins libgcj7-dbg
The following packages will be REMOVED:
  libgcj7
The following NEW packages will be installed:
  libgcj7-0 xutils-dev
The following packages will be upgraded:
  gij-4.1 libasound2
2 upgraded, 2 newly installed, 1 to remove and 876 not upgraded.
5 not fully installed or removed.
Need to get 0B/9599kB of archives.
After unpacking 11.5MB of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 87183 files and directories currently installed.)
Preparing to replace gij-4.1 4.1.0-1ubuntu8 (using .../gij-4.1_4.1.1-14ubuntu7_i 386.deb) ...
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

dpkg: error processing /var/cache/apt/archives/gij-4.1_4.1.1-14ubuntu7_i386.deb (--unpack):
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
 /var/cache/apt/archives/gij-4.1_4.1.1-14ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

