---
title: "update has broken ubuntu 14.04"
date: 2015-10-07
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2015-10-07
I have just update ubuntu 14.04 since that the computer hangs on ubuntu start screen.

---

### Post by jaezcurra on 2015-10-07
Same thing happens with 15.04.
I had to start from GRUB with the previous release of the OS...

---

### Post by pauljw on 2015-10-07
Same here on my Sys76 Gazelle Pro.

---

### Post by dbeltrami on 2015-10-07
Upgrade on my 15.04 has also caused serious issues on login.

---

### Post by echotech2 on 2015-10-07
Same here (Ubuntu 15.04) - Applied today's updates which included a kernel(?) update - Restarted - Got to login screen - Logged in normally with my chosen background displayed - No Launcher or Top Bar displayed - Mouse moved normally for about 5-10 seconds then became jerky and froze after a couple of seconds - Rebooted several times - Still the same problem - Rebooted and selected previous kernel and it works.

---

### Post by grahammechanical on 2015-10-07
What is the purpose of this thread? Is it to create a list of people with the same or a similar problem?

One person has 14.04. Others have 15.04. One person does not get to the login screen. Others get past the login screen but with only the background wallpaper and without the user interface (Unity). How is this the same problem? Perhaps it is and echotech2 has come up with the answer for everyone.

Restart. Select Advanced Options for Ubuntu and select an earlier (working) kernel. If that temporarily solves the problem for everyone, that is good. But I, for one, will not attempt to help more than one person at a time. I gets very confusing trying to help more than one person in the same thread. So, hoboy, if selecting an earlier kernel does not work, please report back. For the others if selecting an earlier kernel does not work then start a new thread under your own name.

Thank you.

Oh, by the way, 2 days ago my system loaded to the wallpaper without the user interface. The partiton was very low on space. I opened a terminal and removed one very large file and then restarted and the OS loaded to a working desktop.

---

### Post by madtom1999 on 2015-10-07
I've got the same with Lubuntu 14.04. The new kernel (66) seems to be a bit flakey.
Running the last one before the update seems to work OK.

---

### Post by pauljw on 2015-10-07
Looks like the fix has been committed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1503655)

---

