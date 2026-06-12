---
title: "Can't log on to default user on persistent Lubuntu 10.10 after setting password"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by ranm on 2010-12-29
After setting up a persistent Lubuntu (10.10) on a 4GB SD with Universal-USB-Installer-1.8.1.8 , I started changing the passwd of the original user ubuntu , but after rebooting, I can't log in. 

So I resorted to hitting Ctrl+the function key that gives you a CLI, and changed the password for "ubuntu" user then tried to log on again. [COLOR="Red"]No success[/COLOR].

Then I created a new user with a password, and managed to log in with this user, but it is not the same experience, the menus are lacking, and it is not possible to log on to wifi, [similar problem to this user ]("http://ubuntuforums.org/showthread.php?t=1654409"). [COLOR="red"]No success[/COLOR].

Anyone with an idea to why I can't log in ?

---

### Post by C.S.Cameron on 2010-12-29
Instead of creating a new user change the name of the default user and password in users and groups.

---

### Post by ranm on 2010-12-29
Thank you for your reply.

The thing is, my menus are just showing "Run" and "Logout", not the other elements such as Preferences, Accessories, Office and so on. Because of that I have no way to change the user in users and groups, unfortunately. 

I can start the terminal by pressing Ctrl+Alt+T and maybe input something there? What is the command to start "users and groups" from a CLI ?

---

### Post by C.S.Cameron on 2010-12-29
> **ranm said:**
>  

I can start the terminal by pressing Ctrl+Alt+T and maybe input something there? What is the command to start "users and groups" from a CLI ?

```
users-admin
```

Edit:
Oops, now that I recall, I did not change the existing user, I made a new user, changed the Account type to Administrator and added a password.
The next time I logged on I was the only user listed in Users and Groups.

---

