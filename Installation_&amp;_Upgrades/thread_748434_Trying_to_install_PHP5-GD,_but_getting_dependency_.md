---
title: "Trying to install PHP5-GD, but getting dependency error"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by leenwebb on 2008-04-07
Hi all,
I'm trying to install php5-gd.  When I do:

[INDENT]apt-get install php5-gd
[/INDENT]
I get the following:

The following packages have unmet dependencies:
[INDENT]  php5-gd: Depends: php5-common (= 5.2.3-1ubuntu6) but 5.2.3-1ubuntu6.2 is to be installed[/INDENT]


The php5-common that I have installed is in fact 5.2.3-1ubuntu6.2, so I'm not sure how I'm supposed to convince the gd package to install anyway.

Thoughts?

Thanks!
Eileen

---

### Post by Belak on 2008-04-07
I'd try a 
sudo apt-get update
then a 
sudo apt-get upgrade

Then try it installing GD again

---

