---
title: "debmirror on fedora?"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by ACID25 on 2007-06-12
Hi

i have an fedora server as an installserver for some linux distributions like suse, fedora etc...so i want to offer the users ubuntu as well. And for that i want to create a local ubuntu repository with debmirror on the fedora server. I think i should work cause it´s a perl script....but i don´t know how to get it work on the fedora machine :(
```

./debmirror
Can't locate LockFile/Simple.pm in @INC (@INC contains: /usr/lib/perl5/5.8.3/i386-linux-thread-multi /usr/lib/perl5/5.8.3 /usr/lib/perl5/site_perl/5.8.3/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.2/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.1/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.0/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.3 /usr/lib/perl5/site_perl/5.8.2 /usr/lib/perl5/site_perl/5.8.1 /usr/lib/perl5/site_perl/5.8.0 /usr/lib/perl5/site_perl /usr/lib/perl5/vendor_perl/5.8.3/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.2/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.1/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.0/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.3 /usr/lib/perl5/vendor_perl/5.8.2 /usr/lib/perl5/vendor_perl/5.8.1 /usr/lib/perl5/vendor_perl/5.8.0 /usr/lib/perl5/vendor_perl .) at ./debmirror line 366.
BEGIN failed--compilation aborted at ./debmirror line 366.
[root@srv1 debmirror-20070123]# perl debmirror
Can't locate LockFile/Simple.pm in @INC (@INC contains: /usr/lib/perl5/5.8.3/i386-linux-thread-multi /usr/lib/perl5/5.8.3 /usr/lib/perl5/site_perl/5.8.3/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.2/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.1/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.0/i386-linux-thread-multi /usr/lib/perl5/site_perl/5.8.3 /usr/lib/perl5/site_perl/5.8.2 /usr/lib/perl5/site_perl/5.8.1 /usr/lib/perl5/site_perl/5.8.0 /usr/lib/perl5/site_perl /usr/lib/perl5/vendor_perl/5.8.3/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.2/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.1/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.0/i386-linux-thread-multi /usr/lib/perl5/vendor_perl/5.8.3 /usr/lib/perl5/vendor_perl/5.8.2 /usr/lib/perl5/vendor_perl/5.8.1 /usr/lib/perl5/vendor_perl/5.8.0 /usr/lib/perl5/vendor_perl .) at debmirror line 366.
BEGIN failed--compilation aborted at debmirror line 366.

```

maybe anyone can help me to set up a local ubuntu repository on a fedora server? or other ideas?

best regards
ACID25

---

### Post by ACID25 on 2007-06-13
Hi

i solved the problem with installing debmirror.rpm and the needed perl packages...

regards
ACID25

---

