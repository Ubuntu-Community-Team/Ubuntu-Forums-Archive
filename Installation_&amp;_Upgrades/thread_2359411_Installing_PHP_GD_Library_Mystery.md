---
title: "Installing PHP GD Library Mystery"
date: 2017-04-23
forum: Installation &amp; Upgrades
---

### Post by rob134 on 2017-04-23
I have been trying to enable GD for php but had no luck so far. I did manage to install GD - just isn't enabled for some reason. 
[http://imgur.com/a/QPQBW](http://imgur.com/a/QPQBW)

I'm running ubuntu 14.04 and php5 and php5.6 are both enabled. This is because I never did a2dismod php5 after installing php5.6 from a the ondrej repository. My guess it probably uses the gd.ini when doing a2dismod php5 - But when I a2dismod php5 I receive virtual server errors so I rather leave it enabled instead of troubleshooting that... I have a live-site with a thousand visitors a day so I don't want to mess around with it too much.
PHP runs over FCGid
[http://imgur.com/a/K2VhI](http://imgur.com/a/K2VhI)


Any thoughts how to enable GD from here?


Yes, I restarted apache2 service :)


Thank you!


Regards
Rob

---

### Post by SeijiSensei on 2017-04-23
Did you install the php5-gd package?

---

### Post by rob134 on 2017-04-23
> **SeijiSensei said:**
> Did you install the php5-gd package? 
Yep, see this screenshot: 
[http://imgur.com/a/K2VhI](http://imgur.com/a/K2VhI)
and 
[http://imgur.com/a/QPQBW](http://imgur.com/a/QPQBW)
Cheers

---

