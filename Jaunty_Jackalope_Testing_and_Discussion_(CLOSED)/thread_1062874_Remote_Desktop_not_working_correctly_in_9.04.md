---
title: "Remote Desktop not working correctly in 9.04"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sizzlefire on 2009-02-07
Hello, I have been using ubuntu for a while now, and just currently decided to upgrade to ubuntu 9.04 Alpha, and everything has been working fine, except remote desktop. I'm not sure what exactly is causing it, but every time I connect to the computer via tightvnc or ultravnc on a windows machine, the mouse is constantly a good inch or so off to the right. Is there any way for me to fix this?

---

### Post by ptn107 on 2009-02-07
Report it.

[https://bugs.launchpad.net/ubuntu/jaunty](https://bugs.launchpad.net/ubuntu/jaunty)

Click 'Report a bug' in the center of the page.

---

### Post by sizzlefire on 2009-02-07
Alrighty, thank you, I figured it was a bug, but I wanted to make sure.

EDIT: Its reported.

[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/326598](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/326598)

---

### Post by ptn107 on 2009-02-07
Nice.  It should keep you in the loop about the bugs progress via email.  They may ask you to provide some more information in order to help them fix it.

---

### Post by sizzlefire on 2009-02-08
Yea it has been confirmed by somebody now, and it has been keeping me up to date, cant wait till its fixed, its a bit annoying :P

---

### Post by diablo75 on 2009-02-08
> **sizzlefire said:**
> Yea it has been confirmed by somebody now, and it has been keeping me up to date, cant wait till its fixed, its a bit annoying :P

It's alpha software.  What did you expect?

---

### Post by sizzlefire on 2009-02-10
No, I know its going to have bugs in it, thats why its not on my main computer, I expected that, as I have used alpha software before.

---

### Post by vishnu on 2009-03-19
i have a problem with remote desktop in jaunty alpha 6 when i connect to my jaunty box with vncviewer.

i move the mouse and see it move in the remote screen but when i click on anything i do not see any result of that click.  e.g., when i click on "System" the menu doesn't drop down.  it's as though i'm in view only mode.  however, when i physically look at the actual jaunty box i see that the menu has dropped down.  seems to be an issue with sending refreshed images back to the remote viewer.  i have tried vncviewer, tightvnc, etc all with the same results.

does anyone else have this problem?

---

### Post by vishnu on 2009-03-25
fixed it.  disabled compiz.

---

### Post by shanepardue on 2009-03-31
> **vishnu said:**
> fixed it.  disabled compiz.
That stinks we have to disable Compiz for remoting now!

---

### Post by diablo75 on 2009-03-31
> **shanepardue said:**
> That stinks we have to disable Compiz for remoting now!

Seriously??? (Can this be confirmed anyone?)

---

### Post by shanepardue on 2009-03-31
> **diablo75 said:**
> Seriously??? (Can this be confirmed anyone?)
We've both confirmed disabling compiz fixes the issue.

---

### Post by scaine on 2009-04-01
Or you can use x11vnc to set up your session on the remote device.  When you start x11vnc, make sure that you pass the "noxdamage" paramater, so that your command line looks like :

x11vnc -usepw -forever -noxdamage

It's a much better service than the one that they built into gnome.  It also supports scaling, for large remote screens.  Very nice, pretty easy to use.  Just stick that line into your preferences/start up.

---

### Post by Xsoldier2000 on 2009-04-07
> **scaine said:**
> Or you can use x11vnc to set up your session on the remote device.  When you start x11vnc, make sure that you pass the "noxdamage" paramater, so that your command line looks like :

x11vnc -usepw -forever -noxdamage

It's a much better service than the one that they built into gnome.  It also supports scaling, for large remote screens.  Very nice, pretty easy to use.  Just stick that line into your preferences/start up.

Awesome and PERFECT advice. This fixed all my problems, though when I SSH in with putty, I add the -q "quiet" parameter so I don't see every little change x11vnc does.

My command line looks like this:

```
x11vnc -usepw -forever -noxdamage -q
```

---

### Post by scaine on 2009-04-08
You should "man x11vnc" on a quiet evening - there's a whole of reading for this tool!  I think my full command is something like :

```
x11vnc -usepw -forever -noxdamage -scale 4/5 -avahi -timeout 60 -nolookup -q
```

-avahi will mean that the server will advertise itself using avahi (multicast dns)
-scale 4/5 will mean that a 1900x1200 screen will fit on a 1280x1024 screen
-nolookup means that the server won't try to lookup the client.  No long pauses.
-timeout just specifies how long the server will wait for a client to connect before sleeping again.

---

