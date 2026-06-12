---
title: "Upgrade from Linux Mint to Kubuntu"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by JustinAlf on 2007-12-13
Is it possible for me to upgrade my system from Linux Mint to Kubuntu?  If not I"ll wipe it clean, but I really want to be a KDE user for the time being without lossing my files.  Anyone know how to do this?

---

### Post by snickers295 on 2007-12-13
sorry, i don't think thats possibly.

---

### Post by confused57 on 2007-12-13
> **JustinAlf said:**
> Is it possible for me to upgrade my system from Linux Mint to Kubuntu?  If not I"ll wipe it clean, but I really want to be a KDE user for the time being without lossing my files.  Anyone know how to do this?
You could try installing the kubuntu-desktop:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install kubuntu-desktop
```

May or may not work, but since you're willing to wipe your Linux Mint clean, it won't hurt to try.

---

### Post by rsambuca on 2007-12-13
> **confused57 said:**
> You could try installing the kubuntu-desktop:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install kubuntu-desktop
```

May or may not work, but since you're willing to wipe your Linux Mint clean, it won't hurt to try.

That will work.  If you want to rid yourself of the mint menus etc, you can also just remove them via synaptic and delete the mint repo from your sources.list.  You will just be running *buntu after that.

---

### Post by snickers295 on 2007-12-13
oh, then if its ubuntu based then those commands will work.
sorry about that, its just that most ubuntu based systems have the word ubuntu in them (e.g. kubuntu, xubuntu edubuntu, goubuntu, fluxubuntu.).

---

### Post by JustinAlf on 2007-12-13
Thanks, I'll give it a try tonight and tell you how it went.

---

### Post by snickers295 on 2007-12-13
ok good luck!

---

### Post by rsambuca on 2007-12-13
> **snickers295 said:**
> oh, then if its ubuntu based then those commands will work.
sorry about that, its just that most ubuntu based systems have the word ubuntu in them (e.g. kubuntu, xubuntu edubuntu, goubuntu, fluxubuntu.).

Just thought you might be interested[ in this link]("http://www.debianadmin.com/list-of-ubuntu-based-linux-distributions-and-live-cds.html").  It lists the dozens of Ubuntu supported distros and other distros based on Ubuntu.

---

### Post by snickers295 on 2007-12-13
> **rsambuca said:**
> Just thought you might be interested[ in this link]("http://www.debianadmin.com/list-of-ubuntu-based-linux-distributions-and-live-cds.html").  It lists the dozens of Ubuntu supported distros and other distros based on Ubuntu.
see what i mean, a lot of those have at least "buntu" in it.

---

### Post by rsambuca on 2007-12-13
> **snickers295 said:**
> see what i mean, a lot of those have at least "buntu" in it.

Actually, my point was that a lot of them don't!
mEDUXa
ImpiLinux
Ichthux
X-Evian
SimplyMEPIS
gNewSense
MoLinux
Arabian Linux
Guadalinex
Linux Mint

---

### Post by rfruth on 2007-12-13
Mint (Gnome or KDE?) if free hard disk space permits would dual boot, Mint & Kubuntu work & play well together (there blood cousins)  :KS

---

### Post by snickers295 on 2007-12-13
> **rsambuca said:**
> Actually, my point was that a lot of them don't!
mEDUXa
ImpiLinux
Ichthux
X-Evian
SimplyMEPIS
gNewSense
MoLinux
Arabian Linux
Guadalinex
Linux Mint
exept for mempis, i have never heard of any of those.

---

### Post by JustinAlf on 2007-12-14
I ended up just wiping it clean.  I always do this when Mint comes out with a new Distro.  I always think its going to be bettor then Ubuntu, but it's never enough for me to stay, except for the menu, which is great.  But I"m going to stick with Kubuntu so that I can use KDE 4 when it comes out and I can be ready for it.

---

### Post by snickers295 on 2007-12-14
good because getting kubuntu-desktop gets real messy anyway.

---

### Post by rsambuca on 2007-12-14
> **JustinAlf said:**
> I ended up just wiping it clean.  I always do this when Mint comes out with a new Distro.  I always think its going to be bettor then Ubuntu, but it's never enough for me to stay, except for the menu, which is great.  But I"m going to stick with Kubuntu so that I can use KDE 4 when it comes out and I can be ready for it.

I don't know how you can say this since Mint is basically just Ubuntu with the Mint menu, themes, and codecs.

---

