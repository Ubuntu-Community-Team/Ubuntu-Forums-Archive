---
title: "Software app in Xubuntu - not installing update"
date: 2016-05-30
forum: Installation &amp; Upgrades
---

### Post by jub2 on 2016-05-30
Just installed Xubuntu 16.04 and ran Software Updater to apply the updates since the LTS release. Then rebooted. Then ran Software. In the Updates tab, it said that I had 1 update. I rechecked Software Updater, which confirmed that the system was up to date. 

So I'm not sure why there is a discrepancy between Software Updater and Software. I went ahead and tried to install the update, but Software has been 'working' (spinning gear animation) for a long time.

I'm a Linux newbie and not sure how to safely proceed.

---

### Post by grahammechanical on 2016-05-30
Ubuntu 16.04 has replaced the Ubuntu Software Centre with Ubuntu Software store which is based on Gnome Software store. I am not sure if Xubuntu has Ubuntu Software store or some other software store. But my guess is what you are seeing is a package that is held back for some reason. If we run these two commands we will see if there are any held back packages.

```
sudo apt update
sudo apt upgrade
```

Regards.

---

### Post by jub2 on 2016-05-30
> **grahammechanical said:**
> Ubuntu 16.04 has replaced the Ubuntu Software Centre with Ubuntu Software store which is based on Gnome Software store. I am not sure if Xubuntu has Ubuntu Software store or some other software store. It's simply called 'Software'. I closed it out and restarted it, and still shows 1 update. It also takes forever to search on apps. And when I tried closing it while the app search was ongoing, it ended up freezing.

> **grahammechanical said:**
> 
But my guess is what you are seeing is a package that is held back for some reason. If we run these two commands we will see if there are any held back packages.

```
sudo apt update
sudo apt upgrade
```

Regards.From apt update: "All packages are up to date."
From apt upgrade: "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

So I guess it's an issue with Xubuntu's 'Software' app. Sounds like I need to install and use a different software store app.

---

