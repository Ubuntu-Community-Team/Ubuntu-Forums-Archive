---
title: "Run shell command at user logout"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by ubuntogenius on 2008-03-24
'd like to run the following command every time a user logs out of his Gnome desktop.

rm -Rf /tmp/*

Is there a way to execute this command automatically as soon as they log off? There is only one user on this system at a time.


OS - Ubuntu Linux 7.10

---

### Post by Th3Professor on 2008-03-25
You might consider any of these...
-modifying what type (if any) of shell access they have
-modifying their ~/.profile
-creating an automated shell script that overrides the generic logout command, precedes it with the actions you want, then ends with the logout

---

### Post by Oldsoldier2003 on 2008-03-25
> **ubuntogenius said:**
> 'd like to run the following command every time a user logs out of his Gnome desktop.

rm -Rf /tmp/*

Is there a way to execute this command automatically as soon as they log off? There is only one user on this system at a time.


OS - Ubuntu Linux 7.10

edit  /etc/gdm/PostSession/Default

---

