---
title: "LTSP 10.04.1 client text on gnome is backward"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by filibertov on 2010-11-18
I have just installed LTSP from the Ubuntu 10.04.1 alternate CD with several minor problems which were resolved quickly.  I was able to login with my first client PC.  The problem started when the PC went to Screensaver mode.  After entering the password, all the text in gome is upside down, flipped,...backwards.  Cannot correct it after reboot.  I'm attaching a screenshot.  Can anyone help me figure out how to fix this?

---

### Post by filibertov on 2010-11-19
I just booted from a different computer and the screen for the same user is also backward.  It looks the same as the screenshot I provided.  Any ideas?

---

### Post by rppein on 2010-11-22
Same problem here after an update, restart and logging in. The screen layout is more or less normal, but all visual content is flipped overhead. At the same time, the interactive components (e.g. buttons) have their active area in the correct position, making it quite difficult to hit. The window titles appear readable on the right edge. Further, a moving window is very slowly updated.

Graphics card:
Nvidia GeForce G 210M

Graphics Driver:
Default (proprietary Nvidia driver always ended up with black screen)

System:
Ubuntu 10.4.1 LTS

---

### Post by rppein on 2010-11-22
It seems to be somehow caused by the Nvidia driver (see link to bug report). Logging in with the "gnome-failsafe" option fixed the screen for the moment. I'll try the suggested cleaning up of nvidia packages later. Sadly, their 3D drivers only caused problems for me so far.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/542813](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/542813)

-----
[ullix]("https://launchpad.net/%7Eullix")             wrote             on 2010-03-22:                                                             [ #5]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/542813/comments/5")                                                        oddly enough, debb1046's suggestion did work! Thanks.
 I did the following: logged in to failsafe-gnome, with wired connection. Command:
lsmod | grep -i nv
did not give any output.
Under Synaptic I uninstalled all packages (about 7) with names beginning with "nvidia-". Logged out and logged in to Gnome.
 Desktop is correct!

---

### Post by filibertov on 2010-11-22
Yep, removing the nvidia driver from the LTSP server did the trick.  I now see "straight" on my clients.

---

