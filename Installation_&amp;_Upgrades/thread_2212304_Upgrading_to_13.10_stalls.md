---
title: "Upgrading to 13.10 stalls"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by k20 on 2014-03-20
It stalls right at "Removing obsolete conffile /etc/logrotate.d/cups ..."

Can someone please tell me how I would proceed from here? 

Oh It's been stiting there for more than 45 minutes now. 

$ du -h /var/log
1.4M    /var/log/dist-upgrade
132K    /var/log/apt
4.0K    /var/log/unattended-upgrades
du: cannot read directory ‘/var/log/speech-dispatcher’: Permission denied
4.0K    /var/log/speech-dispatcher
4.0K    /var/log/samba
428K    /var/log/upstart
4.0K    /var/log/news
4.0K    /var/log/hp/tmp
8.0K    /var/log/hp
28K    /var/log/ConsoleKit
64K    /var/log/cups
48K    /var/log/lightdm
12K    /var/log/fsck
1.3M    /var/log/installer
6.4M    /var/log

$ du -h /var/log/cups
64K    /var/log/cups

Doesn't look like I got a tons of logs here. I have no idea why it's talking so long to delete files. The desktop is still responding to everything else, not like a typical embarrasing frozen Firefox thingy.

See attached screenshot
[ATTACH=CONFIG]251338[/ATTACH]

---

