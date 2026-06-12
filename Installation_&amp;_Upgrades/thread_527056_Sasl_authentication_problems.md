---
title: "Sasl authentication problems"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Peque on 2007-08-16
Hey Ubuntu community. 

I am trying to make a mailserver - with postfix,mysql,courier and virtual domains with authentication for sending mail - but having som ought problems. I have followed several guides - but mostly this one: [http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL](http://postfix.wiki.xs4all.nl/index.php?title=Virtual_Users_and_Domains_with_Courier-IMAP_and_MySQL)

Without SASL authentication it works great - but need the authentication for sending mail . and runs into this problem in my auth.log: 
```

Aug 16 13:44:06 mail postfix/smtpd[4057]: sql plugin Parse the username pbj@insa.dk
Aug 16 13:44:06 mail postfix/smtpd[4057]: sql plugin try and connect to a host
Aug 16 13:44:06 mail postfix/smtpd[4057]: sql plugin trying to open db 'postfix' on host 'localhost'
Aug 16 13:44:06 mail postfix/smtpd[4057]: sql plugin could not connect to host localhost
Aug 16 13:44:06 mail postfix/smtpd[4057]: sql plugin couldn't connect to any host

```

My /etc/postfix/sasl/smtpd.conf looks like this:
```

pwcheck_method: saslauthd auxprop
mech_list: login plain
auxprop_plugin: sql
sql_engine: mysql
sql_hostnames: localhost
sql_user: postfix
sql_database: postfix
sql_password: XXXXXXXX
sql_select: select password from mailbox where username = '%u@%r'

```

My /etc/default/saslauthd
```
root@mail:~# cat /etc/default/saslauthd
# This needs to be uncommented before saslauthd will be run automatically
START=yes

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"
MECHANISMS="pam"
PARAMS="-m /var/spool/postfix/var/run/saslauthd -r"

```

and the most important from main.cf
```
myhostname = insa.dk
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.insa.dk, localhost
relayhost =
mynetworks = 192.168.2.0/24 127.0.0.0/8 195.249.32.221/32
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_maibox = Maildir/

# Support for virtual domains:
virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual:mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /usr/local/virtual
virtual_transport = virtual

# Additional support for quota support
virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps.cf
virtual_mailbox_limit_override = yes
virtual_mailbox_limit_message = Sorry, the maildir has overdrawn your diskspacequota - Please free up some space and try again - if it's keeps comming - plaese kontakt webmaster@insa.dk
virtual_overquota_bounce = yes

# SASL2 authentication
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions =
        permit_mynetworks,
        permit_sasl_authenticated,
        reject_non_fqdn_hostname,
        reject_non_fqdn_sender,
        reject_non_fqdn_recipient,
        reject_unauth_destination,
        reject_unauth_pipelining,
        reject_invalid_hostname,
        reject_rbl_client opm.blitzed.org,
        reject_rbl_client list.dsbl.org,
        reject_rbl_client bl.spamcop.net,
        reject_rbl_client sbl-xb1.spamhaus.org
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_security_options = noanonymous
smtpd_sasl-path = /etc/postfix/sasl:/usr/lib/sasl2

```

root@mail:~# ls -lah /var/spool/postfix/var/run/saslauthd/
total 12K
drwxr-xr-x 2 root sasl 4,0K 2007-08-16 13:09 .
drwxr-xr-x 5 root root 4,0K 2007-08-16 11:29 ..
srwxrwxrwx 1 root root    0 2007-08-16 13:09 mux
-rw------- 1 root root    0 2007-08-16 13:09 mux.accept
-rw------- 1 root root    5 2007-08-16 13:09 saslauthd.pid

root@mail:~# ls -lah /var/spool/postfix/var/run/courier/authdaemon/
total 8,0K
drwxrwxrwx 2 daemon daemon 4,0K 2007-08-16 12:38 .
drwxr-xr-x 3 daemon daemon 4,0K 2007-08-16 10:39 ..
lrwxrwxrwx 1 root   root     34 2007-08-16 12:38 socket -> /var/run/courier/authdaemon/socket

root@mail:~# ls -lah /var/spool/postfix/var/run/mysqld
total 8,0K
drwxrwxrwx 2 mysql root 4,0K 2007-08-16 08:40 .
drwxr-xr-x 5 root  root 4,0K 2007-08-16 11:29 ..
lrwxrwxrwx 1 root  root   27 2007-08-16 08:40 mysqld.sock -> /var/run/mysqld/mysqld.sock

I'm running postfix chroot - but that does not seems to cover my problem about what's going on. 
I have installed the libsasl-modules & libsasl-modules-sql 

So rigth now I do not have any more ideas of what is going on??? Could some one get an idea of what is going on - Caurse I can recieve and read mails but not sending those - but have testet that the DBconnection is working - so I'm on the edge og insanity with this little problem??? 

After getting something to work - I found out that I had spelled wrong i smtpd.conf - my bad - But still getting failure like this now: 
```

Aug 16 14:52:41 mail postfix/smtpd[5033]: sql plugin Parse the username pbj@insa.dk
Aug 16 14:52:41 mail postfix/smtpd[5033]: sql plugin try and connect to a host
Aug 16 14:52:41 mail postfix/smtpd[5033]: sql plugin trying to open db 'postfix' on host '127.0.0.1'
Aug 16 14:52:41 mail postfix/smtpd[5033]: begin transaction
Aug 16 14:52:41 mail postfix/smtpd[5033]: sql plugin create statement from userPassword pbj insa.dk
Aug 16 14:52:41 mail postfix/smtpd[5033]: sql plugin doing query SELECT password FROM mailbox WHERE username = 'pbj@insa.dk';
Aug 16 14:52:41 mail postfix/smtpd[5033]: sql plugin create statement from cmusaslsecretPLAIN pbj insa.dk
Aug 16 14:52:41 mail postfix/smtpd[5033]: sql plugin doing query SELECT password FROM mailbox WHERE username = 'pbj@insa.dk';
Aug 16 14:52:41 mail postfix/smtpd[5033]: commit transaction
Aug 16 14:52:41 mail postfix/smtpd[5033]: sql plugin Parse the username pbj@insa.dk
Aug 16 14:52:42 mail postfix/smtpd[5033]: sql plugin try and connect to a host
Aug 16 14:52:42 mail postfix/smtpd[5033]: sql plugin trying to open db 'postfix' on host '127.0.0.1'

And in the mail.log :
Aug 16 14:51:43 mail postfix/smtpd[5033]: connect from unknown[195.249.32.221]
Aug 16 14:51:45 mail postfix/smtpd[5033]: warning: unknown[195.249.32.221]: SASL LOGIN authentication failed
Aug 16 14:51:45 mail postfix/smtpd[5033]: lost connection after AUTH from unknown[195.249.32.221]

THe mysql log:
070816 14:52:41     218 Connect     postfix@localhost on postfix
                    218 Query       START TRANSACTION
                    218 Query       SELECT password FROM mailbox WHERE username = 'pbj@insa.dk'
                    218 Query       SELECT password FROM mailbox WHERE username = 'pbj@insa.dk'
                    218 Query       COMMIT
                    218 Quit
                    219 Connect     postfix@localhost on postfix
                    219 Quit


```


Thanks in advance! 
P

---

