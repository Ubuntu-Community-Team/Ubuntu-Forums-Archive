---
title: "ubuntu 11.10 partial upgrade, no unity bar, can't go past login screen"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by SImranAliShah on 2011-10-15
HELP me out!!!!!!!!!

I have recently upgraded from ubuntu 11.04 to 11.10. The problem is that i can not go past the login screen with my existing username/password. 
By Ctr+Alt+F1 i was able to create a newuser and login, but the unity bar is not shown, i am launching programs using terminal. Update-manager also fails to update. I have Toshiba Pro L640. 

I had no problems after upgrading 11.04 to 11.10 on the other laptop (DELL vostro 1310).

---

### Post by rajwarrior on 2011-10-15
> **SImranAliShah said:**
> HELP me out!!!!!!!!!

I have recently upgraded from ubuntu 11.04 to 11.10. The problem is that i can not go past the login screen with my existing username/password. 
By Ctr+Alt+F1 i was able to create a newuser and login, but the unity bar is not shown, i am launching programs using terminal. Update-manager also fails to update. I have Toshiba Pro L640. 

I had no problems after upgrading 11.04 to 11.10 on the other laptop (DELL vostro 1310).

Hi,

Since you were able to create new user, your original username / password works in terminal. Suggest you run sudo apt-get dist-upgrade and see if any packages have been held back while you installed (broken upgrade). If so try running through the dist-upgrade.

As for missing unity bar, you need to click the small settings gear wheel next to login fields and select ubuntu rather than gnome classic as your desktop.

cheers

---

