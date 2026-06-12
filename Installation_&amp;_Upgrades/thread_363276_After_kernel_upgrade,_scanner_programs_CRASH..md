---
title: "After kernel upgrade, scanner programs CRASH."
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by myke on 2007-02-16
I have a canon LiDE60 scanner that I've been using since breezy up to edgy with little problems.  After the latest normal upgrade for the linux kernel that the adept notifier suggested, my scanner programs will no longer launch.  None.  I've used both Kooka and Xsane and neither will launch.  If my scanner is plugged in, it will be detected, then the programs immediately crash.   If it's not, they just will not  start at all.   I installed another package from the repositories for scanners, "quiteinsane", and it does the eXACT same thing.  Will not launch.  Neither adept nor synaptic show any broken package problems yet neither program will launch at all.

Please some suggestions.  I use the scanner quite alot when I work from home partially during the week and I've had to restart in the damned WinXP partition just to use the scanner which I've not had to do in months!  

Keep me from launching XP!  What will make Kooka or Xsane work again????

---

### Post by myke on 2007-02-16
For some reason ... & I don't know why ... after the kernel upgrade, it apprantly affected a setting with my Samsung printer which in turn affected the scanner software even though the printer never stopped working.   After poking around the forums a while, I found this thread:

[http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697]("http://www.ubuntuforums.org/showthread.php?p=2167697#post2167697")

I used the chmod solution and commenting out one line in a root file and now both kooka & xsane are working again.

Specifically, this is what was suggested and what fixed my problem & hey ... I don't know what the kernel upgrade had to do with it but I'm just glad the solution turned out to be relatively simple:

you'll find xsane now executes as root. (This is also true if you have a multifunction printer, but see below instead of this step.) To fix this, since you don't want to run xsane as root, do the following:
a: in a terminal, type "sudo chmod -s /usr/bin/xsane"
b: sudo edit /etc/sane.d/dll.conf, and comment out (add a "#") in front of the line that says "smfp" (probably the last line).
If you only do (a) and not (b), xsane will crash.

Good luck, and let me know if you have success and/or failure, and I'll try to modify accordingly.

---

