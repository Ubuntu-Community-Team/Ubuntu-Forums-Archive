---
title: "Authentication Failed , Need Help"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by Mwanitete on 2010-08-26
Hii Guys when I upgraded my linux ubuntu 9.10 to 10.4 I can't login 

I tried to use vi /etc/pam.d/gdm.conf

remove or comment : @include common -pamkeyring , i put it at the end of the pam:

But still I can't login ...what can I do..?? need Help


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

or where should I put :: @include common-pamkeyring..??

---

