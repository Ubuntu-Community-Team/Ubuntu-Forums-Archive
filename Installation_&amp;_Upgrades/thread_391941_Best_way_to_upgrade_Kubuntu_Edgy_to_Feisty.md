---
title: "Best way to upgrade Kubuntu Edgy to Feisty?"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by clintonthegeek on 2007-03-23
Hey all!

Reading through the Upgrade instructions ([https://help.ubuntu.com/community/FeistyUpgrades)](https://help.ubuntu.com/community/FeistyUpgrades)), I have no idea what the best way is for upgrading my install of Kubuntu Edgy to the new Feisty Beta. There is no "upgrade-manager" installed on my system... should I apt-get install it? Or is it only suited for Gnome or something?

Or should I follow the Server upgrade instructions?

Help me out,

-Clinton

---

### Post by axcairns on 2007-03-23
The tool you are looking for is *update-manager*. Not upgrade-manager.

Allan

---

### Post by clintonthegeek on 2007-03-24
> **axcairns said:**
> The tool you are looking for is *update-manager*. Not upgrade-manager.

Allan

Crap! Typo. At any rate, it doesn't matter 'cause there is no "update-manager" installed by default in Kubuntu anyways.

```
clinton@clinton-desktop:~$ sudo update-manager
Password:
sudo: update-manager: command not found
clinton@clinton-desktop:~$
```

Anyways, here's what apt-cache has to say:
*update-manager - GNOME application that manages apt updates*

That's why I'm hesitant to use it.... is there any differences upgrading in KDE that it won't account for?

-Clinton

---

### Post by Rashid584 on 2007-03-24
[https://wiki.kubuntu.org/KubuntuDistUpgrade](https://wiki.kubuntu.org/KubuntuDistUpgrade)

I tried it myself and adept halts at some point (can't remember where exactly) and aptitude doesn't start the graphical dist-upgrade thing like Adept is supposed to...

why do they insist on us using Adept? Personally, I think adept is crap, I prefer using yakuake and aptitude...though I appreciate Adept's usefulness for new users.

Still, I did a sudo aptitude dist-upgrade, it upgraded a load of packages but nothing else has changed really...am I now running feisty 7.04 beta? :S

-Rashid

---

