---
title: "[xubuntu] X not starting automatically on 16.04"
date: 2016-04-26
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2016-04-26
I've just updated to 16.04 and no longer have a graphical login screen. Instead I get a full-screen console login and I have to log in and then run startx. (using Xubuntu)

I also don't seem to have the option of skipping the disk check on startup with Ctrl-C and as it does it every time, rebooting is a real pain now with the ten minute wait and manually starting the GUI.

Has anyone a fix/workaround for either issue?

---

### Post by pickarooney on 2016-04-26
Might be related to this:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1369216](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1369216)

I have the same errors when trying to run lightdm. I tried switching to gdm but get the same behaviour

---

### Post by pickarooney on 2016-04-26
Apparently ssdm is failing to start. How do I fix that, then?

---

### Post by pickarooney on 2016-04-26
Well, after trying them all, SLIM manager is the only one that will run.

For the disk check, editing fstab and changing the last column to 0 seems to work, even if it's not advisable

---

### Post by navarro2 on 2016-04-27
Why would they release an LTS with such a glaring problem?

---

### Post by pickarooney on 2016-04-27
Probably the silly time constraints they impose on themselves
Last time they broke the suspend option
The time before that they broke the splashscreen
There's invariably some new audio problem with each release
Time to boot has gone from 30 seconds to about 3 minutes in a year...

---

