---
title: "Error while trying to install gcc 4.5"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by HighCommander4 on 2011-05-11
Hello,

I'm trying to install gcc 4.5 on Ubuntu 9.10 from the debian testing repository.

This is what I've done: 

1) I went to Synaptic Package Manager, and added a new repository with the APT line "deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) testing main".

2) I tried to install gcc-4.5 using the command "sudo apt-get install gcc-4.5", but I got this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binutils cpp-4.5 gcc-4.5-base gcc-4.6-base libc-bin libc-dev-bin libc6 libc6-dev libc6-i686 libcloog-ppl0 libelfg0 libgcc1 libglib2.0-0 libglib2.0-bin
  libglib2.0-dev libgmp10 libgmpxx4ldbl libgomp1 libmpc2 libmpfr4 libnih-dbus1 libnih1 libpcre3 libppl-c4 libppl9 libpwl5 libstdc++6 locales upstart
Suggested packages:
  binutils-doc gcc-4.5-locales gcc-4.5-multilib libmudflap0-4.5-dev gcc-4.5-doc libgcc1-dbg libgomp1-dbg libmudflap0-dbg libppl-c2 libppl7 binutils-gold
  glibc-doc libglib2.0-doc
Recommended packages:
  manpages-dev
The following packages will be REMOVED:
  mountall sreadahead ubuntu-desktop ureadahead
The following NEW packages will be installed:
  cpp-4.5 gcc-4.5 gcc-4.5-base gcc-4.6-base libcloog-ppl0 libelfg0 libglib2.0-bin libgmp10 libgmpxx4ldbl libmpc2 libmpfr4 libnih-dbus1 libnih1 libppl-c4
  libppl9 libpwl5
The following packages will be upgraded:
  binutils libc-bin libc-dev-bin libc6 libc6-dev libc6-i686 libgcc1 libglib2.0-0 libglib2.0-dev libgomp1 libpcre3 libstdc++6 locales upstart
14 upgraded, 16 newly installed, 4 to remove and 1037 not upgraded.
Need to get 0B/38.8MB of archives.
After this operation, 28.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  locales libc-bin libc6 libnih1 libnih-dbus1 upstart libpcre3 libglib2.0-0 libglib2.0-bin libglib2.0-dev libc6-i686 libc-dev-bin gcc-4.6-base libstdc++6
  binutils libc6-dev libgcc1 gcc-4.5-base libgmp10 libgmpxx4ldbl libppl9 libpwl5 libppl-c4 libcloog-ppl0 libelfg0 libmpfr4 libmpc2 cpp-4.5 libgomp1 gcc-4.5
Install these packages without verification [y/N]? y
Preconfiguring packages ...
(Reading database ... 166359 files and directories currently installed.)
Preparing to replace locales 2.9+git20090617-3 (using .../locales_2.11.2-11_all.deb) ...
Unpacking replacement locales ...
dpkg: error processing /var/cache/apt/archives/locales_2.11.2-11_all.deb (--unpack):
 trying to overwrite '/usr/sbin/update-locale', which is also in package libc-bin 0:2.10.1-0ubuntu19
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.11.2-11_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What am I doing wrong? Is there a better way to install gcc 4.5 on Ubuntu? I really need it, but it doesn't come packaged with Ubuntu until 10.10, and I don't want to upgrade to that now...

---

