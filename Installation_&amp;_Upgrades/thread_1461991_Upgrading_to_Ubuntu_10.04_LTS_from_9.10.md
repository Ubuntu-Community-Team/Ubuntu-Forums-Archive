---
title: "Upgrading to Ubuntu 10.04 LTS from 9.10"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by jagan185 on 2010-04-25
Hi I want to upgrade to Ubuntu 10.04 LTS stable version (When it is released). Can I export all my current packages, settings , home directory from Ubuntu 9.10. What about the boot loader. I'm now dual booting with Windows 7. Can I do that after upgrading. What are the issues I may have to face after upgrading, like boot loader, current settings and files (data loss). Please Help me with this and some tips and advises for upgrading with out loosing present data and settings. Looking forward to your valuable tips.

---

### Post by zvacet on 2010-04-25
Before you do anything back up your files.You may be interested in [this.]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by oldfred on 2010-04-25
How much space do you have?

After you have moved home as per zvacet link, you may find your install is less than 10GB. I like keeping my old install just in case. You only need another 10-20GB for the new install of root. You probably should not run applications from the old install if linked to the common home as then may upgrade settings with the new versions that may not work with the old version. But you can still boot as backup or to find some setting you forgot to move.

All your user settings are in /home as well as your files. If you made any special system settings the will be in /etc so you may want to back that up also.

You can copy all the additional installed applications:
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

