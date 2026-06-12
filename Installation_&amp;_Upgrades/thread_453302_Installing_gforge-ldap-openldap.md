---
title: "Installing gforge-ldap-openldap"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by david8igore on 2007-05-24
I'm having difficulty installing gforge-ldap-openldap on a Base Ubuntu system i'm getting the follwoing from teh install log after using dselect to install. 


[INDENT][INDENT][FONT="Courier New"]Setting up gforge-ldap-openldap (4.5.14-22ubuntu1) ...
/etc/libnss-ldap.conf replacement already wanted, not changing.
/etc/nsswitch.conf replacement already wanted, not changing.
/etc/ldap/slapd.conf replacement already wanted, not changing.
Calculating defaults
Reading defaults from /etc/gforge/gforge.conf
[: 104: ==: unexpected operator
Creating /etc/gforge/gforge.conf
[: 107: ==: unexpected operator
[: 107: ==: unexpected operator
[: 107: ==: unexpected operator
Creating /etc/gforge/httpd.conf
Creating /etc/gforge/httpd.secrets
Creating /etc/gforge/local.inc
Creating other includes
WARNING: Please check referal line in /etc/ldap/slapd.conf
WARNING: Probably incorrect base line in /etc/libnss-ldap.conf
Should be: base dc=nodomain
Stopping OpenLDAP: slapd.
Starting OpenLDAP: slapd.
gforge_base_dn = dc=nodomain
server_base_dn = dc=nodomain
Gforge base DN is under the existing server base DN -- OK
addon =
Gforge base DN is equal to server base DN -- OK
WARNING WARNING WARNING: LDAP Configuration Failed
It seems the LDAP load failed, possibly due to a password mismatch
Please check your passwords (especially /etc/ldap.secret) and try again.
dpkg: error processing gforge-ldap-openldap (--configure):
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 gforge-ldap-openldap

installation script returned error exit status 100.
Press <enter> to continue.
[/FONT][/INDENT][/INDENT]
has anybody had a sucessfull installation of this, i get a similar error if i use debian to install this so its the same error when using debian or ubuntu. 

thanks

dave :)

---

