---
title: "compiled new php 5.3 and can't get apache load the new version"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by insistkool on 2009-12-09
Hi all, 
I just install the latest php binary (version PHP 5.3.1) mainly because a missing function imageconvolution() in gd. Everything went smooth until I realized apache is still using the repository version (PHP Version 5.2.6-3ubuntu4.4) while cli is using the updated version. I linked the new binary to /usr/bin/php5

name:/$php -v
PHP 5.3.1 (cli) (built: Dec  9 2009 21:44:18 )
Copyright (c) 1997-2009 The PHP Group
Zend Engine v2.3.0, Copyright (c) 1998-2009 Zend Technologies

My OS version:
name:/ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty


I have restarted & reloaded apache, it still loads the old version. What am I missing and how do I point it to the new version? Please let me know if you need any other info.

---

### Post by insistkool on 2009-12-10
Any hints?

---

