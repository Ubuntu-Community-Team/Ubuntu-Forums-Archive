---
title: "Bad luck installing Apache2/PHP5"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by nucklebone on 2008-01-29
I have tried to install Apache2/PHP5 the normal way, by using Synaptic. But for some reason, PHP is not enabled after install and no amount of editing the apache2.conf or the httpd.conf file gets it working.

So...

I uninstalled everything via Synaptic, and used the Edit > Mark packages by task, feature in Synaptic. Everything installs fine, but when I tried to view a page in my browser I get the "Firefox can't establish a connection to the server at 127.0.0.1." error. So I run the command sudo /etc/init.d/apache2 start
and get this error:
 * Starting web server apache2
 apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory

So, I look in /etc/apache2 and sure enough, no apache2.conf file.

I'm not sure how this is possible. Can someone clue me in? This will be my 5th attempt at installing this and it shouldn't be this hard.

-N

---

### Post by zvacet on 2008-01-30
Maybe [this](http://doc.ubuntu.com/ubuntu/serverguide/C/) will be helpfull to you.

---

