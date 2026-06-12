---
title: "where does sasl looks for its configs? smtpd.conf specially"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2006-11-29
I try to make smtp-auth working with postfix and saslauthd.

I put a smtpd.conf in /etc/postfix/sasl where I state saslauthd as pw_check_method.

----------
#cat /etc/postfix/sasl/smtpd.conf

saslauthd_path: /var/run/saslauthd/mux
pw_check_method: saslauthd
mech_list: plain login
-----------

saslauthd is running and seems to be fine. I can authenticate my users positively:

# testsaslauthd -u hans2 -p hans2 -s smtpd
0: OK "Success."

but although I stated sasl in my postfix/main.cf postfix/smtpd seems to ask sasl for the authentication instead of saslauthd. So authenticaten fails, cause the users are not in the sasldb2 but only accessible via saslauthd (which uses PAM as mechanism and pam uses ldap then)

so I get the following errors when a clients tries to send an email:

---
Nov 29 22:34:50 ihf2 postfix/smtpd[26864]: warning: unknown[10.21.1.5]: SASL PLAIN authentication failed: authentication failure
Nov 29 22:34:50 ihf2 postfix/smtpd[26864]: warning: unknown[10.21.1.5]: SASL LOGIN authentication failed: authentication failure
Nov 29 22:34:51 ihf2 postfix/smtpd[26864]: warning: SASL authentication failure: Password verification failed
---

It seems that postfix/smtpd does not read smtpd.conf and therefore just queries SASL instead of saslauthd.  I also tried putting smtpd.conf in /usr/lib/sasl2, but nothing changed (I restarted saslauthd and postfix)


Postfix seems to be configured correctly:

----
# postconf | grep sasl | grep smtp

smtp_sasl_auth_enable = no
smtp_sasl_mechanism_filter = 
smtp_sasl_password_maps = 
smtp_sasl_path = 
smtp_sasl_security_options = noplaintext, noanonymous
smtp_sasl_tls_security_options = $smtp_sasl_security_options
smtp_sasl_tls_verified_security_options = $smtp_sasl_tls_security_options
smtp_sasl_type = cyrus
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, check_recipient_maps, reject_unauth_destination, permit_auth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = no
smtpd_sasl_exceptions_networks = 
smtpd_sasl_local_domain = 
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = $smtpd_sasl_security_options
smtpd_sasl_type = cyrus
------



-------
# cat /etc/postfix/master.cf | grep smtp | grep -v ^#

smtp      unix  -       -       -      -       -       smtp
smtp      inet  n       -       n       -       -       smtpd
relay     unix  -       -       -       -       -       smtp
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
--------


any help appretiated,
thnx
peter

---

### Post by gruadp on 2006-11-30
> **gruadp said:**
> I try to make smtp-auth working with postfix and saslauthd.

pw_check_method: saslauthd




SOLVED : the correct directive is pwcheck_method and not pw_check_method

But I also found out about correct locations of the sasl-conf-files: For Details look at [http://www.goldfisch.at/knowledge/362](http://www.goldfisch.at/knowledge/362)

the short answer is (C) by mouss:

----------------------
Don't blindly put files in random places and hope it will work. You need to find the directory used by your sasl library. This path is compiled in the sasl lib. try:

# strings /path/to/libsasl2.so | grep /sasl2

some common places:

/usr/pkg/lib/sasl2/ /usr/local/lib/sasl2/ /usr/lib/sasl2/ /etc/sasl2/
-----------------------

---

