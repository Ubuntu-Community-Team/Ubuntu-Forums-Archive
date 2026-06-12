---
title: "cannot get 18.10 to upgrade to 19.04"
date: 2019-05-05
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2019-05-05
So, I cannot get the software center update tab to show anything other than that my software is up to date.
I have run this command:

sudo gedit /etc/update-manager/release-upgrades

and set the option to normal (was lts).

This worked for me when I upgraded from 18.04 to 18.10, and I performed that upgrade because I read that you could not upgrade to 19.04 straight from 18.04.

Running the same command and setting the option to normal does nothing to change the behavior in the software center, so I cannot perform the upgrade to 19.10.

What am I doing wrong?

Advice much appreciated.

Thanks.

Caruso

---

### Post by #&amp;thj^% on 2019-05-05
I just use:
```

sudo sed -i 's/cosmic/disco/g' /etc/apt/sources.list
```
Update and Upgrade:
```
sudo apt update 
sudo apt full-upgrade
```
If there are PPA's involved, clean them up first. (PPA Purge / disable)
Good Luck

---

