---
title: "apt-get Probs"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by wavz on 2007-02-02
I tried running apt-get a while ago to update Beryl and an error message came up saying that one of the files was broken or something like that, and now apt-get is stuck saying that another instance of apt-get or adept is running and will not allow me to do anything. Is there a way to check what programs are running and how do I end them to get this prob fixed? Thanks in advance!

                                                                                                                                                        Wavz:guitar:

---

### Post by seshomaru samma on 2007-02-02
Open a terminal and run:
```
 ps ax
```
this will show you all programs
```
sudo ps ax
```
will show you some more


this is a part of the output i get for ps ax :
```
 5323 ?        Ssl    0:14 /usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c so 5325 ?        Ss     0:00 /usr/lib/scim-1.0/scim-launcher -d -c socket -e socke 5350 ?        S      0:01 /usr/lib/notification-daemon/notification-daemon
 5372 ?        Ss     0:02 gnome-screensaver
 9902 ?        Sl     1:32 /usr/lib/firefox/firefox-bin -a firefox
12046 ?        Rl     0:01 gnome-terminal
```
if you want to terminate a programme , use the kill command followed by the PID number
so if I wanted to end Firefox I would go:
```
kill 9902
```

---

