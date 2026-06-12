---
title: "[server] installing newer php5-fcgi on jaunty"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by Beoras on 2010-03-25
Hi everyone,

due to changes in my requirements I need a newer version than PHP 5.2.6, since I don't want to change the complete system to the current beta I'm looking into ways to get PHP at least to version 5.3.0
One option is to compile everything from scratch, this is kind of my last resort, since I want to be up to date on security fixes without having to recompile every two or three days.
Another option I came up with was this:

append the sources for lucid in /etc/apt/sources.list 
create file /etc/apt/preferences with content "jaunty"

apt-get install -t lucid php5-fcgi

If I read the man pages correctly this would set the default target distribution to jaunty (so apt-get update/upgrade would still work for the rest of the system), and with the specific request for lucid in the install command it should install PHP5-fcgi with version 5.3.1
Can this work or will it break the system?
I don't have the possibility to try it anywhere so I'm kind of fumbling in the dark, and I'd really like not to have to reinstall or do other extensive repair works after screwing up my live-system :D

Thanks for reading,
Regards,
Beoras

---

