---
title: "Dual booting problems!"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by fm232 on 2007-01-31
After installing ubuntu dapper I tried to do [this]("http://ubuntuforums.org/showthread.php?t=56723") so I could easily boot ubuntu at startup, but all I get is a flashing "_" and nothing happens. (windows xp boots fine). I used the dd command and everything seemed to work; I copied over the file to c: in windows, edited boot.ini etc, but, as desribed above, nothing happens? any Idea what could be wrong? (ubuntu still boots fine if I use a cd with grub)
Thanks for your help

---

### Post by fm232 on 2007-02-01
still no resolution:(

---

### Post by devils_casper on 2007-02-01
its seems graphics card problem. which graphics card do you have?
boot up Ubuntu in command line mode and execute 'startx'. what does it show? post error message if any.





Casper

---

### Post by fm232 on 2007-02-01
I have a radeon x800xt pe

if I type just "startx" I get:

xauth:  creating new authority file /home/phil/.serverauth.6025
X: user not authorized to run the X server, aborting.
xinit:  Server error.
Couldnt get a file descriptor referring to the console

if I type "sudo startx" I get:

xauth:  creating new authority file /home/phil/.serverauth.6061

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.
:confused:

---

### Post by fm232 on 2007-02-02
I'm still not sure what I can do:(

---

### Post by devils_casper on 2007-02-03
execute this
```

sudo dpkg-reconfigure xserver-xorg

```






Casper

---

