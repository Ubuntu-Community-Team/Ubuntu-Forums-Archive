---
title: "upgrade problems - No unity No menubar packages deleted menus in German!"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by thespud on 2012-05-15
Hi there,

Firstly - let me say, while i have been using ubuntu for a while, i still havent delved too much into the debugging - so please tread lightly with me...

I just did an upgrade from 11.10 to 12.04.  All seemed to go smoothly in the install except for a few errors about broken packages, which i expected for some such as pam-face-authentication and possibly things like hugin.

However, upon first boot - not only are my menus in German (!), even though in Language settings i have English (Australia) and English (United kingdom) above German in the list and applied system-wide.  I know some, but not enough to navigate my way around a system!

So, other than German menus - the biggest problem is the fact that i have NO unity, no launcher, and no top bar.  So i cannot launch programs except by opening multiple terminal windows by using Ctrl+Alt+T and moving windows around to get to the others - because unity is gone - there is no Alt+Tab!

To add insult to injury - the problems i have been having with firefox are persitent (i lose back arrows quickly - a bug report has been filed, but no-one can reproduce my bug), chromium, evolution (again, i was having issues with thunderbird) and the nvidia-settings packages were all deleted!  In an upgrade!  And these are only the ones i have gone looking for so far...  I hope i havent lost my shotwell database too, as this is the biggest reason i use ubuntu!

Strangely - all of my wine desktop shortcuts are there - as is my old desktop background.

I know its a long post - and a very strange case.  I am probably going to have to rebuild and start again - but i was REALLY hoping i didnt have to!  I had just got this thing the way i wanted it :(   I think i might just stick to LTS to LTS from now on...

Btw - It is an Acer Aspire 5738G Laptop - that up until today ubuntu 10.10, 11.04 and then a fresh install of 11.10 ran flawlessly on!

Thanks in advance for your help,
Scott!

---

### Post by cortman on 2012-05-15
> **thespud said:**
> Hi there,

Firstly - let me say, while i have been using ubuntu for a while, i still havent delved too much into the debugging - so please tread lightly with me...

I just did an upgrade from 11.10 to 12.04.  All seemed to go smoothly in the install except for a few errors about broken packages, which i expected for some such as pam-face-authentication and possibly things like hugin.

However, upon first boot - not only are my menus in German (!), even though in Language settings i have English (Australia) and English (United kingdom) above German in the list and applied system-wide.  I know some, but not enough to navigate my way around a system!

So, other than German menus - the biggest problem is the fact that i have NO unity, no launcher, and no top bar.  So i cannot launch programs except by opening multiple terminal windows by using Ctrl+Alt+T and moving windows around to get to the others - because unity is gone - there is no Alt+Tab!

To add insult to injury - the problems i have been having with firefox are persitent (i lose back arrows quickly - a bug report has been filed, but no-one can reproduce my bug), chromium, evolution (again, i was having issues with thunderbird) and the nvidia-settings packages were all deleted!  In an upgrade!  And these are only the ones i have gone looking for so far...  I hope i havent lost my shotwell database too, as this is the biggest reason i use ubuntu!

Strangely - all of my wine desktop shortcuts are there - as is my old desktop background.

I know its a long post - and a very strange case.  I am probably going to have to rebuild and start again - but i was REALLY hoping i didnt have to!  I had just got this thing the way i wanted it :(   I think i might just stick to LTS to LTS from now on...

Btw - It is an Acer Aspire 5738G Laptop - that up until today ubuntu 10.10, 11.04 and then a fresh install of 11.10 ran flawlessly on!

Thanks in advance for your help,
Scott!

Whew. You really go hit with the upgrade problems.
My personal recommendation- salvage all your data (copy your entire ~/ including all hidden files) and do a fresh installation. If you grab your whole home folder your Shotwell databases should be in there as well.

---

### Post by thespud on 2012-05-23
An update on this - I got it working finally!

As far as the German goes - there seems to be a bug in the system that means that there are no translations for en_AU, en_GB or en_US for things like lightdm login and terminal.  Might have to search launchpad for that one...

As far as my packages go, after much fiddling i realised that they had (thankfully) not been purged, so upon reinstalling i was able to restore them all to how they were (phew!)

As far as unity goes - i found a few conflicting stories, so i will explain how i did it and what worked for me.

Firstly, after logging in in 2D mode - i went to the startup applications and removed anything that had been deleted, so that these werent conflicting, then logged out, logged back in as 3D (still minus unity) then opened a terminal (Ctrl+Alt+T) and typed the following):

```
sudo apt-get --yes install ccsm && sudo ccsm 
```

Once ccsm had opened, scrolled down to unity, turned it on, and once all of the conflicts and bits that needed to be turned on were, unity appeared.

Restarted for good measure, and it has worked perfectly since!

---

