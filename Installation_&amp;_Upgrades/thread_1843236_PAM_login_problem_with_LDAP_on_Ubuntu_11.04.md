---
title: "PAM login problem with LDAP on Ubuntu 11.04"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by slacktom on 2011-09-13
Hi there!
I really need some help because I am stuck in configurationg Ubuntu as a LDAP-client in my local network. 
I have set up LDAP properly according to a guide on internet. LDAP is working and I can search the LDAP database for users without problems
The problem occurs when i try to log in as a user in the LDAP-database
When I log in with a LDAP user name (not a local one) the computer seems to have contact with the LDAP server; it recognizes the name and the password and "welcome to Ubuntu 11.04....." shows up. After that there is an error message telling me "user not known to the underlying authentication module" and then it sends me  back to the login prompt.
This must be a PAM-related error becase i can easily browse the LDAP-database with "ldapsearch -x uid=<username>". Something goes wrong ....but i cant figure out what it is
Any help or suggestions on this topic would be very appreciated, because Im really stuck with this...
Best regards  

My PAM common-auth (should be OK), common-password and common-session looks like this: 

[I]## common-auth ##
###############
# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]    pam_unix.so nullok_secure
auth    [success=1 default=ignore]    pam_ldap.so use_first_pass
# here's the fallback if no module succeeds
 auth    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;/
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config[/I]


[I]##common-password ##
####################
# here are the per-package modules (the "Primary" block)
password    [success=2 default=ignore]    pam_unix.so obscure sha512
password    [success=1 user_unknown=ignore default=die]    pam_ldap.so use_authtok try_first_pass
# here's the fallback if no module succeeds
#password    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
#password    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
password    optional    pam_gnome_keyring.so 
# end of pam-auth-update config

password   required     pam_cracklib.so difok=2 minlen=8 dcredit=2 ocredit=2 retry=3

password   sufficient   pam_unix.so nullok md5 shadow use_authtok

password   sufficient   pam_ldap.so use_first_pass

password   required     pam_deny.so[/I]


[I]##common-session##
##################
# here are the per-package modules (the "Primary" block)
  session    [default=1]            pam_permit.so
# here's the fallback if no module succeeds
  session    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
# session    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
session    required                        pam_mkhomedir.so umask=0022 skel=/etc/skel
session    required                    pam_ldap.so 
session    optional            pam_unix.so 
session    optional            pam_ck_connector.so nox11
# end of pam-auth-update config[/I]

---

