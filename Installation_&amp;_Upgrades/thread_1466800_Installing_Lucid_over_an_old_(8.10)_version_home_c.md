---
title: "Installing Lucid over an old (8.10) version: /home conflicts"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by G_u_s on 2010-04-30
Hi all,

I'm installing Lucid over 8.10. I had a separate /home partition which contains data I cannot move (I don't have extra devices). It also contains data that, I believe, might cause errors, since they are old gnome configuration files, among other things.

Is this really an issue? If so, how can i solve it, i.e., keep my data but force ubuntu/gnome to write over the configuration files?

Thank you for your help!

EDIT: for instance, i get the following errors when logging in:

"The panel encountered a problem while loading "OAFIID:Deskbar_Applet".
Do you want to delete the applet from your configuration?
(Don't Delete - Delete)

The same happens with OAFIID:GNOME_NetstatusApplet

And indeed, I cannot see the Network Manager's icon to the top-right of my screen.

---

### Post by itang sanjana on 2010-04-30
A bug in migration-assistant prevents some users with separate home partitions from completing the install successfully. Users who experience such a crash can disable migration-assistant by selecting "Try Ubuntu" at the first screen of the installer, then pressing Alt-F2 and typing ubiquity --no-migration-assistant at the prompt that appears. see: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/536673](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/536673)

HTH

---

### Post by G_u_s on 2010-05-01
I'm not sure I got what you meant. It didn't seem to match with my situation and problem, sorry. Thank you for trying, anyway =)

---

### Post by G_u_s on 2010-05-01
After trying a few reinstallations of the incriminated applets, it seems to work now. I don't really know why, so I won't tag the thread as Solved, unless an admin thinks otherwise, of course =)

---

