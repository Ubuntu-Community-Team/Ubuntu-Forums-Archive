---
title: "Ubuntu Server problems after 12 to 14.04 upgrade"
date: 2014-10-07
forum: Installation &amp; Upgrades
---

### Post by zoomiest2 on 2014-10-07
I just upgraded my Ubuntu Server from 12.x to 14.04, and it loaded fine, but the webserver and app didn't completely make it through.

1) I searched and found the new document root location, and edited that - now the website is up again. Whew.
2) Apache and MySQL are apparently running, but when I go to the root location for my LAMP application, my browsers says: No data. ?  All of the solutions I see posted are for Ubuntu Desktop, not server.
3) I checked my PHP-5 module with 
      user@hostname:~$ dpkg -l |grep libapache2-mod-php5            and I get a successful:
            ii  libapache2-mod-php5                 5.5.9+dfsg-1ubuntu4.4               amd64        server-side, HTML-embedded scripting language (Apache 2 module)

Testing my PHP with phpinfo() also brings up the full answer page. I seem to be on [COLOR=#000000][FONT=undefined]PHP Version 5.5.9-1ubuntu4.4[/FONT][/COLOR]
So, I think I am okay, there.

4) I also find that my SugarCRM instance is fine. (Its just my custom LAMP app from opencats.org that won't come up) Could the PHP code be too old? Is there a cut off after which old PHP won't resolve?

Any help would be appreciated, so I can get this LAMP app running again.
/Allan

---

