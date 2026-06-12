---
title: "xinit install on Samba error... please help"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by zoomiest on 2008-02-13
I just installed Samba with Gutsy Gibbon, on an old PIII machine for a home file server... and I got a couple of errors. I wonder is someone could help me out...

ran startx and the terminal said I didn't have it, but with ```
sudo apt-get install xinit
``` ... then I could install it, so I did. But now when I run startx again, the terminal says ```
xauth: creating new authority file /home/allan/.serverauth.4532
X cannot stat /etc/x11/x (no such file or directory)
xinit: server error
```

so... do I have more to install? I guess a base server install leaves out any windowing...
My goals is to be able to open up X and administer the system, and then close X, so it runs lean while it is serving up the files.

Compaq Deskpro Pentium III, 200 MB
Ubuntu 7.10 Server cd. (installed as both file server & print server)
[B]
 - Oh forget it... I will do this all with command line and vi. [/B] There is enough documentation out there.

---

