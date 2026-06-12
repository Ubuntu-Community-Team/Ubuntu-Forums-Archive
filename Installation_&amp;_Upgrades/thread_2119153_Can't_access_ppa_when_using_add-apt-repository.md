---
title: "Can't access ppa when using add-apt-repository"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by JustSteph on 2013-02-23
Hi, I recently upgraded from 10.04 to 12.04. When I try to install utouch to fix my touchpad (lost multi-touch), I get the following error.

```
steph@Jarvis:~$ sudo add-apt-repository ppa:utouch-team/daily
Cannot access PPA (https://launchpad.net/api/1.0/~utouch-team/+archive/daily) to get PPA information, please check your internet connection.
```My internet is working fine, I'm using it now, and I'm not connected through a proxy. Can anyone help?

Edit: Also, I tried accessing the link it gives though the internet but the connection times out.

---

### Post by juzzlin on 2013-02-24
I'm experiencing this same problem on 13.04.

Edit: It worked when I added my PPA via Software Center. For some reason add-apt-repository doesn't work anymore.

---

### Post by dino99 on 2013-02-24
That ppa seems having been removed

[https://launchpad.net/~utouch-team/](https://launchpad.net/~utouch-team/)

---

