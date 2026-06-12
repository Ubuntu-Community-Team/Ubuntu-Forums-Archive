---
title: "apache2 problem - should I reinstall?"
date: 2007-08-02
forum: Installation &amp; Upgrades
---

### Post by rick23 on 2007-08-02
(98)Address already in use: make_sock: could not bind to address [::]:443
Please note:  The start of the line above is parenthesis 9 8 parenthesis.

I get this after doing quite a bit of work installing gallery2 galleries.  I did an experiment with a really big slideshow which died, so I removed the gallery this morning.  However, since then apache2 cannot be started without the message.
If I run a netstat -lnp | grep :443 I get the following:
tcp6       0      0 :::443                  :::*                    LISTEN     5594/apache2
Then if I do a ps on the process 5594 I get the following:
5594 ?        S      0:00 /usr/sbin/apache2 -k start -DSSL

Deleting the process allows me to restart apache2, but next time I reboot the system I am back at the other problem.  In looking at the apache2 error.log file it appears that there is an ssl library error.  Is it possible to re-run the ssl certificate process?  Should I do it?  If not that, what would be a good step now?  Thanks.
Rick

---

