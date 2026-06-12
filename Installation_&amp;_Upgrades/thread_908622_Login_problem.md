---
title: "Login problem"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by scalywag66 on 2008-09-02
Well, I got my brother to install Ubuntu, but his installation gives him a slight problem.

After inputting the log in, his screen goes black for a few seconds, and then takes him back to login.   What happened?

---

### Post by manishtech on 2008-09-05
Can he login through the virtual terminal..

When you get the login screen. Press Ctrl+Alt+F1 to get a text based terminal. Try to login at this place. If you can do this, then means that there is some problems with your Xserver.

To return back to Graphical press Ctrl+Alt+F7

---

### Post by Crafty Kisses on 2008-09-05
Your X is restarting for some reason, see if you get the X.org logs using gedit and post back.

---

### Post by manishtech on 2008-09-05
> **Codename said:**
> Your X is restarting for some reason, see if you get the X.org logs using gedit and post back.
He means post the content of **/etc/X11/xorg.conf** file

---

