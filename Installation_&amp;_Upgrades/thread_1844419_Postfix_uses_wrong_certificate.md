---
title: "Postfix uses wrong certificate"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by ragoon on 2011-09-15
Hi there. After transfering a working installation of postfix and dovecot from OpenSUSE, updating paths etc. now it turns out I can't send any emails because it says: The server failed the authenticity check (<my_server>). The certificate does not apply to the given host. And in certificate details it says: CN=ubuntu.lan (???) Where does it come from? main.cf points to a valid pair of certs, certainly not ubuntu ones. When I click on "accept security exception" it still won't go ahead because relay is denied. The mail.log says: new auth connection: pid=3261
Sep 15 08:14:11 <myhost> postfix/smtpd[3264]: warning: <myip>: address not listed for hostname O2WirelessBox.lan [COLOR="Red"]<--nothing about O2 in OpenSUSE[/COLOR]
Sep 15 08:14:11 hostname postfix/smtpd[3264]: connect from unknown[<myip>]
Sep 15 08:14:11 hostname postfix/smtpd[3264]: NOQUEUE: reject: RCPT from unknown[<myip>]: 554 5.7.1 <sth@yahoo.com>: Relay access denied; from=<sthelse@mydomain.com> to=<sth@yahoo.com> proto=ESMTP helo=<[192.168.1.66]>
Sep 15 08:15:52 hostname postfix/smtpd[3264]: lost connection after RCPT from unknown[<myip>]
Sep 15 08:15:52 hostname postfix/smtpd[3264]: disconnect from unknown[<myip>]
main.cf:
queue_directory = /var/spool/postfix
command_directory = /usr/sbin
daemon_directory = /usr/lib/postfix
data_directory = /var/lib/postfix
mail_owner = postfix
unknown_local_recipient_reject_code = 550
debug_peer_level = 2
debugger_command =
         PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin
         ddd $daemon_directory/$process_name $process_id & sleep 5
sendmail_path = /usr/sbin/sendmail
newaliases_path = /usr/bin/newaliases
mailq_path = /usr/bin/mailq
setgid_group = maildrop
html_directory = /usr/share/doc/packages/postfix-doc/html
manpage_directory = /usr/share/man
sample_directory = /usr/share/doc/packages/postfix-doc/samples
readme_directory = /usr/share/doc/packages/postfix-doc/README_FILES
inet_protocols = all
biff = no
mail_spool_directory = /var/mail
canonical_maps = hash:/etc/postfix/canonical
virtual_alias_maps = hash:/etc/postfix/virtual
virtual_alias_domains = hash:/etc/postfix/virtual
relocated_maps = hash:/etc/postfix/relocated
transport_maps = hash:/etc/postfix/transport
sender_canonical_maps = hash:/etc/postfix/sender_canonical
masquerade_exceptions = root
masquerade_classes = envelope_sender, header_sender, header_recipient
myhostname = <myhostname>
delay_warning_time = 1h
message_strip_characters = \0
program_directory = /usr/lib/postfix
inet_interfaces = all
masquerade_domains = 
mydestination = $myhostname, localhost.$mydomain, $mydomain
defer_transports = 
mynetworks_style = subnet
disable_dns_lookups = no
relayhost = 
mailbox_command = /usr/local/libexec/dovecot/deliver
mailbox_transport = 
strict_8bitmime = no
disable_mime_output_conversion = no
smtpd_sender_restrictions = hash:/etc/postfix/access
smtpd_client_restrictions = 
smtpd_helo_required = no
smtpd_helo_restrictions = 
strict_rfc821_envelopes = no
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtp_sasl_auth_enable = no
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
broken_sasl_auth_clients = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = noanonymous
alias_maps = hash:/etc/aliases
mailbox_size_limit = 0
message_size_limit = 10240000
mydomain = <mydomain>
smtpd_tls_cert_file = /etc/ssl/certs/mailchained.pem
smtpd_tls_key_file = /etc/ssl/private/mailpriv.pem
smtpd_tls_security_level = may
smtpd_tls_auth_only = yes
smtp_tls_security_level = may
home_mailbox = Maildir/
myorigin = $mydomain
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual_mailbox_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual_mailbox_maps.cf
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual_alias_maps.cf
dovecot_destination_recipient_limit = 1
virtual_transport = dovecot
dovecot.conf:
protocols = imap imaps pop3 pop3s 
    protocol imap {
    mail_plugins = quota imap_quota autocreate
    listen = *:143
    ssl_listen = *:993
   }
    protocol pop3 {
    mail_plugins = quota
    listen = *:110
    ssl_listen = *:995
   }
 
disable_plaintext_auth = yes
ssl = yes
ssl_cert_file = /etc/ssl/certs/mailchained.pem
ssl_key_file = /etc/ssl/private/mailpriv.pem
verbose_ssl = yes
    mail_location = maildir:~/Maildir
protocol imap {
  mail_plugin_dir = /usr/local/lib/dovecot/imap
}
  
protocol pop3 {
  mail_plugin_dir = /usr/local/lib/dovecot/pop3
}
  
protocol lda {
  postmaster_address = postmaster@<mydomain>
  mail_plugins = quota
  mail_plugin_dir = /usr/local/lib/dovecot/lda
  log_path = 
  info_log_path = 
  auth_socket_path = /usr/local/var/run/dovecot/auth-master
}
auth_verbose = yes
auth_debug_passwords = yes
mail_debug = yes
auth_debug=yes
auth_debug_passwords = yes
auth default {
  mechanisms = plain login
  passdb pam {
    args = dovecot
  }
  passdb sql {
    args = /usr/local/etc/dovecot-sql.conf
  }
  userdb passwd {
  }
  userdb sql {
    args = /usr/local/etc/dovecot-sql.conf
  }
  user = root
  ssl_require_client_cert = no
  socket listen {
    master {
      path = /usr/local/var/run/dovecot/auth-master
      mode = 0600
      user = vmail
    }
    client {
      path = /var/spool/postfix/private/auth
      mode = 0660
      user = postfix
      group = postfix
    }
  }
}
dict {
  expire = mysql:/usr/local/etc/dovecot-dict-expire.conf
}
plugin {
  quota = maildir
  quota_warning = storage=95%% /usr/local/bin/quota-warning.sh 95
  quota_warning = storage=80%% /usr/local/bin/quota-warning.sh 80
  expire = Trash 30 Trash.* 30 Spam 360 
  expire_dict = proxy::expire
  autocreate = Trash
  autocreate2 = Spam
  autosubscribe = Trash
  autosubscribe2 = Spam
  sieve=~/.dovecot.sieve
  sieve_dir=~/sieve
}
---
I can't find where I go wrong. Any suggestions? Thanks in advance.

---

### Post by ragoon on 2011-09-15
Sorry, but I was using wrong main.cf. Didn't notice main.cf was also in /etc/postfix and it was this one that postfix used. So no need to reply. Thanks.

---

