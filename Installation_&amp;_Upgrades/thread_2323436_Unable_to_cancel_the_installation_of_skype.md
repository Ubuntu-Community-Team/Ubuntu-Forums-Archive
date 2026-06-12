---
title: "Unable to cancel the installation of skype"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by jackysochiwang1115 on 2016-05-05
Hi all!
I am new to ubuntu and I have installed ubuntu 16.04. I tried to install skype from the package that is provided by their official site. I am aware that they do not have a package available for ubuntu 16.04 but as a new user I did not consider that at the time. As expected the installation fail and through some research online I now know what mistake I've done. However, the "waiting to install icon" remains on my launcher and doesn't seems to go away. I've try the killall -9 apt-get command in the terminal but it says no process found. I've also checked the status of the package "skype" and terminal tells me it is not installed. Which means skype is not install nor installing and the icon is merely there for no purpose. Is there anyone have the same problem or know how to fix it?

Thank you for your help

---

### Post by khelben1979 on 2016-05-05
How did you uninstall the Skype application?

I'm thinking there could be some configuration files around. apt-get purge <package> removes it in a clean way.

---

