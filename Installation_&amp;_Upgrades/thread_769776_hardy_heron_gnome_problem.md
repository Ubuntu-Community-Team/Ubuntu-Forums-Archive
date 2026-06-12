---
title: "hardy heron gnome problem"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by abds on 2008-04-26
Hi,

I am having this weird problem. Everything loads ok. But after the login screen, when I input the username / password, gnome crashes and restarts and I am back to the login screen again. I tried this with both the 32-bit version and 64-bit version. Both are giving the same problem. The CDs are ok, since I already installed the 32-bit version on another system. I can not access the command line either. When I press ctrl+alt+1, it just freezes. This also happens when I try running from the live CD. 
I can log in by setting the session to Gnome failsafe. It seems to work fine when I do this. 

I am running an I have an Athlon 64 3000+, with 1Gb RAM, running on ECS RS480-M which has a built-in ATI X200.

Please help.. I really need to get the system up and running.

---

### Post by mathenge on 2008-04-26
Looks like you're able to get to a gdm login window which probably means that X is running fine.

Which probably means that it's the window manager that's failing. If it's gnome, it's probably metacity.

You could try logging into failsafe mode, then using apt to remove the window manager or at least to see what's happening when you try to start gnome at the command prompt (by typing gnome-session).

You can also take a look at logs in /var/log to see why it keeps bringing you back to the login prompt.

---

