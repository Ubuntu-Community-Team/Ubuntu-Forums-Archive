---
title: "Lost panel custom launchers under gnome"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by wgw on 2013-01-02
After upgrade to 12.04, the Unity toolbar has the custom launchers I had added to gnome panels under 10.04. When I go to gnome classic however, the panels aren't there, and there are no launchers.  :(

I would like to resurrect them in gnome classic, or at least see the code I put in the command line of the launchers. 

Where is that information stored? Is there a way to see launcher properties in Unity? Under gnome, you can edit the launcher's command. If I could do the same under Unity, I could at least see how I configured those launchers and then redo them.  

Thanks!

---

### Post by ibjsb4 on 2013-01-03
Your now on gnome3 and I would guess that your launchers are lost and need to be reinstalled.  

Try reinstalling "gnome-panel" to bring back those missing panels in Classic.

---

### Post by Frogs Hair on 2013-01-03
Gnome 3 Classic uses a completely different panel than Gnome 2 from 10.04. In Gnome 3 classic you can access panel properties and the add to panel menu with Alt + Right Click or Super Key + Alt + Right Click.

---

### Post by wgw on 2013-01-03
Thanks for you comments.

I got the panels working, and then poked around some more and found /home/me/.gnome2/panel2.d/default/launchers. And voilà! my old panel launchers. I just dragged and dropped them on to my new panels and revoilà! I'm good. 

Another success story for blind poking around in configuration files! Of course, it could have had a terrible ending... :biggrin:

I do wonder why they are lost in gnome3 but not in Unity...

Probably an upgrade issue, that Unity handles better than gnome.

Again, many thanks for your suggestions.

---

