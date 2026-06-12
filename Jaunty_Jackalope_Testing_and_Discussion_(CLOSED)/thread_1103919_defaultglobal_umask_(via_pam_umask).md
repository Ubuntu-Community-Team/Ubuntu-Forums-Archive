---
title: "default/global umask (via pam_umask) ??"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Guenter on 2009-03-23
hi,

I am trying to change the default/global umask on my notebook (ibm t60 @ Ubuntu Jaunty Alpha6).

I used to do these steps on other systems with success (Debian 4, Debian 5, Ubuntu 8.04, Ubuntu 8.10):

-> make sure umask is not set anywhere (/etc/login.defs, /etc/profile, /etc/skel/*, ~/.bash* ~/.profile)

-> set umask via libpam-umask (/etc/pam.d/common-session -> session optional        pam_umask.so umask=002)

Unfortunately this does not seem to work currently, I still get the standard umask of 022.

Am I missing anything? Thank you :)

---

### Post by Guenter on 2009-03-28
nobody? or what would the preferred way be?

---

