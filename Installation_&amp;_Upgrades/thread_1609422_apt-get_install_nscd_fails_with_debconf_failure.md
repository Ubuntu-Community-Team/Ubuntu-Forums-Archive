---
title: "apt-get install nscd fails with debconf failure"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by meekamoo on 2010-10-30
So I've just replaced my windows 7 desktop with ubuntu 10.10. Running gentoo on server but felt like trying out the latest ubuntu and there is no going back to windows now...

One issue, trying to get ldap authentication going on my network.

On ubuntu client, apt-get isntall nscd fails:

```
apt-get install libpam-ldap libnss-ldap nscd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnss-ldap is already the newest version.
libpam-ldap is already the newest version.
The following NEW packages will be installed:
  nscd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/207kB of archives.
After this operation, 381kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Config.pm line 22.
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown user 'root' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Ran an apt-get update && apt-get upgrade just to make sure everything was up to date and it was.

Any ideas? Should I just install it via source?

---

