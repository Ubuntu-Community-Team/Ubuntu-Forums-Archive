---
title: "Software updater not showing upgrade"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by coffeecat on 2014-01-11
I've moved your post into its own thread, and given it what I hope is a relevant thread title.

Since the thread you posted to mentioned Ubuntu 13.10 and the upcoming 14.04, it's possible you are running 13.10, in which case the Software Updater will not give you the option to upgrade to 14.04 until 14.04 is released near the end of April. If you are running a version of Ubuntu earlier than 13.10, please give further details and someone will be able to help you.

---

### Post by fantab on 2014-01-11
If your system is already uptodate then Software Updater will NOT show any updates.

Run the following in the Terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

Report back if you encounter any errors.

---

### Post by ibjsb4 on 2014-01-11
If your running 13.10 you can do a version upgrade to 14.04 using the -d option, just be prepared for breakage.

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

---

