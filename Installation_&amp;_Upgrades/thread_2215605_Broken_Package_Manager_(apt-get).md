---
title: "Broken Package Manager (apt-get)"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by pnashdc on 2014-04-07
After an upgrade from 13.10 to 14.04 (beta 2), I seem to have a corrupt package manager. When I try to fix, install, or remove a package, apt-get fails with:[INDENT]
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)[/INDENT]

Not a problem, so far. However, the suggestion fails with:

$ sudo apt-get -f install[INDENT]Reading package lists... Done[/INDENT]
[INDENT]Building dependency tree       [/INDENT]
[INDENT]Reading state information... Done[/INDENT]
[INDENT]Correcting dependencies... Done[/INDENT]
[INDENT]The following extra packages will be installed:[/INDENT]
[INDENT]  libpostproc52[/INDENT]
[INDENT]The following NEW packages will be installed:[/INDENT]
[INDENT]  libpostproc52[/INDENT]
[INDENT]0 upgraded, 1 newly installed, 0 to remove and 52 not upgraded.[/INDENT]
[INDENT]19 not fully installed or removed.[/INDENT]
[INDENT]Need to get 0 B/30.6 kB of archives.[/INDENT]
[INDENT]After this operation, 100 kB of additional disk space will be used.[/INDENT]
[INDENT]Do you want to continue? [Y/n] [/INDENT]
[INDENT]dpkg: error processing archive /var/cache/apt/archives/libpostproc52_6%3a0.git20120821-4_amd64.deb (--unpack):[/INDENT]
[INDENT] libpostproc52:amd64 6:0.git20120821-4 (Multi-Arch: no) is not co-installable with libpostproc52 which has multiple installed instances[/INDENT]
[INDENT]E: Sub-process /usr/bin/dpkg returned an error code (1)[/INDENT]

Is there a recommended way to directly remove libpostproc52 or related files? I have already tried every apt-get command.

______________

SOLVED:"dpkg -P fubar" deleted all of the offending packages

---

### Post by ibjsb4 on 2014-04-07
Looks to be a known bug.

[https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1286836](https://bugs.launchpad.net/ubuntu/+source/libav/+bug/1286836)

---

