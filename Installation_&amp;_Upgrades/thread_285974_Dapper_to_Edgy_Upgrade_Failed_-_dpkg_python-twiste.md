---
title: "Dapper to Edgy Upgrade Failed - dpkg python-twisted-core"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by jblaty on 2006-10-27
I have followed the online instructions to upgrade to Edgy, and have made several attempts.  Here is what I'm getting:

> E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-twisted-core (2.4.0-2) ...
INFO: using old version '/usr/bin/python2.3'
pycentral: pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/twisted/plugins/__init__.py
pycentral pkginstall: already exists: /usr/lib/python2.4/site-packages/twisted/plugins/__init__.py
dpkg: error processing python-twisted-core (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-twisted-mail:
 python-twisted-mail depends on python-twisted-core (>= 2.4); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-mail (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-news:
 python-twisted-news depends on python-twisted-core (>= 2.4); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-news (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-names:
 python-twisted-names depends on python-twisted-core (>= 2.4); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-names (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-conch:
 python-twisted-conch depends on python-twisted-core (>= 2.4); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-conch (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted:
 python-twisted depends on python-twisted-core (>= 2.4); however:
  Package python-twisted-core is not configured yet.
 python-twisted depends on python-twisted-conch (>= 1:0.7); however:
  Package python-twisted-conch is not configured yet.
 python-twisted depends on python-twisted-mail (>= 0.3); however:
  Package python-twisted-mail is not configured yet.
 python-twisted depends on python-twisted-names (>= 0.3); however:
  Package python-twisted-names is not configured yet.
 python-twisted depends on python-twisted-news (>= 0.2); however:
  Package python-twisted-news is not configured yet.
dpkg: error processing python-twisted (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-web:
 python-twisted-web depends on python-twisted-core (>= 2.4); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-web (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-osd:
 python-osd depends on python-twisted; however:
  Package python-twisted is not configured yet.
dpkg: error processing python-osd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-runner:
 python-twisted-runner depends on python-twisted-core (>= 2.4); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-runner (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-words:
 python-twisted-words depends on python-twisted-core (>= 2.4); however:
  Package python-twisted-core is not configured yet.
dpkg: error processing python-twisted-words (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-twisted-lore:
 python-twisted-lore depends on python-twisted-web (>= 0.2); however:
  Package python-twisted-web is not configured yet.
dpkg: error processing python-twisted-lore (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-twisted-core
 python-twisted-mail
 python-twisted-news
 python-twisted-names
 python-twisted-conch
 python-twisted
 python-twisted-web
 python-osd
 python-twisted-runner
 python-twisted-words
 python-twisted-lore


Any ideas?

Regards,
Joe

---

