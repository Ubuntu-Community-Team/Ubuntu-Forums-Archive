---
title: "gdm/kdm: Face browser shows only local users"
date: 2005-02-07
forum: Installation &amp; Upgrades
---

### Post by Martin Stigge on 2005-02-07
Hi,

I'm installing some Ubuntu machines with user authentication against an OpenLDAP Server (SuSE Linux Standard Server 8 ). I installed libpam-ldap and libnss-ldap and set up /etc/pam.d/common-* and /etc/nsswitch.conf, and 'getent passwd' shows both local and ldap users. But I don't see them in the face browsers of kdm or gdm. By doing some network sniffing, i discovered LDAP-packages going server->client, where all relevant LDAP entries are transmitted, so kdm and gdm seem to ignore them...? This seems to be Ubuntu-specific, because it works with a Suse Linux Desktop installation. Where's the magic switch?

Thanks.
Martin

---

### Post by Martin Stigge on 2005-02-07
Hrm, just noticed that uids start at 500 on Suse servers, while 1000 on Debian systems, so it was as easy as pulling the hide-uids-lower-than-limit from 1000 to 500 in gdm and kdm to solve this problem.

---

