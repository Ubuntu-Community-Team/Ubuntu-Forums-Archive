---
title: "Firefox 2.0: unable to download plugins"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by sohaibma on 2007-02-06
i installed firefox. 2.0 on my dapper system (in the /opt directory). Now when i go to a website that requires a certain plugin (eg. java,flash), firefox asks me to install the missing plugin. when i try to install it firefox shows that it was unable to download the plugin and that i should install it manually. I have installed the plugins like flash and Java manually (repos and Adobe website), but why isn't firefox unable to download the plugins itself as in windows xp.

why?

---

### Post by taurus on 2007-02-06
Did you install those plugins in ~/.mozilla/plugins?

---

### Post by sohaibma on 2007-02-06
the problem isn't the installation of plugins, i can install the plugins manually.
the problem is how to install plugins from within firefox.
is there any way to fix this problem

---

### Post by DJ_Peng on 2007-02-11
You may also want to check with the guys in the [Firefox Support]("http://forums.mozillazine.org/viewforum.php?f=38") forum over at Mozillazine. They support all OS's so someone there may have run into what you're dealing with.

---

### Post by tubasoldier on 2007-02-11
> **sohaibma said:**
> the problem isn't the installation of plugins, i can install the plugins manually.
the problem is how to install plugins from within firefox.
is there any way to fix this problem

It is not a bug, or a problem, its a feature. Believe it or not you can not install plugins for Firefox within Firefox because as a user you do not have write access to your /opt directory. Installing plugins in Linux should be done manually. This removes the chances of some website being able to upload malicious code into your web browser.

---

### Post by vgrisham on 2007-03-04
> **tubasoldier said:**
> It is not a bug, or a problem, its a feature. Believe it or not you can not install plugins for Firefox within Firefox because as a user you do not have write access to your /opt directory. Installing plugins in Linux should be done manually. This removes the chances of some website being able to upload malicious code into your web browser.

Tubasoldier (or anyone else), where might one find a howto on installing plugins manually?

---

### Post by DJ_Peng on 2007-03-04
> **tubasoldier said:**
> It is not a bug, or a problem, its a feature. Believe it or not you can not install plugins for Firefox within Firefox because as a user you do not have write access to your /opt directory. Installing plugins in Linux should be done manually. This removes the chances of some website being able to upload malicious code into your web browser.
This, and the fact that I can't fetch updates from within Firefox itself, is the main reason why I opted to not use the repository version of Firefox and go with the code straight from Mozilla. IMO this breaks a major feature of the program, and while I understand why i was done is actually pretty useless if you only get extensions from AMO. They guard what goes there pretty closely and if an extension (or a theme) opens a security hole they'd either get rid of it *tout de suite* or never accept it in the first place.

---

