---
title: "dovecot: no SASL authentication mechanisms"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by robbrandt on 2010-08-23
I just went through a painful upgrade from 8.04 to 10 LTS.  I've made a lot of progress but am still having email problems.  Dovecot seems to not be able to run, the log is continually reporting:

Aug 22 23:47:34 amd64 postfix/smtpd[22298]: fatal: no SASL authentication mechanisms

Here's this section of dovecot.conf:

auth default {
  mechanisms = plain login
passdb pam {
  }

userdb passwd {
  }

socket listen {
    #master {
      # Master socket provides access to userdb information. It's typically
      # used to give Dovecot's local delivery agent access to userdb so it
      # can find mailbox locations.
      #path = /var/run/dovecot/auth-master
      #mode = 0600
      # Default user/group is the one who started dovecot-auth (root)
      #user = 
      #group = 
    #}
    client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
      path = /var/spool/postfix/private/auth-client
      mode = 0660
      user = postfix
      group = postfix
    }
  }


  ## dovecot-lda specific settings
  ##
  # socket listen {
  # userdb = 
  # passdb = 
  #   master {
  #     path = /var/run/dovecot/auth-master
  #     mode = 0600
  #     user = mail # User running Dovecot LDA
  #     #group = mail # Or alternatively mode 0660 + LDA user in this group
  #   }
  # }
}

What am I missing?

---

### Post by Rinusch on 2011-02-10
kick..

---

