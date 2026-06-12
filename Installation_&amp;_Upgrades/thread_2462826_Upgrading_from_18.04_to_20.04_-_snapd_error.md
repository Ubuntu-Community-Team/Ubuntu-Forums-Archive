---
title: "Upgrading from 18.04 to 20.04 - snapd error"
date: 2021-05-28
forum: Installation &amp; Upgrades
---

### Post by erdemaltuntac on 2021-05-28
Hello,

I am trying to upgrade to 20.04 from 18.04. I face the error message saying that my snapd is outdated. Then, it exits the upgrading. I check the snapd update, and it says that snapd is up to date.
Any help please?

Thanks

---

### Post by corradoventu on 2021-05-28
Try to remove snapd, you will reinstall after migration.

---

### Post by erdemaltuntac on 2021-05-28
Upgrading does not continue without snapd. It requires the updated snapd.

---

### Post by GhX6GZMB on 2021-05-28
Too bad you didn't follow our advice in your previous thread. We told you it would be tedious.
You now have a "bastardized" system. Congrats.

---

### Post by grahammechanical on 2021-05-28
Use the terminal to remove snapd and then reinstall snapd followed by apt update & apt upgrade.

```
sudo apt remove snapd
```

```
sudo apt install snapd
```

```
sudo apt update
```

```
sudo apt upgrade
```

Regards

---

### Post by erdemaltuntac on 2021-05-29
It didn´t work. I think this time I´m gonna have to reboot from a usb with backing-up all the data.

---

### Post by ajgreeny on 2021-05-29
Thread moved from Development Version to Installation and Upgrades for a better fit.

---

### Post by aska93 on 2021-06-25
I have the same god, nothing helps

---

### Post by monkeybrain20122 on 2021-06-25
Just do a fresh install. Take you much less time and effort than to upgrade from a messy system.

---

