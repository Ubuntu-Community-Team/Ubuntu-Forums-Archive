---
title: "Installation and Upgrades"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by mikemykel on 2010-11-28
I have used 10.4 for several months with no problems.  When I upgraded to 10.10 my Update Manager stopped working.  It comes up (now with 250 updates waiting to be installed) but when I hit the Install button nothing happens.  I have tried these forums before and never get any responses.  Is this all a big hoax?

Can I fix this by reinstalling the upgrade over again?  
Can I fix this by erasing Ubuntu completely and starting over?
How do I erase Ubuntu so that I can try another distro?
Should I spend 120 Dollars to purchase a years support from Canonical?

Mike Mykel

---

### Post by wojox on 2010-11-28
Open a terminal and try:

```
sudo apt-get update; sudo apt-get upgrade; sudo apt-get dist-upgrade
```

---

### Post by sikander3786 on 2010-11-28
> Can I fix this by reinstalling the upgrade over again? 

Yes, try the commands mentioned in above post.

> Can I fix this by erasing Ubuntu completely and starting over?

That would definitely fix the problem. But the problem should be fixed without re-install ;-)

> How do I erase Ubuntu so that I can try another distro?

Delete the Ubuntu partition and install the new distro with its own bootloader.

> Should I spend 120 Dollars to purchase a years support from Canonical?

Your call. If you want immediate support, purchase it. Otherwise the community is great.

Please post the output of above mentioned commands if they contain any errors.

---

