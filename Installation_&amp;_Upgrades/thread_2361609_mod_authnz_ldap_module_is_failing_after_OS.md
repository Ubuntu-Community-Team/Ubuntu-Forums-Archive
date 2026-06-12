---
title: "mod_authnz_ldap module is failing after OS"
date: 2017-05-18
forum: Installation &amp; Upgrades
---

### Post by nikhil.singh.ext on 2017-05-18
HI Team,
 
This would be long mail but I need to be in detail to clear the air and have your support on the same.
 
We have few logfiles Urls which are binded through ldap and used to fetch logs on Ubuntu server(by0nte).
 
One of set of urls are as follows:
[http://price.intranet.cnb/logfiles/](http://price.intranet.cnb/logfiles/)
[http://price-dev.intranet.cnb/logfiles/](http://price-dev.intranet.cnb/logfiles/)
[http://price-qa.intranet.cnb/logfiles/](http://price-qa.intranet.cnb/logfiles/)
 
 
These urls works sometime and sometime not. When it does not works, we get below logs in the apace error logs.
[Thu May 18 13:05:23.397629 2017] [authnz_ldap:debug] [pid 25851:tid 139833942968064] mod_authnz_ldap.c(554): [client 10.140.24.45:49396] AH01694: auth_ldap authenticate: user emohl authentication failed; URI /logfiles/ [User not found][No such object] (not authoritative)
 
The main issue is that sometimes it works and sometimes it does not. 

Do anyone have idea on the same?

I have one server.
10 Tomcat instances
1 apache
below are the config in one of the tomcat vhost conf.

## LOGFILE ACCESS VIA LDAP AUTH
Alias /logfiles "/app/dev-1-3/logs"
<Directory "/app/dev-1-3/logs">

AllowOverride AuthConfig
AuthType Basic
AuthName "DEV-1-3 Logfile Access"
AuthBasicProvider ldap
AuthLDAPURL "ldaps://ldaps.bayer-ag.com:636/o=bayer?uid?sub?(objectClass=person)"
AuthLDAPBindDN "uid=MACHINEUSER,ou=itaccounts,o=bayer"
AuthLDAPBindPassword MYPASSWORD
AuthLDAPBindAuthoritative off
Require ldap-group cn=webapp-logfiles,ou=managedGroups-iam,o=bayer

Options Indexes FollowSymLinks
IndexOptions FancyIndexing NameWidth=* FoldersFirst HTMLTable IgnoreCase VersionSort
IndexOrderDefault Descending Date
Order allow,deny
Allow from all
</Directory>

Do anyone have idea on the same?

Regards
Nikhil Singh

---

