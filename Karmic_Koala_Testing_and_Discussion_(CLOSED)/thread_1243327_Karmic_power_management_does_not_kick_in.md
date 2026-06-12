---
title: "Karmic power management does not kick in"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Paqman on 2009-08-18
I've had this bug since installing Karmic a couple of weeks ago, but haven't really had time to look into it much.

Bottom line: I set my machine to sleep after 10 mins, but Karmic isn't playing the game. I'm wondering if this is related to the bug some folks have that is causing the [screensaver to not start]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/397892")? Suspend works fine when I tell it to explicitly. 

Related to HAL deprecation maybe? Thoughts?

---

### Post by chronosMark on 2009-08-18
I think you might be experiencing the same issue as me I found that killing the gnome-power-manager process and then restarting it fixes this issue (at least till the next reboot).

[http://ubuntuforums.org/showthread.php?t=1242019](http://ubuntuforums.org/showthread.php?t=1242019)

---

### Post by wnelson on 2009-08-18
That works for me. I noticed some hal-runner and related is loaded after gnome-power-management is reloaded.

Thanks for the info..

---

### Post by thund3rman on 2009-08-18
Maybe you came across this bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/411350](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/411350)

Still don't know how to solve it but I will try your "workaround" to see if it works on my box as well...

---

