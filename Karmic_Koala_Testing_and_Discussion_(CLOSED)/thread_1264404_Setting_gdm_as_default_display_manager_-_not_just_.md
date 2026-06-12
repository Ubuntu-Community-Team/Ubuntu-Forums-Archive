---
title: "Setting gdm as default display manager - not just temporarily"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by godhika on 2009-09-12
I got the following, well lets call it problem: I am running Karmic and additionally installed the kde package. This changed the usplash to ksplash ( no problem for me, since hopefully we will see the full xsplash bling during the whole boot sequence) and the default display manager to kdm. so far, no problem, as I can easily change that in /etc/x11/default-display-manager. But now here comes the really annoying part. Everytime there comes some bigger update, the default display manager is set back to kde. Anyone an idea how to change that permanently back to gnome?

---

### Post by renkinjutsu on 2009-09-12
have you
```
sudo dpkg-reconfigure gdm
``` yet?

---

### Post by godhika on 2009-09-12
Doh - should have tried that first. but I just found that that added another 6 seconds to my boot time. Between ksplash and the start of xsplash appears now for a few seconds a text mode bootscreen once again. Btw am I the only one who observed a mayor regression in boot times since alpha 3 ? with the 2.6.31-4 kernel I had around 21 seconds (basically the same es under Jaunty) and now I am at 46 seconds!

---

### Post by Leighman on 2009-09-12
I'm having the same problem here.  Every time I get an update for kdm it resets itself as default.  Definitely tried the above before but not recently so I will try it again and keep watch for a while.

---

### Post by misfitpierce on 2009-09-12
When you login you don't have the session option at bottom still? Cause you can select session there and click permanently through there... I don't have much experience with ksplash or KDE for that matter lol.

---

### Post by taavikko on 2009-09-12
> **renkinjutsu said:**
> have you
```
sudo dpkg-reconfigure gdm
``` yet?

If that fails, editing /etc/X11/default-display-manager is the next step.
to point to desired manager (/usr/sbin/gdm) for gdm

---

### Post by Leighman on 2009-09-12
I currently have to edit that file after every kdm update

---

### Post by godhika on 2009-09-12
> **taavikko said:**
> If that fails, editing /etc/X11/default-display-manager is the next step.
to point to desired manager (/usr/sbin/gdm) for gdm
I am aware of that. My whole point is, like the previous poster noted, that this setting is set back to /usr/bin/kdm after every kdm update. So my question is, how is it possible to set this permanently (and not just til the next update)?

---

### Post by taavikko on 2009-09-12
> **godhika said:**
> I am aware of that. My whole point is, like the previous poster noted, that this setting is set back to /usr/bin/kdm after every kdm update. So my question is, how is it possible to set this permanently (and not just til the next update)?

Easy fix, remove the kdm package. 
It will also remove kubuntu-desktop though.
But it keeping an eye out for new dependencies of it, it shouldn't matter, since you can install them by hand.

---

### Post by snkiz on 2009-09-13
reinstall gdm after kdm and set as default in install process. It used to work. Try that, if it doesn't work file a bug, its a regression.

---

