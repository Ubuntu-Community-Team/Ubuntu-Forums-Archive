---
title: "Might want to skip current updates!"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2013-04-27
I installed the 13.04 Xubuntu beta2 and Ubuntu Studio beta2 and both were working well until I allowed the automatic updates yesterday.  Now both crash back into the login screen if I do much of anything :(

Updates to the beta had been making small improvements, until yesterday morning (Xubuntu) and last night (Studio) updates.

I've sent crash reports until I got tired of sending them :(

Two very different systems, one AMD 8-core with Nvidia GT-650 card running Nouveau, the other dual core Intel with Nvidia drivers as automatically installed by the installer (Studio)

---

### Post by dino99 on 2013-04-27
maybe check the /etc/apt/sources.list validity
and watch the logs to know what is wrong, an app might have a huge issue

---

### Post by wkulecz on 2013-04-27
> **dino99 said:**
> maybe check the /etc/apt/sources.list validity

Any problems here came from the installer initially or an update, so how can I have any idea on what to check?


> and watch the logs to know what is wrong, an app might have a huge issue

As far as I can tell just about any app will cause the crash, even launching xfce terminal.

---

### Post by wkulecz on 2013-04-29
Going into "Settings"->"Session and Startup" choosing "Advanced" tab and unchecking "Launch GNOME services on startup"  so far seems to have stopped the crashing back to the login screen.

Why are these GNOME and KDE service options there?  What is the installer's default?  Would installing other software change it?  I know I didn't mess with it until I stumbled on to it while trying to permute options in an attempt to get back to the working system I had before Friday's "updates" broke it.  Right now, neither option is checked and the system seems to be working fine -- at least its not crashing.

This was on Ubuntu Studio, I'll try the straight Xubuntu system when I get back tomorrow.

---

