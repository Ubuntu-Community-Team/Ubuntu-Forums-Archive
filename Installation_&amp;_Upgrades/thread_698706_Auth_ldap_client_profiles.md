---
title: "Auth ldap client profiles"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by moos3 on 2008-02-16
I'm trying to get the following profile for auth-client-config profile to work and I can't figure out what is wrong with 
```

[open_ldap]
nss_passwd=passwd: compat ldap
nss_group=group: compat ldap
nss_shadow=shadow: compat ldap
pam_auth=auth       required     pam_env.so
 auth       sufficient   pam_unix.so likeauth nullok
 auth       sufficient   pam_ldap.so use_first_pass
 auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
 account    sufficient   pam_ldap.so
 account    required     pam_deny.so
pam_password=password   sufficient   pam_unix.so nullok md5 shadow use_authtok
 password   sufficient   pam_ldap.so use_first_pass
 password   required     pam_deny.so
pam_session=session    required     pam_limits.so
 session    required     pam_mkhomedir.so skel=/etc/skel/
 session    required     pam_unix.so
 session    optional     pam_ldap.so

```
any ideas?

get this error message
root@edgecomb:/home/moos3# auth-client-config -a -p open_ldap
** WARNING: Skipping 'open_ldap' (couldn't process)
Usage: auth-client-config -p PROFILE -a -t TYPE [-dn -f FILE]
       auth-client-config -p PROFILE -a -t TYPE -r [-n -f FILE]
       auth-client-config -p PROFILE -a -t TYPE -s [-f FILE]

auth-client-config: error: option -p: invalid choice: 'open_ldap' (choose from 'ldap_example', 'lac_ldap', 'kerberos_example')

---

