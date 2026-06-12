---
title: "Compiz update Oct 11 hangs Thinkpad"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2008-10-11
Updated Compiz today on Intrepid Beta.  PC hangs with black screen and frozen spinner at just the point Gnome should display the desktop.  

This is an IBM Thinkpad R31 which runs Intrepid Alpha 5, Hardy, Gutsy, Feisty, Edgy, Dapper O.K.  Intel Celeron 1 gHz, Intel graphics.  See bug 277344.

I'm using Xfce4 which runs O.K. 

Jerry

---

### Post by danbuter on 2008-10-11
Delete Compiz. By doing this, Ubuntu actually becomes pretty stable.

---

### Post by jerrylamos on 2008-10-11
O.k., how is Compiz deleted?  I tried removing it with synaptic, which worked however Firefox then crashes.

What is the method i.e. keystrokes to delete Compiz?

Thanks, Jerry

---

### Post by psyke83 on 2008-10-11
> **jerrylamos said:**
> O.k., how is Compiz deleted?  I tried removing it with synaptic, which worked however Firefox then crashes.

What is the method i.e. keystrokes to delete Compiz?

Thanks, Jerry

Don't "delete" compiz. If it's causing instability, turn it off in System/Preferences/Appearances/Desktop Effects.

---

### Post by danbuter on 2008-10-11
I'm guessing it's yet another stupid Ubuntu-made dependency. If you deleted it via Synaptic, it is gone. Maybe reinstall Firefox in case one of the libs for Compiz is required. Why the heck Canonical builds dependencies on beta software is beyond me.

---

### Post by jerrylamos on 2008-10-11
> **psyke83 said:**
> Don't "delete" compiz. If it's causing instability, turn it off in System/Preferences/Appearances/Desktop Effects.

That's a chicken and egg problem.  To do System/Preferences/Appearances/Desktop requires the desktop to be running.  The problem is the desktop didn't run.

I'm trying:
sudo apt-get remove compiz
sudo apt-get remove compiz-core

This is running successfully once.  I'll see if it holds up.

Thanks, Jerry

---

### Post by jerrylamos on 2008-10-11
Besides:

sudo apt-get remove compiz 
sudo apt-get remove compiz-core

I had to edit:

/etc/X11/default-display-manager
#/usr/sbin/gdm

otherwise Firefox gets an authority error and crashes.

switcher also won't load so I start a command line to halt or reboot.

I'll probably find some other bugs as well but at least it's running, first time since Alpha 6.

Jerry

Note switcher

---

