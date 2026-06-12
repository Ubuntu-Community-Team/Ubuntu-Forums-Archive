---
title: "Solved Lucid Mounting Problem"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by arak on 2010-05-05
In upgraded from 8.04 and had some mounting problems.  I Had a problem which said /proc/bus/usb  and then I had problem with mounting ha1, hda1, and hda2.  

Based upon help from this site I loaded /etc/fstab and put an # before the last item which had /proc/bus/usb and I solved the first problem.

Then I checked in /media  and saw that ha1, hda1, and hda2 were empty.  Following the line of reasoning above I put # in front of the ha1, hda1, and hda2 lines.  

This solved my problems.

I run a dual boot--10.04 and XP--and I run Virtualbox with XP inside of Linux.  Everything works.

I really don't know much about Linux and hope I really solved the problems.

---

