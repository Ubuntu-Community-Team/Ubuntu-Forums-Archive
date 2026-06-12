---
title: "spamassassin - postfix - permissions problem"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by dregan on 2006-09-08
hi,

I have a working postfix mail server but am having trouble with the spamassassin installation.  After reading / searching / reading spamassassin seems to work but for the folling errors in the mail log;

Sep  7 14:43:33 fruity spamd[4401]: spamd: creating default_prefs: /nonexistent/.spamassassin/user_prefs
Sep  7 14:43:33 fruity spamd[4401]: mkdir /nonexistent: Permission denied at /usr/share/perl5/Mail/SpamAssassin.pm line 1467
Sep  7 14:43:33 fruity spamd[4401]: config: cannot write to /nonexistent/.spamassassin/user_prefs: No such file or directory
Sep  7 14:43:33 fruity spamd[4401]: spamd: failed to create readable default_prefs: /nonexistent/.spamassassin/user_prefs
Sep  7 14:43:33 fruity spamd[4401]: mkdir /nonexistent: Permission denied at /usr/share/perl5/Mail/SpamAssassin.pm line 1467
Sep  7 14:43:33 fruity spamd[4401]: spamd: processing message <000001c6d237$bee6f880$1b85a8c0@uykj> for nobody:65534
Sep  7 14:43:33 fruity spamd[4401]: Can't locate Sys/Hostname/Long.pm in @INC (@INC contains: ../lib /usr/share/perl5 /etc/perl /usr/
local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl) at /u
sr/share/perl5/Mail/SPF/Query.pm line 336, <GEN70> line 70.

It would appear that I am starting it incorrectly - I have a spammassassin in the /etc/init.d/... but I feel that it is somewhere else that needs to be configured correctly?

Thank you for any help!

---

### Post by Martin Atkins on 2006-10-11
You should apt-get install libsys-hostname-long-perl. This seems to have worked for me. It looks like a missing dependency on spamassassin.

---

### Post by PriceChild on 2006-10-11
> **Martin Atkins said:**
> You should apt-get install libsys-hostname-long-perl. This seems to have worked for me. It looks like a missing dependency on spamassassin.If so you may want to file a bug on launchpad.net

---

