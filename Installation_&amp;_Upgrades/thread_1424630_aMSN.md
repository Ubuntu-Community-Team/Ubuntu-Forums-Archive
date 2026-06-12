---
title: "aMSN"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by Omar_Gangtux on 2010-03-08
i want to update aMSN but i dont know how :(

---

### Post by MelDJ on 2010-03-08
think if you want the newest amsn, add this repo to your software sources repos:
[https://launchpad.net/~amsn-daily/+archive/ppa](https://launchpad.net/~amsn-daily/+archive/ppa)
after adding do
 ```
sudo apt-get update
```
then it should show a newer version of amsn is available

---

### Post by Omar_Gangtux on 2010-03-08
it wont let me add the new repo

---

### Post by MelDJ on 2010-03-08
in terminal type:
```
    sudo add-apt-repository ppa:amsn-daily
```

then go to system-admin-update manager and check for updates and then install them

---

### Post by Omar_Gangtux on 2010-03-08
thanx man :)

---

### Post by Machiavelli on 2010-03-09
> **MelDJ said:**
> think if you want the newest amsn, add this repo to your software sources repos:
[https://launchpad.net/~amsn-daily/+archive/ppa](https://launchpad.net/~amsn-daily/+archive/ppa)
after adding do
 ```
sudo apt-get update
```
then it should show a newer version of amsn is available

Thanks, that did the trick for me.

---

