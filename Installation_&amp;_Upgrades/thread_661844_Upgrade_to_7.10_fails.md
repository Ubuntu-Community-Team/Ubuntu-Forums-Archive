---
title: "Upgrade to 7.10 fails"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by DrScum on 2008-01-08
Trying to upgrade to 7.10 using the update tool fails with the error
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found
this happened about 5 times before I quit.
Any suggestions what to do

---

### Post by tech9 on 2008-01-08
if you can, try to install 7.10 clean. I wouldn't recommend the upgrade. I have tried it myself and had all kinds of bootup problems. I installed 7.10 clean and have no problems at all.

---

### Post by DrScum on 2008-01-08
But then I woul have to redo all the tinkering I already did (installing additional software and so on).

---

### Post by tech9 on 2008-01-08
> **DrScum said:**
> But then I woul have to redo all the tinkering I already did (installing additional software and so on).

true, but if you backup, you shouldn't have too...

see this link...

[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)

if you backup this way, it should keep your system in-tact... you can alway run updates when you are under the latest version.

---

### Post by MONODA on 2008-01-08
I would recommend making a seperate /home partition when you install. see:
[www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)
also get the app aptoncd. What it does is it creates a cd with all of your apt cache so that you dont have to redownload any files when you want to install it again.

---

### Post by zvacet on 2008-01-08
```
gksudo gedit /etc/apt/sources.list
```

and put # in front of medibuntu lines.Save and close.

```
sudo apt-get update
```

You can upgrade now.

---

