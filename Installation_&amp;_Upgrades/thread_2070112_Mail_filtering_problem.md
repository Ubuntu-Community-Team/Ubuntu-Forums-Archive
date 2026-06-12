---
title: "Mail filtering problem"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by velda on 2012-10-12
Dear all,
  I am having trouble making sieve filtering work under Sendmail+Dovecot+RoundCube combination.
  Here are the system characteristics :
  Red Hat 6U2
  RoundCube 0.8.1
  Dovecot 2.0.9-2
  Sendmail 8.14.4-8
  I have a tab under RoundCube for filtering, and can make a filter with no problem. Filter script appears under /home/username/sieve/managesieve.sieve
  I have tested the filering script, and it is OK, BUT it simply does not filter!!!
  Here are relevant configurations :
  **************
  /etc/mail/sendmail.mc
  …
  MAILER(smtp)dnl
  MAILER(dovecot)dnl   ------------------[FONT=Wingdings][FONT=Wingdings]à[/FONT][/FONT]this line was added
  MAILER(procmail)dnl
  **************
  /etc/dovecot/dovecot.conf
  # 2.0.9: /etc/dovecot/dovecot.conf
  # OS: Linux 2.6.32-220.17.1.el6.i686 i686 Red Hat Enterprise Linux Server release 6.2 (Santiago)
  listen = *
  log_path = /var/log/dovecot.log
  login_trusted_networks = 10.0.0.0/8
  mail_debug = yes
  mail_location = mbox:~/mail:INBOX=/var/spool/mail/%u
  mbox_write_locks = fcntl
  passdb {
    driver = pam
  }
   
  pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
  protocols = imap lmtp sieve pop3
   
  service auth {
    unix_listener auth-master {
      group = mail
      mode = 0664
      user = mail
    }
    user = root
  }
   
  service managesieve-login {
    inet_listener sieve {
      port = 4190
    }
    process_min_avail = 1
    service_count = 1
    vsz_limit = 64 M
  }
   
  service managesieve {
    process_limit = 10
  }
   
  plugin {
    sieve_dir = ~/sieve
    sieve = ~/.dovecot.sieve
  #  sieve_global_dir = /var/lib/dovecot/sieve/global/
  #  sieve_global_path = /var/lib/dovecot/sieve/default.sieve
    }
   
  service pop3-login {
    inet_listener pop3 {
      port = 0
    }
  }
   
  ssl_cert = </etc/pki/dovecot/certs/dovecot.pem
  ssl_key = </etc/pki/dovecot/private/dovecot.pem
   
  userdb {
    driver = passwd
  }
   
  verbose_proctitle = yes
   
  protocol sieve {
    info_log_path = /var/log/dovecot-sieve.log
    log_path = /var/log/dovecot-sieve-errors.log
    managesieve_implementation_string = dovecot pigeonhole
    managesieve_max_line_length = 65536
    managesieve_notify_capability = mailto
    managesieve_sieve_capability = fileinto reject envelope encoded-character vacation subaddress comparator-i
  ;ascii-numeric relational regex imap4flags copy include variables body enotify environment mailbox date
  }
   
  protocol lda {
    auth_socket_path = /var/run/dovecot/auth-master
    hostname = mail-2012.test
    info_log_path = /var/log/dovecot-lda.log
    lda_mailbox_autocreate = yes
    lda_mailbox_autosubscribe = yes
    log_path = /var/log/dovecot-lda-errors.log
    mail_plugin_dir = /usr/libexec/dovecot/
    mail_plugins = " sieve"
    plugin {
      sieve = ~/.dovecot.sieve
    }
    postmaster_address = postmaster@localhost
  }
   
  protocol lmtp {
    info_log_path = /var/log/dovecot-lmtp.log
    log_path = /var/log/dovecot-lmtp-errors.log
    mail_plugins = " sieve"
  }
  **************
  /usr/share/sendmail-cf/mailer/dovecot.m4
  ######################*****##############
  ####   DOVECOT Mailer specification   ###
  ###################*****#################
  Mdovecot,   P=/usr/libexec/dovecot/deliver, F=DFMPhnu9,
                   S=EnvFromSMTP/HdrFromSMTP, R=EnvToSMTP/HdrFromSMTP,
                   T=DNS/RFC822/X-Unix,
                   A=/usr/libexec/dovecot/deliver -d $u
  **************
  /usr/share/squirrelmail/roundcubemail/config/main.inc.php
  …
  $rcmail_config['plugins'] = array('managesieve');---[FONT=Wingdings][FONT=Wingdings]à[/FONT][/FONT]added “managesieve” in this line
  …
  **************
   
  Please help.

---

