---
title: "[Jaunty] apparmor error when upgrading firefox"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by rrwo on 2010-01-23
When I use a package manager (aptitude or synaptic) to install updates to firefox (3.6), I get the following error:
```
Setting up firefox-branding (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~jaunty) ...
Setting up firefox (3.6.1~hg20100122r33535+nobinonly-0ubuntu1~umd1~jaunty) ...
Installing new version of config file /etc/apparmor.d/usr.bin.firefox ...
apparmor_parser: invalid option -- 'T'
Novell/SUSE AppArmor parser version 2.3
Copyright (C) 1999, 2000, 2003, 2004, 2005, 2006 Novell Inc.

Usage: apparmor_parser [options] [profile]

Options:
--------
-a, --add		Add apparmor definitions [default]
-r, --replace		Replace apparmor definitions
-R, --remove		Remove apparmor definitions
-C, --Complain		Force the profile into complain mode
-B, --binary		Input is precompiled profile
-p, --preprocess	Dump profiles with includes expanded
-N, --names		Dump names of profiles in input.
-S, --stdout		Dump compiled profile to stdout
-b n, --base n		Set base dir and cwd
-I n, --Include n	Add n to the search path
-f n, --subdomainfs n	Set location of apparmor filesystem
-m n, --match-string n  Use only match features n
-n n, --namespace n	Set Namespace for the profile
-q, --quiet		Don't emit warnings
-v, --version		Display version info and exit
-d, --debug 		Debug apparmor definitions
-h, --help		Display this text and exit

```
Any ideas how to fix this?

---

### Post by byStanderone on 2010-01-23
...hi, just wondering if hardy already supports the latest version of firefox?

---

