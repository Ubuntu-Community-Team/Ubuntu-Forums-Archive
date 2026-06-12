---
title: "Dapper from fresh install"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by katiad on 2006-06-05
Currently running a rather buggy, crashy Breezy install, and would naturally like to upgrade to Dapper. I've done a lot of configuration, program installation, etc. to Breezy, but I suspect with the problems I have (lots of random crashing/freezing, gnome no longer loading, amarok refusing to load even on a fresh reinstall of it...) I had perhaps better just do a fresh install of dapper.

However, I've never done this and left my /home partition intact, which is a must this time, since I've migrated over from the XP computer pretty much entirely. Anything in specific I need to know about doing a fresh install and leaving the /home partition alone? I'd be using the same usernames, but will this cause conflicts with settings or anything?

Thanks.

---

### Post by aysiu on 2006-06-05
The whole point of having a separate /home partition it preserves your settings.

When you get to this point in the installation process (after you selected "manually edit the partition table"), make sure you choose /home as the mount point for your home partition and uncheck (or untick, if you're British) the box that says "reformat."

In this example, I chose /documents as the mount point for my documents partition, but the same principle applies for /home.

---

### Post by katiad on 2006-06-05
That's what I thought. *sigh of relief* Just thought I'd make so there would be no obvious conflicts before I actually went and did it. Would really not make my day if I'd gone and obliviously done something to screw myself over. *laugh* Thanks for the quick response.

---

