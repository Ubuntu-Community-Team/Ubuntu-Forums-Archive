---
title: "samba broke on upgrade 6.06 to 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by oetzl on 2008-04-27
Hi all,

I got a running 6.06 64bit installation with Samba and LDAP configured as PDC. Since I got some minor problems with Samba (not always propely updating roaming profile), I decided to upgrade to 8.04.

Upgrade took some hours but went OK, I decided not to overwrite my LDAP and Samba configuration.

But after restarting the machine no Windows client was able to login to the domain. I figured out that Samba lost the local SID. It wasn't a big deal to fix that. But I still have a lot of problems:

1. when trying to login Windows tells me that it is unable to retrieve the user's profile (access denied error). However it uses the local copy of the profile and logs in then. Access to the Samba shares is possible without problems. However changes on the profile are not stored.

2. The root/administrator user is no longer able to login on a Windows machine.

3. The user groups (Domain Admins, Domain Users, self defined groups) are no longer visible in Windows. However they are still defined on the LDAP server and the group maps are OK. I even tried to create new groups - they are also not visible.

All Windows machines are XP SP2.

Does anybody know why the behaviour of Samba/LDAP is that strange?

Oetzl

---

