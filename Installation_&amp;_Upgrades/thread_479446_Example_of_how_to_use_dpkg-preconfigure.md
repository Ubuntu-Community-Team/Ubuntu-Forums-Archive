---
title: "Example of how to use dpkg-preconfigure?"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by EmmEff on 2007-06-20
Where can I get examples of how to use dpkg-preconfigure manually?

For example, I'd like to preconfigure nullmailer.  I've done the procedure as follows:

[LIST=1]
[*]"apt-get install -d nullmailer" - download package without installing
[*]"dpkg-preconfigure -fnoninteractive /var/cache/apt/archives/nullmailer..." - install debconf entries for nullmailer
[*]"debconf-set-selections <valid nullmailer entries>" - preconfigure nullmailer
[*]"debconf-show nullmailer" - indicates the settings were saved
[*]"apt-get install nullmailer" - nullmailer package installed
[*]"debconf-show nullmailer" - shows that all settings have been overwritten with defaults
[/LIST]

Am I using dpkg-preconfigure incorrectly?  I have been unable to find any example docs of how to use it.

Thanks in advance

---

