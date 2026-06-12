---
title: "[warn] NameVirtualHost *:443 has no VirtualHosts"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by robinbillings on 2010-05-23
After running the upgrade to from 8.04 LTS to 10.04 LTS, I can no longer access the virtualhosts, only the index.html file in the /var/www folder loads.  I also get this error twice when apache2 starts:

[warn] NameVirtualHost *:443 has no VirtualHosts
[warn] NameVirtualHost *:443 has no VirtualHosts

What is wrong?!  How can this be fixed?

---

### Post by AlexanderDGreat on 2011-07-14
Any solutions to this yet?

This problem has been bugging me as well, as I'm just learning how to SSL. And this came up.

---

### Post by AlexanderDGreat on 2011-07-14
I found the solution to this: Just follow these threads:

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html]("http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html")

And this:

[http://www.howtoforge.com/forums/showthread.php?t=33015]("http://www.howtoforge.com/forums/showthread.php?t=33015")

Mine specifically, I forgot to link the sites-available/default-ssl to sites-enabled/000-default-ssl

Good luck!

---

