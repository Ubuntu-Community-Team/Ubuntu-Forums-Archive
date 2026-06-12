---
title: "Login Screen still shows after login."
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by saquibahmed on 2013-05-11
**Hi All**
Login Screen still shows after login.Upgraded from 12.10 32Bit to 13.04 32Bit.I am able to use Unity & and other applications, but the login screen won't go away. I tried to change the wallpaper.Previously on 12.10, I had muliple Desktop environments, such as GnomeFallack, Gnome, KDE, XMBC Installed. I believed i have remove them before upgrading to 13.04.Surprisingly I have a work Gnome DE on 13.04. During installation it prompted me - If I want to replace some configuration files & I did, thought it would be better. I think my LDM is messed up. Any suggestions welcomed. Pic URL: [http://picpaste.com/raring.png](http://picpaste.com/raring.png)
Thanks

---

### Post by midnightramen on 2013-05-14
Not the same exact issue that i encoutered, but if you are running ATI graphics, you'll want to update the latest ATI linux drivers. 13.4, I believe. The login screen is actually the lightdm service, so there may be additional info on the logs at /var/log/lightdm/ .

---

