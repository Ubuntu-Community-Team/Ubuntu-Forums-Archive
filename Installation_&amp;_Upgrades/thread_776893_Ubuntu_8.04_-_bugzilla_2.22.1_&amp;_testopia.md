---
title: "Ubuntu 8.04 - bugzilla 2.22.1 &amp; testopia"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Rsulliv1 on 2008-05-01
Has anyone successfully installed testopia in Ubuntu?

I have bugzilla 2.22.1 (via apt-get) running in my 8.04 Ubuntu, but I can't get testopia working. I couldn't find much documentation on the ubuntu install of testopia either. 

I'm not sure if it has anything to do with how Ubuntu's repo version of bugzilla has a unique install (three directories, bugzilla lives in cgi-bin, etc). 

The error I'm receiving is:

/etc/bugzilla/testopia-1.2.2$ sudo ./tr_install.pl
Can't locate Bugzilla.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./tr_install.pl line 25.
BEGIN failed--compilation aborted at ./tr_install.pl line 25.

---

