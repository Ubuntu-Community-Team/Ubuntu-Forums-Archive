---
title: "How to make xdg-su accept my admin password in Lucid when installing Adobe Air"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by Reepi on 2010-05-20
It seems **xdg-su** is unable to accept my admin/root password whenever I try to install a new AIR application or make an upgrade.

Upon every attempt to add my admin/root password I get an error: "su: Authentication failure". In the end: "Error# 5100"!

I have recently upgraded to Lucid, but the problem has arisen back in Karmic.

Now I am running Adobe Air 2 Beta.

Any tips will be most appreciated. Thank you!

---

### Post by Reepi on 2010-09-13
Problem solved via this post Re TweetDeck: [http://kovshenin.com/archives/tweetdeck-on-fedora-10/](http://kovshenin.com/archives/tweetdeck-on-fedora-10/)

Run as root:

/usr/bin/Adobe\ AIR\ Application\ Installer

and open your downloaded air file.

Thanks, Konstantin!

---

