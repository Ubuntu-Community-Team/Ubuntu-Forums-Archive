---
title: "Software Updater race condition"
date: 2017-03-26
forum: Installation &amp; Upgrades
---

### Post by PaulBx on 2017-03-26
I did the following:

1) Booted
2) Software Updater told me I had updates
3) I turned on my Internet connection
4) I then told Software Updater to go ahead, which it finished (requiring no reboot)
5) I then manually invoked Software Updater, which said there were more updates to do.

It seems SU is using old information about what updates need to be done, in the absence of an internet connection. I wonder if it should go out automatically after having finished an update with the old information, to inform the user (if necessary) there is more to be done after it has established the fact there is now an internet connection?

I am at Lubuntu 16.04 LTS

---

### Post by Autodave on 2017-03-26
I would do it manually if I were you. Turn on your internet connection. Then in a terminal, type "sudo apt-get update". When that finishes type "sudo apt-get upgrade". When that is finished, exit the terminal and you can shut off your internet connection.

---

### Post by Impavidus on 2017-03-26
Software updater tries to check for updates when it's started. When it fails, because there's no network or the server is down or whatever, it doesn't try again. And indeed, when software updater discovers it can download packages, it doesn't automatically check for new updates again. The devs sort of silently assume most users have a permanent internet connection.

In your case it may be best to do it manually. Whenever you want to check for updates, enable your internet connection, then update the list of available updates and download and install them. You can use software updater manually or synaptic or the terminal. You can change the settings for automatic updating to never have it check automatically. Without internet, you're not in too much of a hurry to install all updates.

If you use terminal, the proper way to do it in 16.04 is```
sudo apt update
sudo apt upgrade
```In contract to the apt-get commands, this will also install new packages is required to upgrade already installed packages, as is often the case with kernel upgrades. In contrast to apt-get dist-upgrade, it won't uninstall packages.

---

