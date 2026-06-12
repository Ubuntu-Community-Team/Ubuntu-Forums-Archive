---
title: "update to gutsy .... maybe not the better way"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by tortue17 on 2008-01-16
Hi,
and sorry for my English

At work, I install Ubuntu, for the Linux part, since version 5.04.
All pass by the network and is auto.
Kickstart + http + script

Such as new version of Ubuntu, I test my install scripts in this last versions.
And this time, I have most problem than before.

In my script installation, I have 2 lines for automatic install of package, which doesn't ask me any question:
**yes `` | apt-get -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" install ssh libnss-ldap libpam-ldap libpam-mount smbfs**

This for samba and ldap.
I saw there is new package : ldap-auth-config ldap-auth-client
But this is not the problem.
The problem is that this command doesn't work under gutsy.
The packages are download, it prepare it, and after nothing, this is block.

I have the same with this line at the end of another script:
** yes `` | apt-get -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold" dselect-upgrade**

After change option in command line to make installation, even if it's not automatic,I have some problem to connect :
A local login as no problem, but a network login as a problem (authentication LDAP)
problem with X

> Refusing to initialize GTK+
getpwuid_r() : failed due to permission denied
...
I can log on a terminal, but not X.
Of course I remove all the  .Xaut .gconf , and other for the Profile

And for the end, my NFS share don't mount.

These are a lot of mistake for an update.
I didn't have some problem for the update of egdy to feisty, on the contrary it resolve a lot of problem.

---

