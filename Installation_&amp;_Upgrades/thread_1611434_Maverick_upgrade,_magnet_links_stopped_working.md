---
title: "Maverick upgrade, magnet links stopped working"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by odinb on 2010-11-01
Hi!

Magnet links worked just fine in Firefox in Lucid 10.04 with Transmission.

After update to Maverick 10.10, it no longer works. Nothing happens when I click a magnet link.

Have tried configuring Firefox to recognise magnet links (which I never did in Lucid, it just worked) following this post: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1416277](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1416277)

But it still does not work.

Any ideas?

---

### Post by lovinglinux on 2010-11-01
Try to create a new FF profile and see if it can recognize the magnet links. Also check [http://ubuntuforums.org/showthread.php?t=1273985](http://ubuntuforums.org/showthread.php?t=1273985)

---

### Post by odinb on 2010-11-03
Yup, after deleting my FF profile, it now asks, and I pointed to Transmission and set as default.

Working again. Thanks!

Annoying though that Firefox is this fragile! Have had similar problems before with Flash where I had to delete the profile to get flash working.

//Odin

---

### Post by lovinglinux on 2010-11-03
> **odinb said:**
> Yup, after deleting my FF profile, it now asks, and I pointed to Transmission and set as default.

Working again. Thanks!

Annoying though that Firefox is this fragile! Have had similar problems before with Flash where I had to delete the profile to get flash working.

//Odin

Profiles can get corrupted, but usually you can pinpoint the culprit inside it and avoid complete profile deletion.

I usually don't recommend deleting the profile. The idea was to make a test to see if if the problem was inside your personal settings or not. But sometimes is easier to just delete it and start over, if you have backups of important stuff.

See [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html).

BTW, this is an issue not exclusive to Firefox. I had to restore a Opera profile backup yesterday, because it became unusable after a crash after visiting OMG Ubuntu site.

Anyways, make regular backups.

---

### Post by r.anger on 2010-11-15
i had the same problem.

in my case the cause was, that transmission ist now called transmission-gtk

so to fix it, i had to rename the handler for magnet-links from /usr/bin/transmission to /usr/bin/transmission-gtk in preferences -> applications

---

### Post by Yleeyas on 2010-11-17
Thanx r.anger, renaming did the trick for me.

---

