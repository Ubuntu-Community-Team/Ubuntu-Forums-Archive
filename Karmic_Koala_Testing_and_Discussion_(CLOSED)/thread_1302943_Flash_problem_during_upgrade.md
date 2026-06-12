---
title: "Flash problem during upgrade"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Jesus_Valdez on 2009-10-27
I upgrade my laptop using  the alternate CD, and everything went well untill flashplugin falied and broke the upgrade.

Now I cant login into gnome (well, I can but all I see is my mouse pointer and a white screen) I see the new GDM and the Brown thing at the start.

Grub show the kernel 2.6.18, not the 2.31, I can login into LXDE but with really slow video graphics and no sound.

The panel shows me the error "Error Brokencount >0"

Edit. I found a Bug report on Launchpad [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841)

Im using AMD64 and the RC Version of the Karmic Koala.

---

### Post by psyke83 on 2009-10-27
From [today's upload]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/011919.html"):

> adobe-flashplugin (10.0.32.18-1karmic2) karmic; urgency=low

  * Fixed upgrade issues from jaunty by exiting normally after removing
    alternatives and by not issuing a remove-all as this could
    remove alternatives not owned by the package.

You should update your repository lists and install the updated package.

---

