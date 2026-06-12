---
title: "Software center not clearing"
date: 2018-10-28
forum: Installation &amp; Upgrades
---

### Post by zaivala on 2018-10-28
I installed a package from a saved .deb file. Now when I open the Software Center, it still shows that software [package, I can uninstall it or nothing. I hit the Back arrow and nothing happens. I close the Software Center and reopen it, same thing. I can change my Software & Sources, but can't get to new software.

---

### Post by TheFu on 2018-10-29
Why would you expect APT to be able to magically install a fresh version of something that you manually installed from a source completely unknown to APT?

Installing from a .deb file is the 3 best way to install software and by doing so, you've accepted the requirement to manually upgrade/patch that file forever.  After 3-6 months, it is likely that APT will prevent further updates for other packages due to the dependencies.  When that happens, you'll need to remove this .deb file, do all the upgrades.

Probably not what you want to hear, but that is reality.  APT isn't magic.

---

### Post by mc4man on 2018-10-29
Probably [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1798053](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1798053)

---

### Post by zaivala on 2018-10-30
I believe you misunderstood me. 

The app works fine. Indeed, I installed it from a .deb file, and expected Ubuntu Studio to open it with Gdebi, not with the Software Center.

Now, though, when I open the Software Center (to look for other software, or to look for updates), it still only shows the screen for installing the app, which is already installed.

I did solve the problem -- by changing desktops (to MATE).

---

