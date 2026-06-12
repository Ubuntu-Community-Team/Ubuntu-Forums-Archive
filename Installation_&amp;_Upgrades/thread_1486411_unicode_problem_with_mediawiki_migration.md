---
title: "unicode problem with mediawiki migration"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by realjaja on 2010-05-17
made a clean server from scratch 10.04, and tried to migrate a mediawiki - works except for unicode input/edits.

kind of puzzled... any ideas?

1. copied entire mediawiki folder
2. dumped sql / and loaded in via utf8

error i got was (once i enabled it in localsettings.php)
Fatal error: Allowed memory size of 20971520 bytes exhausted (tried to allocate 30720 bytes) in /var/www/wiki/includes/UserMailer.php on line 123

MediaWiki	1.13.2
PHP	5.3.2-1ubuntu4.1 (apache2handler)
MySQL	5.1.41-3ubuntu12

just updated to latest mediawiki... now i get a different error message...

Fatal error: Allowed memory size of 20971520 bytes exhausted (tried to allocate 79 bytes) in /var/www/wiki/languages/Language.php on line 391

---

