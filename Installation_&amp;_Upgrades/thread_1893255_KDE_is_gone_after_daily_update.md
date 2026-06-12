---
title: "KDE is gone after daily update"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by Leprechaun7 on 2011-12-09
My KDE under ubuntu was running fine and up to date yesterday. KDE told me I had a bunch of updates (I normally use update manager, but the KDE equivalent said it this time, maybe that the problem). I just hit OK and confirmed after the update KDE was acting funny, I rebooted and now KDE plasma is no longer an option for me to log in. Also I'm trying to reinstall KDE and some of the components appear to be installed in synaptics but when I try to install KDE-full desktop or plasma, I have missing dependencies. I don't know how to fix this either. Any clue on how to get my KDE back?

Has anyone else updated their KDE today and its gone like this?

Thank you.

---

### Post by kio_http on 2011-12-09
> **Leprechaun7 said:**
> My KDE under ubuntu was running fine and up to date yesterday. KDE told me I had a bunch of updates (I normally use update manager, but the KDE equivalent said it this time, maybe that the problem). I just hit OK and confirmed after the update KDE was acting funny, I rebooted and now KDE plasma is no longer an option for me to log in. Also I'm trying to reinstall KDE and some of the components appear to be installed in synaptics but when I try to install KDE-full desktop or plasma, I have missing dependencies. I don't know how to fix this either. Any clue on how to get my KDE back?

Has anyone else updated their KDE today and its gone like this?

Thank you.

Could you try

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get install -f
sudo apt-add-repository ppa:kubuntu-ppa/ppa
sudo apt-get update
sudo apt-get upgrade
sudo aptitude install kubuntu-desktop
```

---

### Post by Leprechaun7 on 2011-12-10
WOW! Totally fixed it. A million thanks! KDE is just how I left it. Any idea what happened?

for others looking at this thread for help, instead of the last line I used:

sudo apt-get install kubuntu-desktop

---

### Post by kio_http on 2011-12-10
> **Leprechaun7 said:**
> WOW! Totally fixed it. A million thanks! KDE is just how I left it. Any idea what happened?

for others looking at this thread for help, instead of the last line I used:

sudo apt-get install kubuntu-desktop

Yes, some dependency problem must have removed kde components. I recommend aptitude and not apt-get because

1) When you install a meta package like kubuntu-desktop and then remove it it does not remove just the meta package as apt-get would

2) It is much smarter when it comes to handling dependencies.

Actuall aptitude is recommended rather the apt-get in debian.

---

### Post by Leprechaun7 on 2011-12-10
Ah, the aptitude command didn't work for me since I didn't have aptitude installed. I thought apt was the same thing. I've installed aptitude now, Thanks again.

---

