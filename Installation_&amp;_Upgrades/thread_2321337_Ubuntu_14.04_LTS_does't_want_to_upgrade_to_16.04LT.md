---
title: "Ubuntu 14.04 LTS does't want to upgrade to 16.04LTS"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by chris-burmajster on 2016-04-22
Hello everybody,

When I set for upgrading by changing the software to "any version" I get "failed repository connection". And then I get "you have 14.04, upgrade to 15.10". Why is it happening?

Thanks,

Chris

---

### Post by Impavidus on 2016-04-22
From 14.04 to any would be from 14.04 to 14.10, which is no longer supported. I'm not sure why it proposes upgrading to 15.10, although I've read more posts stating this happened. I'm not sure upgrading from 14.04 to 15.10 is safe. To upgrade from 14.04 to 16.04 you have to set the update manager to inform of upgrades to LTS releases only. It will propose to upgrade in a few months time, when 16.04.1 is released and most of the remaining bugs have been removed.

---

### Post by chris-burmajster on 2016-04-22
Ah, so I set it to "long term ...."etc? The official blurb seems to say it'll go now.

---

### Post by slickymaster on 2016-04-22
*Thread moved to ***Installation & Upgrades ***sub-forum*

---

### Post by Frogs Hair on 2016-04-22
Direct upgrades from 14.04 LTS to 16.04 LTS are possible and being done. Try the following from the terminal. ```
sudo apt-get update && sudo apt-get upgrade
``` If no upgrade is offered by the update manager try the following .```
sudo do-release-upgrade -d
```

---

### Post by chris-burmajster on 2016-04-22
Thank you! Just what I needed.

---

### Post by chris-burmajster on 2016-04-23
I have a problem. The installation goes fine, and the thing boots. However, the next time I re-boot, the screen goes blank. I have tried everything, from altering the UEFI settings to altering the installation. Can anybody suggest what is causing this?

---

### Post by MikeCyber on 2016-04-23
reinstall the graphics drivers. Anyway 16.04 is buggy better to wait for official announcemtn in package manager

---

### Post by kc1di on 2016-04-23
you should not attempt an upgrade from 14.04 lts to 16.04 lts until the first point release of 16.04 in about three months.  if you need 16.04 before that back up essential files and do a fresh install.  it will save a lot of headaches.

---

### Post by recurringvisitor on 2016-04-23
What type gpu are you using? Is it AMD? if so, then it could be related to that. I had to remove proprietary drivers in upgrading to 15.10 and afterwards most everything went smoothly. Maybe someone here more knowledgeable can get you through it - I'd hate to give advice and then screw up your machine. Anyhow, the big problem with removing the drivers, from what I've heard is heavy use of graphic software and gaming might not work so well. You might be better off doing a clean install after backing up your system.

---

### Post by chris-burmajster on 2016-04-25
Thank you for all your suggestions. I eventually found that my graphics card was faulty by removing it and getting a perfect picture. All I need now is a new graphics card which hopefully will be suppiled under guarantee.

---

