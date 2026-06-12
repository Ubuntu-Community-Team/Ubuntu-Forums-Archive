---
title: "Access Denied on Login after joining Ubuntu 16.04 to windows domain using PBIS open"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by adedamoo-ab on 2017-03-07
I just successfully joined a system running Ubuntu 16.04.2 to the windows domain using PBIS open 8.5.3.293.
Every test shows the computer is now on the domain.
However any login attempt always return "Access denied". I have tried  "su domain\\username"
I have also tried logging in directly., below is the error message from the auth,log.
Please note that the user is already a member of the group listed.
I have checked all related thread and all proposed solutions is not working as i am still having the error and i am currently locked out.

```

su[6288]: PAM unableto dlopen(pam_ldap.so): /lib/security/pam_ldap.so: cannot open sharedobject file: No such file or directory
su[6288]: PAM addingfaulty module: pam_ldap.so
su[6288]:[lsass-pam] [module:pam_lsass]User domain\username is denied accessbecause they are not in the 'require membership of' list
su[6288]:[lsass-pam] [module:pam_lsass]pam_sm_authenticate error[login:domain\username][error code:40158]
su[6288]:pam_unix(su:auth): authentication failure; logname= uid=1000 euid=0tty=/dev/pts/1 ruser=root rhost=  user=domain\username
su[6288]:pam_authenticate: Authentication failure
su[6288]: FAILED sufor domain\username by root
su[6288]: -/dev/pts/1 root:domain\username

```

Please help

---

