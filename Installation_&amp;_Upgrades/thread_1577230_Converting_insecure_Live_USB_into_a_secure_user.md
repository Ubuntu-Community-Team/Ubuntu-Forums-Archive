---
title: "Converting insecure Live USB into a secure user"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by Maahes on 2010-09-18
So I'm trying to alter the usb install so that I have a user with a password. Being careful I created a new user, added them to the admin group and tried to login, I get two following errors, first one may be nothing but the second one is definitely something:

```
Sep 11 00:32:03 ubuntu chpasswd[2644]: eCryptfs PAM passphrase change module retrieved a NULL passphrase; nothing to do
Sep 11 00:32:03 ubuntu chpasswd[2644]: pam_unix(chpasswd:chauthtok): password changed for mcrisp
Sep 11 00:32:03 ubuntu chpasswd[2644]: gkr-pam: couldn't update the login keyring password: no old password was entered
Sep 11 00:32:03 ubuntu chpasswd[2644]: Error attempting to parse .ecryptfsrc file; rc = [-13]
Sep 11 00:32:04 ubuntu chpasswd[2644]: Passphrase file wrapped
Sep 11 00:32:04 ubuntu chpasswd[2644]: eCryptfs PAM passphrase change module retrieved at least one NULL passphrase; nothing to do
```

```
Sep 11 00:41:21 ubuntu gdm-session-worker[3166]: pam_unix(gdm-autologin:session): session closed for user ubuntu
Sep 11 00:41:21 ubuntu polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session1 (system bus name :1.21, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8) (disconnected from bus)
Sep 11 00:41:33 ubuntu gdm-session-worker[4350]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "mcrisp"
Sep 11 00:41:39 ubuntu gdm-session-worker[4350]: pam_unix(gdm:session): session opened for user mcrisp by (uid=0)
Sep 11 00:41:39 ubuntu gdm-session-worker[4350]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Sep 11 00:41:40 ubuntu gdm-session-worker[4350]: pam_unix(gdm:session): session closed for user mcrisp
Sep 11 00:41:57 ubuntu gdm-session-worker[4431]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "mcrisp"
Sep 11 00:42:01 ubuntu gdm-session-worker[4431]: pam_unix(gdm:session): session opened for user mcrisp by (uid=0)
Sep 11 00:42:01 ubuntu gdm-session-worker[4431]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Sep 11 00:42:02 ubuntu gdm-session-worker[4431]: pam_unix(gdm:session): session closed for user mcrisp
Sep 11 00:42:19 ubuntu gdm-session-worker[4523]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "ubuntu"
Sep 11 00:42:21 ubuntu gdm-session-worker[4523]: pam_unix(gdm:session): session opened for user ubuntu by (uid=0)
Sep 11 00:42:21 ubuntu gdm-session-worker[4523]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
```

Now the thing that gets me about the second error is the pam proceed if requirement. Because in gdm.conf There's this:

```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password

```

it merely says sufficient, not required. Also looking at the group settings under users and groups for the Ubuntu user, it's in the group ubuntu but not in the nopasswordlogin group

any help please?

=)

---

### Post by Maahes on 2010-10-20
Just bumping this because I would still like help with this.

---

