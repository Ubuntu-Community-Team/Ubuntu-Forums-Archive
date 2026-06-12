---
title: "partial ibex install....."
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by notsointrepid on 2008-11-02
Hello!

I've been running hardy happily on a windows pc, having used the wubi installer to put it on my xp machine. Yesterday I tried to grab some ibex goodness, and it did most of it, hanging at the end. Foolishly, I went out then - and wasn't there to see what happened when it finished. Reloading it, I don't seem to have any of the ibex features. I can't update - it says I must run a partial upgrade, and then brings up the error message 'An upgrade from 'intrepid' to 'hardy' is not supported with this tool'. The Software Sources panel will not load anymore either.

Does anyone have ideas how to fix this one?

Any help is most appreciated. I'm new to Ubuntu, but really impressed with what I've seen so far, so would love it to all work again nicely!

---

### Post by notsointrepid on 2008-11-02
Is there any way to rollback an install, or save settings for a clean install?

---

### Post by Partyboi2 on 2008-11-02
In a terminal try
```

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```Unfortunately you can not roll back a distro upgrade without doing a clean install. To save your important stuff you would need to boot a ubuntu live cd and mount your ubuntu system and recover your wanted files that way.

---

### Post by notsointrepid on 2008-11-02
One very happy camper here - Ibex is up and running. Following the commands above even made the visual effects work, which they hadn't done previously. Thank you very much for your help!

---

