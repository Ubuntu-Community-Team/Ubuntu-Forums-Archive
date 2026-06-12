---
title: "Postfix+Dovecot on Ubuntu 11.10"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by nonaimer on 2011-12-18
Hello,

I am trying to configure my postfix server for two weeks now... no luck.
I tried over 10 different tutorials and none of them seem to help me. The closest I got to working, was with courier, but it does not support encoded passwords in mysql.

I keep getting different errors, and I think im getting close to a state of giving up.

The latest postfix/dovecot2 configuration gives me this error:
"postfix/master tlsmgr: permission denied"

Please help me out, I really need to set up a mail server so I can move on with my other projects :(

---
I also uncommented "tlsmgr" line in master.cf in /etc/postfix

vmail user uid/gid is 5000, homedir -  /hdd/1/mail

My current main.cf file looks like this:
```

virtual_mailbox_base = /hdd/1/mail
virtual_alias_maps = proxy:mysql:/etc/postfix/sql/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/sql/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/sql/mysql_virtual_mailbox_maps.cf
virtual_transport = virtual
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_sender_restrictions = permit_mynetworks, permit_sasl_authenticated, reject
broken_sasl_auth_clients = yes
queue_directory = /var/spool/postfix

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
dovecot_destination_recipient_limit = 1

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

```

dovecot.conf:

```

disable_plaintext_auth = no
mail_location = maildir:/hdd/1/mail/%d/%n
log_timestamp = "%Y-%m-%d %H:%M:%S "
first_valid_uid = 5000
first_valid_gid = 5000
    userdb  {
driver = mysql
    args = /etc/dovecot/dovecot-mysql.conf
    }
passdb  {

driver = mysql
    args = /etc/dovecot/dovecot-mysql.conf
    }

service auth {
unix_listener /var/spool/postfix/auth {
path = /var/spool/postfix/private/auth
mode = 0666
user = postfix
group = postfix

}
unix_listener auth-master {
mode = 0666
}
}

```

---

### Post by Qutaibah on 2011-12-19
I faced problem in Ubuntu server 11.10 I cant find this package postfix-tls 
I dont know if its the same problem

---

### Post by nonaimer on 2012-01-02
try this:
[http://pastebin.com/P7thuzZ7](http://pastebin.com/P7thuzZ7)

it works on 11.10, mail server work great with it ;)

---

