---
title: "How 3rd party LAMP extensions detect conf.d?"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by miallen on 2008-01-30
Hi,

We have a PHP extension that installs an INI in PHP_CONFIG_FILE_SCAN_DIR. Unfortunately this goes in /etc/php5/cli/conf.d which of course is ignored by Apache.

This leaves us wondering, how do third parties discover where extension INIs should go?

Also, is there a better forum for server oriented questions?

Mike

---

