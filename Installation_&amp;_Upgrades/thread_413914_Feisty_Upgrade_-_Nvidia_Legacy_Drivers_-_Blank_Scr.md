---
title: "Feisty Upgrade - Nvidia Legacy Drivers - Blank Screen"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by cgray on 2007-04-19
I had a slight hitch in the upgrade today which I have fixed. On the initial boot the usplash was running fine, then the Nvidia splash ran - which is looking quite good now, as I have not upgraded for a while. Then gdm would start running, hear the ubuntu sound however I could not see anything. I could log in, but I would only hear the gnome startup noise - again blank screen.

A solution I found was to add the following to my Device section on the xorg.conf

Option "UseDisplayDevice" "DFP"

I found this solution here 

[http://www.nvnews.net/vbulletin/showthread.php?t=88951](http://www.nvnews.net/vbulletin/showthread.php?t=88951)

Restarted X and all was well. I since have used the Nvidia settings tool/Gui to change items and it is still fine.

Thought I would give people a heads up.

I have a GeForce4 440 Go on a Dell Inspirion 8200 plus use nvidia driver 1.0-9631

---

