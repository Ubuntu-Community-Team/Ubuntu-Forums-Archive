---
title: "LDAP Client Not Filtering"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by revzalot on 2010-12-07
I've followed the Host Based Authentication Part from this page: [https://help.ubuntu.com/community/LDAPClientAuthentication#Installation](https://help.ubuntu.com/community/LDAPClientAuthentication#Installation)

I cannot get it to work.  When I delete the 'ldap' from the shadow  line in /etc/nsswitch.com all my ldap users cannot login.  Yes I've uploaded the ldapns.schema, activated hostObject and added the machine name to the host attribute to my test ldap users.  

I get this error from /etc/auth.log: sshd[3979]: pam_ldap: ldap_initialize Bad parameter to an ldap routine

Here's my ldap.conf:
> 
base dc=web,dc=com
uri ldap://10.112.18.2 uri ldap://10.112.18.149
ldap_version 3
rootbinddn cn=admin,dc=web,dc=com
bind_policy soft
pam_check_host_attr yes
pam_filter |(host=webdev120)(host=\*)
pam_password crypt
tls_reqcert never
tls_cacertfile /etc/ssl/certs/cacert.pem
Here's my pam.d/*
> 
auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_ldap.so use_first_pass
auth    requisite            pam_deny.so
auth    required            pam_permit.so

account    [success=2 new_authtok_reqd=done default=ignore]    pam_unix.so 
account    [success=1 default=ignore]    pam_ldap.so 
account    requisite            pam_deny.so
account    required            pam_permit.so

password    [success=2 default=ignore]    pam_unix.so obscure sha512
password    [success=1 user_unknown=ignore default=die]    pam_ldap.so use_authtok try_first_pass
password    requisite            pam_deny.so
password    required            pam_permit.so
/etc/nsswitch.conf
> passwd: files ldap
group: files ldap
shadow: files
#  shadow: files ldap
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup: nis




---

### Post by revzalot on 2010-12-13
Ok I tried so many ldap and pam configurations and looks like filtering is dead in the latest 10.10 maverick ldap and pam package even the nssov overlay is missing.

---

### Post by luvshines on 2010-12-13
Saw you post in other thread and got redirected here :)

So, how are you trying to filter the host from /etc/ldap.conf ? Ie. what configuration are you trying

---

### Post by revzalot on 2010-12-13
I'm using the host based authentication based on this link:  [https://help.ubuntu.com/community/LDAPClientAuthentication#Installation](https://help.ubuntu.com/community/LDAPClientAuthentication#Installation)

I was able to get this to work on 10.04 but didn't work on 10.10

---

