---
title: "installing YAML for perl 5.12.1"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by madhuti on 2010-09-15
I have installed perl 5.12.1 on ubuntu,
But now i am facing 2 issues:
1. Not able to get the GUI once machine boots
2. not sure how to install YAML package for perl 5.12.1.

I am trying a script which uses the YAML it shows error like

Can't locate YAML.pm in @INC (@INC contains: /usr/local/lib/perl5/site_perl/5.12.1/i686-linux /usr/local/lib/perl5/site_perl/5.12.1 /usr/local/lib/perl5/5.12.1/i686-linux /usr/local/lib/perl5/5.12.1 .)


Please help me on this

---

### Post by davidbu on 2011-02-21
a search for yaml in synaptic turned up libconfig-yaml-perl
i installed that and its dependencies, now its working.

---

