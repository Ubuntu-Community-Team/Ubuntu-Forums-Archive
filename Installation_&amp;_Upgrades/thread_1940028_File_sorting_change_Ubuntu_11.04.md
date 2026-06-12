---
title: "File sorting change: Ubuntu 11.04"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by Hans Husman on 2012-03-12
Upgrading to Ubuntu 11.04 and on a new computer I noticed possible change behavior regarding directory listning from Perl:

[INDENT]
opendir(DIR,$_[0]);
my @files = readdir(DIR);
[/INDENT]

Earlier position zero and one of the array would contain . and .. while after the update I noticed . and .. could be found at other positions.

I did not search for the reason nor in Perl (modules for Perl would have changed during the update as well nor Ubuntu instead replaced readdir with handling of it.

If a general change / bug it would seem rather much code a bit all over would start behaving "odd".

---

