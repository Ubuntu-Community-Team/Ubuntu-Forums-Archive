---
title: "Distribution Upgrade popped up??"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by SRTS on 2011-01-25
Just some minutes ago, a distribution upgrade box automatically popped up, I didn't realize it at first and just thought it was the normal auto-updating of packages, until I noticed it, and since it has no cancel-button I used xkill to kill it in panic, since I thought it might be some exploit, since I'm running 10.10 and 11.04 won't be available before april. Anyone know what the heck that was?? Thanks!

---

### Post by sikander3786 on 2011-01-25
That might be caused by some newly added Testing PPAs. But I am pretty sure it won't upgrade to 11.04, instead, it would upgrade a few pacakges on your current system.

Is it running now? If yes, don't try to cancel it or you may leave your system in an unstable position. There should be a list of packages being upgraded. Can you please post that?

---

### Post by lechien73 on 2011-01-25
I got the same thing. As far as I can tell it just upgraded the kernel image and removed old ones, and upgraded a few other things such as Wine and Evolution. Odd that it was a distribution upgrade, though.

---

### Post by SRTS on 2011-01-25
ok, I started Update Manager again.
It said that only a "partial upgrade" was possible.
The list of packages was displayed in the background, with a confirmation dialog blocking it in the foreground so I was unable to browse it. After closing the confirmation dialog, the package list disappeared too, that's a bit silly.
Well, after some working, now it shows me package lists again, it says:
Remove (1): Wine  (why remove? It wants to 'upgrade' it too though:)
Upgrade (17): jockey-common, jockey-gtk, libnautilus-extension1, libservlet2.5-java, linux-firmware, nautilus, nautilus-data, nvidia-96-modaliases, python-apt, tar, ttf-symbol-replacement-wine1.3, wine1.3, wine1.3-dev, xserver-common, xserver-xorg-core, xserver-xorg-dev, xserver-xorg-input-evdev

---

### Post by presence1960 on 2011-01-25
Go System > Administration > Update Manager. Bottom left on window click settings. Choose "Updates" tab. At bottom choose never for show new distribution releases.

I never do a dist-upgrade. I always do a clean install. You can make a file of all your installed packages and back it up. Once you do a clean install you move that file back to /home and run one command from terminal. All your previously installed packages will be installed as long as they are in the new releases repositories. Any third party software and software compiled from source will have to be manually installed. [Here]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") is the how to to accomplish this.

---

### Post by SRTS on 2011-01-25
This is strange, "About Ubuntu" really says now my version is 11.04, but shouldn't 11.04 come out in april, not january?

"You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012." <- ??? :-k

---

### Post by sikander3786 on 2011-01-25
> **SRTS said:**
> This is strange, "About Ubuntu" really says now my version is 11.04, but shouldn't 11.04 come out in april, not january?

"You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012." <- ??? :-k
Thats a bug I think. See here.

[http://ubuntuforums.org/showthread.php?t=1651745](http://ubuntuforums.org/showthread.php?t=1651745)

What is your output for

```
cat /etc/*release
```

---

### Post by Max2011 on 2011-01-25
I have only checked important security updates, recommended updates, NOT pre-released updates and NOT unsupported updates. Release upgrade is set to normal releases. I'm not expecting this until April.

I don't like, but understand that the update is trying to install some programs that I've removed, however I don't quite understand why it's trying to downgrade wine from 1.3 to 1.2. Stability? 

What is going on?

---

### Post by Frogs Hair on 2011-01-25
> **Max2011 said:**
> I have only checked important security updates, recommended updates, NOT pre-released updates and NOT unsupported updates. Release upgrade is set to normal releases. I'm not expecting this until April.

I don't like, but understand that the update is trying to install some programs that I've removed, however I don't quite understand why it's trying to downgrade wine from 1.3 to 1.2. Stability? 

What is going on?

If you have installed a higher version of Wine from another source and have not completely purged the stable version , when updates come  It will regress to the stable version because the update manager see the meta packages from the stable version and not the new version.

---

