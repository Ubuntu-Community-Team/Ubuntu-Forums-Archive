---
title: "Login strange behavior"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by frepie on 2014-05-10
Hi
I recently did an installation of lubuntu on an old computer. Everything works fine but for some reason, when restarted, the login and password are not required to access the user session. When suspend is selected, login and password are requested to access the user session.

Can anyone help?

Thank you

---

### Post by sudodus on 2014-05-11
Does it work if you change the settings with

```
users-admin
```

or from the menu ```
Users and groups
```

If that does not work try according to this tip from NikTh

> I think you can use the "old fashion" way, but you have to create the
lightdm.conf file which is not exist anymore.

```
gksudo gedit /etc/lightdm/lightdm.conf

```
should (now) open an empty file. There you can add

```
[SeatDefaults]
autologin-user=USERNAME
autologin-user-timeout=0

```
where USERNAME replace it with yours.

Save the file and restart lightdm.


---

