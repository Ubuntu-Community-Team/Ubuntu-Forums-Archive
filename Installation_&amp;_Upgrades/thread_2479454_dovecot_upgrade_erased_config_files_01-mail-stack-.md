---
title: "dovecot upgrade erased config files 01-mail-stack-delivery.conf"
date: 2022-09-25
forum: Installation &amp; Upgrades
---

### Post by devbeer2 on 2022-09-25
Hey there, just wanted to let people know about an issue i had an how i solved it. 

When upgrading the server to the latest 22.04 LTS ubuntu release, it removed two files from dovecot config directories (\etc\dovecot\conf.d\). one was **01-mail-stack-delivery.conf** and the other one was **99-mail-stack-delivery.conf**

restoring these files from backup made mail work again. was an error like **"auth: Fatal: SCRAM-SHA-1 mechanism can't be supported with given passdbs**" and "postfix/smtpd[1927]: **warning: SASL: Connect to private/dovecot-auth failed: Connection refused**"

Initially, until i compared directories it made no sense. Seems like most of my configuration is in the 01-mail-stack-delivery file with a modified date of 2012, and the ubuntu installer went and deleted these files. Makes me wonder what else it deleted... Ill be making a zip backup file of the old server just incase something else comes up. Luckily this is a home server that doesnt do much,... but yikes.. dont like it deleting files without asking me. I know it wanted me to confirm changes to files and i mostly said no, becuase i had config in those files. Seems like it just decided to whipe these ones though.

And no, i dont know why my configuration is in these files. I did this 10 years ago and its not documented. Installer still should not delete files from config dirs...

contents of the 01-mail-stack file:

```

# Some general options
protocols = imap pop3 sieve
disable_plaintext_auth = yes
ssl = yes
ssl_cert = </etc/ssl/certs/ssl-mail.pem
ssl_key = </etc/ssl/private/ssl-mail.key
ssl_cipher_list = ALL:!LOW:!SSLv2:ALL:!aNULL:!ADH:!eNULL:!EXP:RC4+RSA:+HIGH:+MEDIUM
mail_location = maildir:~/Maildir
auth_username_chars = abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890.-_@

# IMAP configuration
protocol imap {
        mail_max_userip_connections = 10
        imap_client_workarounds = delay-newmail
}

# POP3 configuration
protocol pop3 {
        mail_max_userip_connections = 10
        pop3_client_workarounds = outlook-no-nuls oe-ns-eoh
}

# LDA configuration
protocol lda {
        postmaster_address = postmaster
        mail_plugins = sieve
        quota_full_tempfail = yes
        deliver_log_format = msgid=%m: %$
        rejection_reason = Your message to <%t> was automatically rejected:%n%r
}

# Plugins configuration
plugin {
        sieve=~/.dovecot.sieve
        sieve_dir=~/sieve
}

# Authentication configuration
auth_mechanisms = plain login

service auth {
  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/dovecot-auth {
    mode = 0660
    user = postfix
    group = postfix
  }
}


```

proof that files were erased (left is backup, right is production, black means file doesnt exist, etc (from kdiff3 program on windows)):

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291069&stc=1[/IMG]

hope it helps someone.

---

