---
title: "Manual install of DEB files ?"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by derby007 on 2006-08-14
Problem: how do I install a package A that depends on package B & visa-versa !! ie. both giving errors :confused: NOTE: I don't ave an internet connection on my home Ubuntu set-up, but i have access to another one that is, ie. not mine..   Do I force an install, probably with dpkg -f or can I copy the needed files/folders from the 'Internet PC' to the 'non-Internet PC' ?? My problem is mainly with MPlayer, libgii0 > libgii0-target-x. :?:

---

### Post by llamakc on 2006-08-14
On the connected machine, do:

apt-get -s install mplayer (or name of package you want)

This will simulate the action and should give you a list of stuff you'll need.

It'll look like this:

```

root@dothan:/home/ken# apt-get -s install gxine
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libsmjs1
Suggested packages:
  realplayer gxineplugin
The following NEW packages will be installed
  gxine libsmjs1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst libsmjs1 (1.5rc6a-2 Ubuntu:6.06/dapper)
Inst gxine (0.5.1-0ubuntu15 Ubuntu:6.06/dapper)
Conf libsmjs1 (1.5rc6a-2 Ubuntu:6.06/dapper)
Conf gxine (0.5.1-0ubuntu15 Ubuntu:6.06/dapper)

```

Now, do it with the -d flag to 'download only'.

The packages will end up in /var/cache/apt/archives, so use whatever method you're using to move them over to the other box and install there.

---

### Post by derby007 on 2006-08-14
Cheers, i've done it on the 'internet PC' & i'll transfer those files tonite. Q. As I don't ave the internet on my PC, can I 'comment' out the repositories in my -sourses.list-. Or would this cause problems? Any ideas...

---

