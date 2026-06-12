---
title: "unsupported wmi"
date: 2014-02-01
forum: Installation &amp; Upgrades
---

### Post by scholzilla on 2014-02-01
My idiot roommate closed my laptop in the middle of an install of 13.10. The result: when booting up I get the message "no or unsupported wmi interface". I then get the login screen and when I enter my password, the system just hangs. I've tried to follow the advice here: [http://www.tuxgarage.com/2011/07/creating-chroot-ubuntu.html](http://www.tuxgarage.com/2011/07/creating-chroot-ubuntu.html), but I can't actually get to a shell. I'm out of my depth already here, but when I use control+alt+f1 and am asked for a login name and password, it doesn't accept what was my login name and password. Presumably, if I can't login I can't get get sudo privileges anyway. I'm not well-versed enough to know another way. I don't want to do a clean install and lose some data that I (stupidly) didn't back up before the install. Is there another way? fwiw, my computer is a gateway mt6452 w PhoenixBIOS version 84.05

---

### Post by scholzilla on 2014-02-01
An update: I got into recovery mode by holding Shift down during boot up and selecting the latest kernel (recovery mode). From the menu, I enabled networking. Then I went to root and typed in 
```

apt-get update && apt-get upgrade

```
A long list of "hits" appeared followed by archive addresses. In the end, all the package lists were read, but nothing was upgraded, installed, or removed. I exited root and rebooted. The problem persists.

---

### Post by scholzilla on 2014-02-03
buhler?

---

