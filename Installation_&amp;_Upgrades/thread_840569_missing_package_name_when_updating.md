---
title: "missing package name when updating"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by Ignat on 2008-06-25
I seem unable to upgrade a package. When I issue:

sudo apt-get dist-upgrade -f

I get:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  aspell-en
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/249kB of archives.
After this operation, 561kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 7566:
 missing package name
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/INDENT]
Same problem with all of the apt-get command fixes. Suggestions are very much appreciated!

---

### Post by Ignat on 2008-06-25
I think I fixed it by editing /var/lib/dpkg/available around the reported problematic lines. By the way, I should have said that I'm running Hardy Heron.

---

