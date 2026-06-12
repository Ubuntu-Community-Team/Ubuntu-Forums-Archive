---
title: "Problems with the latest upgrade to Postfix 2.2.10-1 2.4.5-3"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by rlapitz on 2007-10-27
I had a problem with the latest update of Postfix for Ubuntu Dapper Drake 6.06.1: 

Postfix (2.2.10-1ubuntu0.1) to 2.4.5-3build1 ~ dapper1 
Postfix-doc (2.2.10-1ubuntu0.1) to 2.4.5-3build1 ~ dapper1 
Postfix-mysql (2.2.10-1ubuntu0.1) to 2.4.5-3build1 ~ dapper1 

I use Postfix + MySQL (5.0.22-0ubuntu6.06.5) + courier-imap (3.0.8-13ubuntu5.1).

As of this update users of the intranet can receive mail but NOT send it can. For now can use the Webmail to do (SQUIRRELMAIL). 

The error message is this: 

Oct 22 21:53:17 localhost postfix/smtpd[6738]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Oct 22 21:53:17 localhost postfix/smtpd[6738]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory 
Oct 22 21:53:17 localhost postfix/smtpd[6738]: warning: SASL authentication failure: no secret in database
Oct 22 21:53:17 localhost postfix/smtpd[6738]: warning: wr.dominio.com[192.168.0.99 ]: SASL CRAM-MD5 authentication failed: authentication failure


I read in google that Debian this can be resolved by creating a hard link to / var/spool/postfix/etc/sasldb2 File / etc/sasldb2. But this file (/ etc/sasldb2) I do not have it installed. 

Any idea ? . 

This is my setup Postfix:

===== postconf -n =============================
# postconf -n
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0 
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d 
message_size_limit = 51200000
minimal_backoff_time = 1000s
mydestination =
myhostname = dominio.com
mynetworks = 127.0.0.0/8
mynetworks_style = host 
myorigin = /etc/mailname
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache 
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org,         reject_rbl_client combined.njabl.org ,   reject_rbl_client blackholes.easynet.nl,    reject_rbl_client dnsbl.ahbl.org,        reject_rbl_client dnsbl.njabl.org
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12 
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname,   reject_invalid_hostname, permit 
smtpd_recipient_limit = 30
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks,                 permit_sasl_authenticated, reject_non_fqdn_recipient,                 reject_unauth_destination, check_policy_service inet: 127.0.0.1:60000,                 permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,                 reject_non_fqdn_sender, reject_unknown_sender_domain,                 reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3 
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_domains = 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_destination_concurrency_limit = 1
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
------------------------------------------------------------------------------------------------- 

====       /etc/postfix/sasl/smtpd.conf     ==================
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql 
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: secret
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1
----------------------------------------------------------------------------------------------------------

======  output command ldd /usr/lib/postfix/smtpd ================
# ldd /usr/lib/postfix/smtpd
 
        linux-gate.so.1 =>  (0xffffe000)
        libpostfix-master.so.1 => /usr/lib/libpostfix-master.so.1 (0xb7f98000)
        libpostfix-tls.so.1 => /usr/lib/libpostfix-tls.so.1 (0xb7f8c000)
        libpostfix-dns.so.1 => /usr/lib/libpostfix-dns.so.1 (0xb7f87000)
        libpostfix-global.so.1 => /usr/lib/libpostfix-global.so.1 (0xb7f5d000)
        libpostfix-util.so.1 => /usr/lib/libpostfix-util.so.1 (0xb7f34000) 
        libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7ef7000) 
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7dc8000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7db4000) 
        libdb-4.3.so => /usr/lib/libdb- 4.3.so (0xb7cd7000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7cc2000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7caf000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b80000) 
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b7d000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7b68000) 
        /lib/ld-linux.so.2 (0xb7fb1000)
----------------------------------------------------------------------------------------------------------
 

Thank's in advance.
Raul H. Lapitzondo
[email]raul.lapitzondo@gmail.com[/email]

---

### Post by rlapitz on 2007-10-27
:lolflag:> **rlapitz said:**
> I had a problem with the latest update of Postfix for Ubuntu Dapper Drake 6.06.1: 

Postfix (2.2.10-1ubuntu0.1) to 2.4.5-3build1 ~ dapper1 
Postfix-doc (2.2.10-1ubuntu0.1) to 2.4.5-3build1 ~ dapper1 
Postfix-mysql (2.2.10-1ubuntu0.1) to 2.4.5-3build1 ~ dapper1 

I use Postfix + MySQL (5.0.22-0ubuntu6.06.5) + courier-imap (3.0.8-13ubuntu5.1).

As of this update users of the intranet can receive mail but NOT send it can. For now can use the Webmail to do (SQUIRRELMAIL). 

The error message is this: 

Oct 22 21:53:17 localhost postfix/smtpd[6738]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory
Oct 22 21:53:17 localhost postfix/smtpd[6738]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: No such file or directory 
Oct 22 21:53:17 localhost postfix/smtpd[6738]: warning: SASL authentication failure: no secret in database
Oct 22 21:53:17 localhost postfix/smtpd[6738]: warning: wr.dominio.com[192.168.0.99 ]: SASL CRAM-MD5 authentication failed: authentication failure


I read in google that Debian this can be resolved by creating a hard link to / var/spool/postfix/etc/sasldb2 File / etc/sasldb2. But this file (/ etc/sasldb2) I do not have it installed. 

Any idea ? . 

This is my setup Postfix:

===== postconf -n =============================
# postconf -n
alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0 
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d 
message_size_limit = 51200000
minimal_backoff_time = 1000s
mydestination =
myhostname = dominio.com
mynetworks = 127.0.0.0/8
mynetworks_style = host 
myorigin = /etc/mailname
recipient_delimiter = +
relayhost =
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache 
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org,         reject_rbl_client combined.njabl.org ,   reject_rbl_client blackholes.easynet.nl,    reject_rbl_client dnsbl.ahbl.org,        reject_rbl_client dnsbl.njabl.org
smtpd_delay_reject = yes
smtpd_hard_error_limit = 12 
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname,   reject_invalid_hostname, permit 
smtpd_recipient_limit = 30
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks,                 permit_sasl_authenticated, reject_non_fqdn_recipient,                 reject_unauth_destination, check_policy_service inet: 127.0.0.1:60000,                 permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous 
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks,                 reject_non_fqdn_sender, reject_unknown_sender_domain,                 reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3 
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_domains = 
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_destination_concurrency_limit = 1
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf 
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
------------------------------------------------------------------------------------------------- 

====       /etc/postfix/sasl/smtpd.conf     ==================
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql 
sql_hostnames: 127.0.0.1
sql_user: mail
sql_passwd: secret
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1
----------------------------------------------------------------------------------------------------------

======  output command ldd /usr/lib/postfix/smtpd ================
# ldd /usr/lib/postfix/smtpd
 
        linux-gate.so.1 =>  (0xffffe000)
        libpostfix-master.so.1 => /usr/lib/libpostfix-master.so.1 (0xb7f98000)
        libpostfix-tls.so.1 => /usr/lib/libpostfix-tls.so.1 (0xb7f8c000)
        libpostfix-dns.so.1 => /usr/lib/libpostfix-dns.so.1 (0xb7f87000)
        libpostfix-global.so.1 => /usr/lib/libpostfix-global.so.1 (0xb7f5d000)
        libpostfix-util.so.1 => /usr/lib/libpostfix-util.so.1 (0xb7f34000) 
        libssl.so.0.9.8 => /usr/lib/i686/cmov/libssl.so.0.9.8 (0xb7ef7000) 
        libcrypto.so.0.9.8 => /usr/lib/i686/cmov/libcrypto.so.0.9.8 (0xb7dc8000)
        libsasl2.so.2 => /usr/lib/libsasl2.so.2 (0xb7db4000) 
        libdb-4.3.so => /usr/lib/libdb- 4.3.so (0xb7cd7000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7cc2000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7caf000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7b80000) 
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b7d000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7b68000) 
        /lib/ld-linux.so.2 (0xb7fb1000)
----------------------------------------------------------------------------------------------------------
 

Thank's in advance.
Raul H. Lapitzondo
[email]raul.lapitzondo@gmail.com[/email]



What finally settled following recommendations gave me and installed sasl2:
apt-get install sasl2-bin libsasl2-modules

 and changed in the file /etc/postfix/main.cf:

Smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2

by 

Smtpd_sasl_path = smtpd

Otherwise not working...  Now it works.

---

### Post by admarginem on 2007-12-18
Hi,

I have the same situation, but your solution does not work. Maybe some other solutions?

---

### Post by renbaoru on 2007-12-19
I'm having the same problem after running
```
 apt-get upgrade 
``` which I believe included postfix so I tried your method of fixing it.  No dice!

I don't understand why if my /etc/postfix/sasl/smtpd.conf file has auxprop and sql as the pwcheck_method I would need to use saslpasswd2 and create a database of users : passwords elsewhere...?

my setup is basically identical.  Any help is appreciated as I am steadily going insane
-ren

---

