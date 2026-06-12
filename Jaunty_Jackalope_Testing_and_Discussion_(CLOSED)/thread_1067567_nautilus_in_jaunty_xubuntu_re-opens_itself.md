---
title: "nautilus in jaunty xubuntu re-opens itself"
date: 2009-02-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ugkbunb on 2009-02-12
I am using Xubuntu Jaunty with up to date packages as of 02.11.09. I enjoy nautilus and Thunar so I installed nautilus via apt-get on my xubuntu desktop. I am able to open and use it just fine (I run it using the --no-desktop command). The bug happens when I attempt to close out of nautilus. It re-opens itself. I always have to close it 6 six times before it quits re-opening itself. This number never changes... and the speed of closing it does not matter. (I.e. I can close it 3 times... wait 5 min... close it 3 more times or just closely sequentially).

Output of terminal:
$blah@blah-desktop:~$ nautilus --no-desktop
$Initializing nautilus-share extension
$** (nautilus:22180): WARNING **: Unable to add monitor: Not supported
$** (nautilus:22180): WARNING **: Unable to add monitor: Not supported
$Shutting down nautilus-share extension
$--- Hash table keys for warning below:
$--> file:///home/geota
$(nautilus:22180): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys $above)
$(nautilus:22180): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time

rapidshare attacment of recordmydesktop of the bug in action:
[http://rapidshare.com/files/197074067/nautbug.ogv.html](http://rapidshare.com/files/197074067/nautbug.ogv.html)

bug i filed on LP:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/328380](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/328380)

---

