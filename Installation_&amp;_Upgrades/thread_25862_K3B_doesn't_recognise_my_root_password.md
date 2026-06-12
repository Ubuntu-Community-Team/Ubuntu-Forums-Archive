---
title: "K3B doesn't recognise my root password"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by muzza on 2005-04-11
Last night I downloaded K3B using Synaptic.  It seemed to download and install OK. But when I start it, I get a dialogue box which says the following; 

**[COLOR=Red]cdrecord does not run with root priveleges[/COLOR]**
It is highly recommended to configure cdrecord to run with root privileges.  Only then cdrecord runs with high priority which increases the overall stability of the burning process. Apart from that it allows changing the size of the used burning buffer. A lot of user problems could be solved this way.  This is also true when using SuSE's resmgr.
*Solution:* Use K3bSetup to solve this problem.

I also need root privileges to use **[COLOR=Red]cdrdao[/COLOR]** (which I also downloaded)
*Solution: (again)* Use K3bSetup to solve this problem.

When K3b setup runs, it asks me for my root password, but tells me it's "Incorrect password! Please try again.

I tried typing the command it seemed to be looking for (kcmshell k3bsetup2 --lang en_US) in the terminal, but it tells me "kcmshell: command not found

Anybody know what I've done wrong?

By the way, I'm using Warty with the Gnome gui

---

### Post by muzza on 2005-04-11
Sorry, I think I've posted this in the wrong thread.  Could one of the moderators put it in the right cupboard??

Thanx

---

