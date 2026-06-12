---
title: "Upgrade to 16.04: PEAR not php7 compliant"
date: 2016-08-03
forum: Installation &amp; Upgrades
---

### Post by brilyant on 2016-08-03
Following an otherwise successful 14.04 - 16.04LTS upgrade the installed PEAR claims compatibility with php 4 & 5, but not 7.

This shows up with "PHP Warning:  preg_replace(): The /e modifier is no longer supported, use preg_replace_callback" in the Apache error log.

What can I do to get a php7-compatible PEAR installed?

---

### Post by brilyant on 2016-08-04
I can't find any sign of a PEAR packaged designed to be compatible with php7.

BUT, just editing the IT.php file as suggested by the Apache error log got round this particular hitch.  Gets me out of a hole - I hope there won't be other holes for me to fall into.

---

