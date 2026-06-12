---
title: "Replacing XFree86 with X.org?"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by helwitch on 2004-10-25
I can not get the XServer to work with my laptop with XFree86 that comes with ubuntu, even after lots of help and suggestions from people in this forum. How difficult would it be (for a nearly total newbie like me) to remove XFree86 and install X.org? (and if it'd be difficult for noob me, how difficult would it likely be for one of my friends who actually knows what they're doing when it comes to linux?)
Cos a friend of mine suggested if one Xserver isn't working, trying a different one might help. Is this a good idea? bad idea? something that is worth a shot but isn't likely to help?

---

### Post by jdong on 2004-10-25
Trading X-Servers won't help you. Ubuntu's Xfree is 4.3.99 with patches, which is pretty darn close to X.org's.

Xorg is planned for Hoary (next release), and there's already Xorg debs for Hoary in the repository, but they probably aren't near-stable quality right now. I'd strongly advise AGAINST trying this big of an update on Debian, X has too many libs to be shoved into the wrong folders, it'll always cause hell later on.


Provide some info about the laptop and its video/monitor, let's see if we can config it.

---

### Post by emperor on 2004-10-25
If there is a package in the universe, I would think you would be save in giving it a try. If you have to download the source and compile it, I would say NO! You'd be better off installing another Distro in that case. Perhaps there are other people that have run into a similar problem with the X server. Sometimes the BIOS on the laptops needs to be updated for X to work right. This was true with my wifes Dell Inspiron 1000.  I would do a little research here if you have not already:
[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by FLeiXiuS on 2004-10-25
[QUOTE=helwitch]I can not get the XServer to work with my laptop with XFree86 that comes with ubuntu, even after lots of help and suggestions from people in this forum. How difficult would it be (for a nearly total newbie like me) to remove XFree86 and install X.org? (and if it'd be difficult for noob me, how difficult would it likely be for one of my friends who actually knows what they're doing when it comes to linux?)
Cos a friend of mine suggested if one Xserver isn't working, trying a different one might help. Is this a good idea? bad idea? something that is worth a shot but isn't likely to help?[/QUOTE]

Could you provide us with an ERROR log perhaps?

```
cat /var/log/XFree86.0.log |grep EE
```

This will allow us to solve the problem rather then to avoid it.

---

