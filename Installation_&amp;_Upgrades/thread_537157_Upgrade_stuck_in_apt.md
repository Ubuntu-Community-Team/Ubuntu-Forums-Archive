---
title: "Upgrade stuck in apt"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by rhpot1991 on 2007-08-28
I recently upgraded to the weekly builds of the mythtv packages form mythbuntu.  Since doing that I constantly have the ubuntu-mythtv-frontend package needing an upgrade even though it is at the most recent version.  The package installed and runs fine, but it will not get out of the apt list of upgrades.

from /var/log/dpkg.log:

2007-08-27 23:25:37 status unpacked ubuntu-mythtv-frontend 0.20.2+fixes14333-0.0ubuntu0mythbuntu1
2007-08-27 23:25:37 status unpacked ubuntu-mythtv-frontend 0.20.2+fixes14333-0.0ubuntu0mythbuntu1
2007-08-27 23:25:37 status unpacked ubuntu-mythtv-frontend 0.20.2+fixes14333-0.0ubuntu0mythbuntu1
2007-08-27 23:25:37 status unpacked ubuntu-mythtv-frontend 0.20.2+fixes14333-0.0ubuntu0mythbuntu1
2007-08-27 23:25:37 status unpacked ubuntu-mythtv-frontend 0.20.2+fixes14333-0.0ubuntu0mythbuntu1
2007-08-27 23:25:37 status unpacked ubuntu-mythtv-frontend 0.20.2+fixes14333-0.0ubuntu0mythbuntu1
2007-08-27 23:25:37 status half-configured ubuntu-mythtv-frontend 0.20.2+fixes14333-0.0ubuntu0mythbuntu1
2007-08-27 23:25:37 status installed ubuntu-mythtv-frontend 0.20.2+fixes14333-0.0ubuntu0mythbuntu1


john@ultramagnus:/var/log$ dpkg -l ubuntu-mythtv-frontend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  ubuntu-mythtv- 0.20.2+fixes14 Metapackage to setup and configure a "Fronte
john@ultramagnus:/var/log$

You can see from this that it installed just fine.  I tried removing and purging the package and reinstalling, didn't help.  Anyone have any ideas?

---

