---
title: "apt-get upgrade from cron"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by Bender NZ on 2006-10-14
Hi,

I have now become responsible for too many servers to manually update and would like to auto update the servers which have stock standard packages and nothing unusual on them.

Putting apt-get update && apt-get -y dist-upgrade into a cron however causes it to download the package list, and retrieve the packages to be upgraded/installed, but it doesn't install anything after that.

Here is my log output:

> Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-updates Release.gpg [191B]
Get:3 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports Release.gpg [191B]
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-updates Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports Release
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) breezy-backports/multiverse Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [191B]
Oct 15 12:00:02 games6 snmpd[5154]: Connection from 58.28.96.36
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Fetched 4B in 1s (2B/s)
Reading package lists...
Reading package lists...
Building dependency tree...
The following packages will be upgraded:
  gdb gzip libgnutls11 libssl0.9.7 linux-image-2.6.12-10-386 openssh-client
  openssh-server python2.4 python2.4-minimal ssh
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/27.4MB of archives.
After unpacking 12.3kB of additional disk space will be used.

After that apt stops. Running the same command from a shell works fine.

Googling seems to suggest that this is definitely possible - but on all the servers I've tried, it will not work.

These servers do not run X so the auto updater that comes with desktop Ubuntu installs won't be of use here.

The systems are Breezy and Dapper.

---

### Post by taurus on 2006-10-14
I guess the reason it stops because it expects an input, Y/n, from you...  Try it with capital Y and see what happens!!!

---

### Post by Bender NZ on 2006-10-14
I have specified -y though which is supposed to assume yes to all questions. :/

---

### Post by taurus on 2006-10-14
If you run it from a terminal, you would see the choices are Y and n and since Linux is case sensitive, Y is not the same as y.  Try using capital y and see if it works or not!!!

---

### Post by Bender NZ on 2006-10-14
I tried that:

> apt-get -Y dist-upgrade
E: Command line option 'Y' [from -Y] is not known.

The manpage says that it's -y or --yes - these work from a command line for me, but from a cron it just stops.

---

