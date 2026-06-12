---
title: "update manger error message"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by Pasang on 2012-10-21
After Updrading to 12.10 from 12.04 am getting the following error messages while running the update manager,which seems like some problem with file related to Myunity.

could anyone help me to remove this error message.

:Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.



Thanks

---

### Post by Wim Sturkenboom on 2012-10-21
The quantal subdirectory does not exist. Either it was removed or there is something wrong on the server.

[http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/](http://ppa.launchpad.net/myunity/ppa/ubuntu/dists/) only shows entries for maverick, natty, oneiric and precise.

If this is persistent (e.g. try tomorrow again), you can probably remove the ppa, but I'm not the person to advise how.

---

### Post by jerrrys on 2012-10-21
More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=myunity+12.10&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=myunity+12.10&as_qdr=all&sa=Google+Search&lang=en)

---

