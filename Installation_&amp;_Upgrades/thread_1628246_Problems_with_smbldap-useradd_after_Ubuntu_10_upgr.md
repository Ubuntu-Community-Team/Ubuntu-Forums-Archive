---
title: "Problems with smbldap-useradd after Ubuntu 10 upgrade"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by fongd on 2010-11-22
I recently upgraded our ldap server to Ubuntu 10.04.1 (64-bit). In the past, I've been able to use smbldap-useradd to create new ldap and samba users but am having problems since the upgrade.

For starters, /etc/smbldap-tools was empty, which caused smbldap-useradd to bomb out with configuration-related errors. After following some tips on how to create the config files, I've gotten as far as being able to run smbldap-useradd but am now getting this error:

Error: modifications require authentication at /usr/share/perl5/smbldap_tools.pm line 1187, <DATA> line 466.

I've got the correct credentials set up in /etc/smbldap-tools/smbldap_bind.conf. I can login and make changes just fine through phpldapadmin with the same credentials, but smbldap-useradd just doesn't want to work. Is there something else I'm possibly overlooking?

Help!

---

### Post by dino99 on 2010-11-22
dont have experience myself about that, but:

[https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/samba-ldap.html)

---

### Post by fongd on 2010-11-22
Well, I already have a working ldap setup, AFAIK. Samba is using the LDAP DB to authenticate users and everything looks to be OK in phpldapadmin. Also, this setup used to work flawlessly with Ubuntu 9, so I'm not sure what broke it. The only thing that doesn't seem to be working are the smbldap tools, which seem to NOT be authenticating against my LDAP server to make changes, even though they should be.

---

### Post by dino99 on 2010-11-22
why not sending a bug-report on launchpad ?

---

