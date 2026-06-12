---
title: "Upgraded from 11.10 to 12.04  and had a DNS issue"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by nariub on 2012-05-27
bind9 did not restart after the upgrade from 11.10 to 12.04

syslog says she was whining about the named.run logfile.

went and looked and sure enough something in the upgrade removed my /var/cache/bind/data directory and all its contents

so 

[B]sudo mkdir /var/cache/bind/data
sudo touch /var/cache/bind/data/named.run
sudo chown bind:bind /var/cache/bind/data/named.run
sudo service bind9 restart[/B]

working like a charm now

Will mark it solved after adding this thread

---

### Post by nariub on 2012-09-01
just wanted to say,  I love you man..

upgraded from 10.04 to 12.04 and my bind was not working

file not found in syslog..

had to create the directories and chown em like you said..

and i am all golden again..

---

