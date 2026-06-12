---
title: "Issue upgrading from 10.10 to 11.04"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by niko-nojo on 2011-06-14
Hi guys,
I'm getting this issue trying to upgrade to 11.04 ?

installArchives() failed: warning, in file '/var/lib/dpkg/status' near line 6268 package 'g++-4.4':
 'Depends' field, reference to 'libstdc++6-4.4-dev': error in version: invalid character in version number
dpkg: parse error, in file '/var/lib/dpkg/status' near line 46269 package 'language-pack-de':
 `Replaces' field, invalid package name `language-pack-de%base': character `%' not allowed (only letters, digits and characters `-+._')
warning, in file '/var/lib/dpkg/status' near line 6268 package 'g++-4.4':
 'Depends' field, reference to 'libstdc++6-4.4-dev': error in version: invalid character in version number

I'm newish to Ubuntu but I've been searching on Google for a while now but I'm not getting any where.

My current version is

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Thanks.





I figured it out.
In /var/lib/dpkg/status I changed % to -
language-pack-de%base   language-pack-de-base

---

