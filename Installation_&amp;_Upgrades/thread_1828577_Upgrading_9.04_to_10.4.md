---
title: "Upgrading 9.04 to 10.4"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by devipriya on 2011-08-19
Hi

Currently iam using  ubuntu 9.04, i want to upgrade to 10.4,how can  i upgrade,plz anyone help me.




Regards,
devipriya.

---

### Post by drpjkurian on 2011-08-19
Hi
You cannot upgrade from 9.04 to 10.04 since 9.04 is not a LTS release(Long term support). Therefore I advise you to take a backup of your folders and do a fresh Installation of Ubuntu 10.04

---

### Post by coffeecat on 2011-08-19
Yes, you can do this, but it requires a bit of work.

9.04 is now long past end of life, and you need to follow this guide:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Specifically this:

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

... to upgrade from Jaunty to Karmic (9.10). But you need to "trick" the system into thinking Karmic is still supported because 9.10 is also end of life, and those community pages have not yet been updated to take account of this. Have a look here:

[http://ubuntuforums.org/showpost.php?p=11129193&postcount=8](http://ubuntuforums.org/showpost.php?p=11129193&postcount=8)

Save that text as /var/lib/update-manager/meta-release then you *should* be able to do the Jaunty -> Karmic upgrade as described in the earlier link. Then you should be able to do Karmic -> Lucid with the update manager. It worked for me a couple of weeks ago.

Backup all your personal files before you start.

---

### Post by raja.genupula on 2011-08-19
aah mistake , admin please delete this for me . sorry for this

---

### Post by raja.genupula on 2011-08-19
> **coffeecat said:**
> Yes, you can do this, but it requires a bit of work.

9.04 is now long past end of life, and you need to follow this guide:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Specifically this:

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

... to upgrade from Jaunty to Karmic (9.10). But you need to "trick" the system into thinking Karmic is still supported because 9.10 is also end of life, and those community pages have not yet been updated to take account of this. Have a look here:

[http://ubuntuforums.org/showpost.php?p=11129193&postcount=8](http://ubuntuforums.org/showpost.php?p=11129193&postcount=8)

Save that text as /var/lib/update-manager/meta-release then you *should* be able to do the Jaunty -> Karmic upgrade as described in the earlier link. Then you should be able to do Karmic -> Lucid with the update manager. It worked for me a couple of weeks ago.

Backup all your personal files before you start.


but google give me this . to suggest this i dont know is this going to work ? 
make a look at this 
[http://www.liberiangeek.net/2010/05/how-to-upgrade-from-ubuntu-9-04-jaunty-to-ubuntu-10-04-lucid-lynx-directly/](http://www.liberiangeek.net/2010/05/how-to-upgrade-from-ubuntu-9-04-jaunty-to-ubuntu-10-04-lucid-lynx-directly/)

---

### Post by coffeecat on 2011-08-19
> **raja.genupula said:**
> but google give me this . to suggest this i dont know is this going to work ? 
make a look at this 
[http://www.liberiangeek.net/2010/05/how-to-upgrade-from-ubuntu-9-04-jaunty-to-ubuntu-10-04-lucid-lynx-directly/](http://www.liberiangeek.net/2010/05/how-to-upgrade-from-ubuntu-9-04-jaunty-to-ubuntu-10-04-lucid-lynx-directly/)

Did you see the two responses on that page?

> This doesn’t work anymore.

and..

> It sure doesn’t!

That link is out of date. The reason it doesn't work and my workaround does is explained in my earlier post.

---

