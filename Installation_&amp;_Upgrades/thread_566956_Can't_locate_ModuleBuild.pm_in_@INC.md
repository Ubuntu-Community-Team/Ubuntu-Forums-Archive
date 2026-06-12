---
title: "Can't locate Module/Build.pm in @INC"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by I.You on 2007-10-04
Hi

I'm installing "po4a" and met the following error.

~ # perl Build.PL
Can't locate Module/Build.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/armv5tejl-linux /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/armv5tejl-linux /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .). at Build.PL line 3.

So I surveyed it and I think this is because Module::Build is not installed.
Perl is installed. I ran this:

~ # perl -MModule::Build -e 'print "installed!\n"'
Can't locate Module/Build.pm in @INC (@INC contains: /usr/local/lib/perl5/5.8.8/armv5tejl-linux /usr/local/lib/perl5/5.8.8 /usr/local/lib/perl5/site_perl/5.8.8/armv5tejl-linux /usr/local/lib/perl5/site_perl/5.8.8 /usr/local/lib/perl5/site_perl .).

I think something is missing in Perl packages.
Please let me know how to solve it.

P.S.
Distro : Not debian nor ubuntu nor any distro. (so I cannot use the package manager like apt or rpm)
CPU : ARM9

---

