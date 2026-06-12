---
title: "Upgarde Apache 2.2 to 2.4 Passphrase problems"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by Deronius on 2013-06-11
I just upgraded apache2 2.2 to 2.4 that had a working SSL cert.  Now when I restart apache I get the following:


AH00548: NameVirtualHost has no effect and will be removed in the next release /etc/apache2/mods-enabled/ssl.conf:26
AH00526: Syntax error on line 45 of /etc/apache2/mods-enabled/ssl.conf:
SSLPassPhraseDialog: file '/usr/share/apache2/ask-for-passphrase' does not exist
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!


The SSL cert was setup and working and when I did the upgrade I opted to keep my same configuration.  I assume I need to create this file but when searching the web I didn't come up with anything.  Any help would be appreciated.  I definitely need it.

---

