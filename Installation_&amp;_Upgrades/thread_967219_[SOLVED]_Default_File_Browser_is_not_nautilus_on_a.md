---
title: "[SOLVED] Default File Browser is not nautilus on a fresh install."
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Bunnykun on 2008-11-01
Hello all.  I just now completed upgrading to Intrepid Ibex, and I opted to do a fresh install while preserving my home directory.  The install is complete, and the only thing I've done is launch Firefox and activate the propriety broadcom drivers...so I haven't messed with any configuration settings.  

However...

When I attempt to browser folders from Places, the folder is opened in "Eye of Gnome" instead of Nautilus.  Eye of Gnome will then show me whatever images are in that folder.

I am able to launch nautilus from terminal.  Also, if I try to open a folder from the places menu within nautilus, it opens the folder in nautilus.

It seems that just the Places in my panel has this problem at the moment...and only for the folder links.  The links to the drives open in nautilus.

I'm flummoxed.  I've never used eye of gnome before... Any ideas?



edit: it occurred to me that my thread subject isn't entirely accurate.. Should be "Places launches folder with application other than Nautilus" I suppose.. My apologies.

---

### Post by Bunnykun on 2008-11-01
update: searching for eog (eye of gnome) in gconf-editor didn't yeild anything that looked like would effect this.

---

### Post by Bunnykun on 2008-11-01
I got it now.  Found this post.. [http://ubuntuforums.org/showthread.php?t=884000](http://ubuntuforums.org/showthread.php?t=884000)

Just open properties for a folder and set the open with back to "open folder."  weird.

---

