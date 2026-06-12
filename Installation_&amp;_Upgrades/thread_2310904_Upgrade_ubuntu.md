---
title: "Upgrade ubuntu"
date: 2016-01-22
forum: Installation &amp; Upgrades
---

### Post by Paulus_Christofel_ on 2016-01-22
when i run sudo apt-get upgrade,
 there is one problem
E: Some index files failed to download. They have been ignored, or old ones used instead.


and when i run sudo apt-get update
E: The package google-chrome-stable needs to be reinstalled, but I can't find an archive for it.

how to fix that, masta?

---

### Post by Vladlenin5000 on 2016-01-22
Hi and welcome.

You probably know that but it isn't clear in your post, perhaps due to the order in which you mentioned the commands, but *update* should be run before [I]upgrade.
[/I]That said*, *try again tomorrow and make sure you do this sequence one at a time:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

The error message suggests the Google Chrome's PPA couldn't be reached which certainly is just a temporary problem.

---

