---
title: "After uninstalling libparted0debian1, problem loading GUI"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by pmcevoy on 2010-10-25
Hi there. I'm using Ubuntu 10.04 (installed) but writing this using a live cd since my distro is currently fracked.

So I was attempting to install gparted to repartition my hard drive, and it told me that it needed a different version of libparted0debian1. So I tried updating libparted0debian1, but that didn't do anything. I figured maybe gparted depended on an older version of libparted0debian1, so I uninstalled said package (and the packages depending on it- there were two, which I cannot recall the names of- I assume now that they were important) thinking I would then install the older version.

I was doing all of this through the software center. Halfway through removing the software, my music stopped playing, the screen went blank and the computer turned off. I reset the computer and the splash screen never came up. It game me the option (as a graphic window) to load ubuntu with basic graphics or reset. I chose basic graphics, and it gave me a command line. I tried "sudo apt-get install libparted0debian1" and it asked me to do "sudo dpkg --configure -a", which I did. The apt-get for libparted0debian1 then updated a few packages.

After restarting this time the ubuntu loading screen showed up (pretty purple background, UBUNTU text, and 5 animated dots) but nothing ever came of it. I pressed escape which showed me some text that ended with "testing battery levels" or something like that.

Anyway, I'm not super worried- I'm pretty sure I just deleted something that allows ubuntu to read the filesystem. Can anybody tell me what packages I may have deleted that could be causing this problem?

Thanks :)

---

