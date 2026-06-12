---
title: "Increase root.disk size?"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Champers on 2008-04-23
I just downloaded Ubuntu 8.04 last weekend, and I've been having fun learning about how to do things in it. I installed it in Windows, and not on its own real partition. I originally thought that I would only need about 5GB, because I thought that most programs could be run off my NTFS XP setup. Wine requires many programs to be installed on the root.disk in order to work. **I want to know if I can increase the size of the root.disk from 5GB to 20GB without reinstalling Ubuntu.** It took me days to get all of my drivers working (Wireless was a killer!) and I would rather not go through all of that again. If my only option is re-installation, is there any way to save what I have done (drivers/software) on this installation and put it into a new installation?


Answer bolded question if you can help.

---

### Post by Partyboi2 on 2008-04-23
Yes, you should be able to use gparted to resize the ubuntu partition. You can either download the gparted live cd
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
or boot the ubuntu live cd and when you are at the desktop open "Partition Editor" (System>Admin>Partition Editor) then use the resize feature.

---

