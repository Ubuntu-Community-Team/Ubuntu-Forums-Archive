---
title: "Software Updater - No network connection detected"
date: 2019-04-16
forum: Installation &amp; Upgrades
---

### Post by Newbunto on 2019-04-16
I've just upgraded from 16.04 to 18.04 (specifically 18.04.2). Since then use of Software Updater gives the following messages.
[INDENT](for the Technical description)
**No network connection detected, you can not download changelog information.**

(towards the bottom of the window)
**You may not be able to check for updates or download new updates.**
(and to the left of that text there is an icon that looks like a 'no network' icon)
[/INDENT]

I definitely have a working network connection. I am posting from the offending computer!

It looks to me that something runs at startup before the network is up and remembers that the network was not up at that time and then won't forget that.

If that is correct, how do I persuade Software Updater that the network is up? It runs automatically at startup but re-running it manually does not get different results. How is Software Updater "detecting" whether I have a network connection? It seems as if it is trying to be helpful but in this case getting itself more confused than is necessary.

(My network connection - wired ethernet - does seem to take an inordinate amount of time to be recognised. The icon in the "system menu" at the top right of the screen does not show a happy network until several minutes after booting. That is a problem for another day. The actual internet is permanently fine. The problem is just getting the wired ethernet to be recognised as 'connected'. However even once it is connected and definitely all working, I have the above problem.)

---

### Post by cruzer001 on 2019-04-17
Try a terminal update and see if it gives any additional information.
```
sudo apt update
```

---

### Post by Newbunto on 2019-04-17
[FONT=courier new]apt update[/FONT]

and

[FONT=courier new]apt upgrade[/FONT]

both work fine. Lots of downloading. **No** errors.

Functionally, the problem is that I don't get changelog information. Cosmetically, the problem is that it is giving misleading and incorrect messages.

---

### Post by cruzer001 on 2019-04-18
Try reinstalling both update-manager and update-manager-core.  Use the purge command to remove configuration files.
```
sudo apt purge update-manager update-manager-core && sudo apt install update-manager
```

---

### Post by Newbunto on 2019-04-22
The last few boots this problem seems to have gone away but there was an update to the Software Updater itself, I think. Might have to leave it unless the problem comes back.

---

### Post by cruzer001 on 2019-04-22
Sounds good :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by mikegee81 on 2019-12-05
purge and re-install fixed it for me. Thanks.

---

