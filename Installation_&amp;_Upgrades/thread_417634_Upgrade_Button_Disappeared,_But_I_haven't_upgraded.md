---
title: "Upgrade Button Disappeared, But I haven't upgraded!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by tiglionabbit on 2007-04-21
I haven't upgraded to feisty, but the upgrade button in my update manager no longer shows up!  Curses.  Here's my story:

Today, I popped open the update manager and noticed the little button allowing me to upgrade to Feisty.  Thinking it would be safest to upgrade everything else first -- especially since it was having authentication issues and errors -- I opened up synaptic and tried to fix my repositories.

I soon found that unchecking all my repositories in synaptic, reloading, checking them all again, and reloading again, produced a proper sources.list that didn't have the errors.  I proceeded to install all my updates.  The gnome update manager upgrade failed to download, so I tried that one once more after the rest of them were finished, and then restarted the computer to apply the kernel upgrade.

On restarting, update manager claims everything is up to date, and has no dist upgrade button anymore.  But my sources.list is all edgy stuff.  Wtf.

---

### Post by spin2cool on 2007-04-21
Try running: 
gksudo "update-manager -c -d"
to start the graphical install process

---

