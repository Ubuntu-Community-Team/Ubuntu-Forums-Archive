---
title: "CGI version upgrade"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by ross_gailer on 2010-03-30
I am running Ubuntu9.1 server and am trying to install OTRS. The check facility (bin/otrs.checkModules) is indicating that I need to upgrade CGI form the currently running 3.29 to at least 3.33 as listed:

o CGI............................failed!!! Version 3.29 installed but  3.33 or higher is required! 

Running the apt-get upgrade has not moved this version and I have been unable to find any reference to upgrading this.

Can anyone help with this please?

:confused:

---

### Post by ross_gailer on 2010-04-05
Solved.

To upgrade this, as the OTRS is using Perl, run sudo cpan CGI

---

