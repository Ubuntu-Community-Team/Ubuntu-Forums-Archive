---
title: "Spamassassin 3.1.3 and perl 5.8.8"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by brianbarry on 2006-09-19
As I tend to learn "trial by fire", I've upgraded to Edgy using dist-update and have run into a problem using Spamassassin.  Using Spamassassin I'm getting perl errors of the following:

Use of uninitialized value in substitution (s///) at /usr/share/perl5/Mail/SpamAssassin/Conf/Parser.pm line 850.

Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Mail/SpamAssassin/Conf/Parser.pm line 923.

Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Mail/SpamAssassin/Conf/Parser.pm line 924.

config: invalid regexp for rule X_MAILER_SPAM: : missing or invalid delimiters
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Mail/SpamAssassin/Conf/Parser.pm line 850.

config: invalid regexp for rule BAD_ENC_HEADER: : missing or invalid delimiters

as well as a few others.  The errors are resultant from scanning with rulesets from Apache.  From the errors, it would appear perl is using  a different sytax, which doesn't make sense to me.  Using my minuscule logic set, it would seem the problem lies in Spamassassin's use of the perl language (unlikely), or in Ubuntu's implentation.  Could someone assist me finding the root of the problem?

Thanks,
Brian

---

### Post by tagra123 on 2006-09-19
partimage

rsync

There is a package that can create custom install cds but I dont remember the name. Maybe someone will know what the name of theat app is.

---

### Post by brianbarry on 2006-09-20
Sorry, I didn't spell out the fact that I upgraded to Edgy Eft using dist-upgrade.  The errors are being produced since upgrading.  And by the way, anyone reading this and thinking of using dist-upgrade should know it was not a smooth upgrade for me.  However, the bumps encountered were in no way related to this issue.  I'm unable to discern whether my problems are from dist-upgrade not being ready for prime time or the individual packages just aren't completely woven together yet, as I type it occurs to me both are inextricably tried.  The upgrade was performed on a clean install of Ubuntu 6.06.1.

Brian

---

