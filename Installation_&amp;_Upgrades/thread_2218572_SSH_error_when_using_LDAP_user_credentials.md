---
title: "SSH error when using LDAP user credentials"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by bksyssathish on 2014-04-21
I am not able to make SSH with LDAP user credentials from LDAP client. I am getting below error in LDAP server.

/var/log/auth.log:

```
Apr 21 17:13:10 dennis sshd[3613]: Invalid user myusername from 192.168.12.34
Apr 21 17:13:10 dennis sshd[3613]: input_userauth_request: invalid user myusername [preauth]
Apr 21 17:13:23 dennis sshd[3613]: pam_unix(sshd:auth): check pass; user unknown
Apr 21 17:13:23 dennis sshd[3613]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.12.34 
Apr 21 17:13:25 dennis sshd[3613]: Failed password for invalid user myusername from 192.168.12.34 port 60097 ssh2
Apr 21 17:13:29  sshd[3613]: last message repeated 2 times
Apr 21 17:13:29 dennis sshd[3613]: Connection closed by 192.168.12.34 [preauth]
```

But, I am able to login with LDAP user credentials from LDAP client in **Atl+Ctrl+F1**. 

Is any configuration missing?

---

### Post by Lars Noodén on 2014-04-21
I would look around in /etc/pam.d/common-auth, /etc/pam.d/login and /etc/pam.d/sshd  It is the last one that is relevant, but the others might give a clue about what is missing.

---

### Post by bksyssathish on 2014-04-21
Here is some configuration files.

/etc/pam.d/common-auth:
```
auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_ldap.so use_first_pass
auth    requisite            pam_deny.so
auth    required            pam_permit.so
```

/etc/pam.d/login:
```
auth       optional   pam_faildelay.so  delay=3000000
auth [success=ok new_authtok_reqd=ok ignore=ignore user_unknown=bad default=die] pam_securetty.so
auth       requisite  pam_nologin.so
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session       required   pam_env.so readenv=1
session       required   pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth       optional   pam_group.so
session    required   pam_limits.so
session    optional   pam_lastlog.so
session    optional   pam_motd.so
session    optional   pam_mail.so standard
@include common-account
@include common-session
@include common-password
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
```

/etc/pam.d/sshd:
```
auth  sufficient  pam_ldap.so  no_warn
@include common-auth
account    required     pam_nologin.so
@include common-account
@include common-session
session    optional     pam_motd.so # [1]
session    optional     pam_mail.so standard noenv # [1]
session    required     pam_limits.so
session    required     pam_env.so # [1]
session    required     pam_env.so user_readenv=1 envfile=/etc/default/locale
@include common-password
```

/etc/pam.d/common-password:
```
password    [success=2 default=ignore]    pam_unix.so obscure sha512
password    [success=1 user_unknown=ignore default=die]    pam_ldap.so use_authtok try_first_pass
password    requisite            pam_deny.so
password    required            pam_permit.so
```

I think somewhere I am missing some configuration. But, I don't know what it is. Can you help me.

---

