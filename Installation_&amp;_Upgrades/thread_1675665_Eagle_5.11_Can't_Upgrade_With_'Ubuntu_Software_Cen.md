---
title: "Eagle 5.11: Can't Upgrade With 'Ubuntu Software Center'"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by StingzLD on 2011-01-25
Hey Guys.

Eagle came out with their new version 5.11, but the Ubuntu Software Center still has 5.10. I downloaded the software from the site, yet the only way to access it is by going into the Eagle folder. Is there anyway to upgrade the already installed 5.10 without the Ubuntu Software Center and still have it accessible in the Applications Menu?

Thanks in advance!

[I am running Ubuntu 10.10]

---

### Post by sikander3786 on 2011-01-26
If the updates for Eagle are available under Ubuntu now, you can update your software from System > Administration > Update Manager or Applications > Accessories > Terminal using this command.

```
sudo apt-get update && sudo apt-get upgrade
```

You can also keep using your downloaded 5.11 version and add a shortcut to the Menu by going to System > Preferences > Main Menu.

But most of the times, it takes some time before the updates are verified for stability and then added to the Ubuntu Repositories.

---

### Post by StingzLD on 2011-01-29
Awesome. Thanks for your help!

---

