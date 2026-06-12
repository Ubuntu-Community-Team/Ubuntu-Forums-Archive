---
title: "Partial upgrade - Broke some things."
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2008-08-18
Last night, Ubuntu notified me that it had upgrades (as it always does), so I let it download and install them.

I got a dialog advising me it was doing a "Partial Upgrade", I didn't pay much attention to it, and allowed it. I mean, the package maintainers know what they are doing.

Afterwards, I can only get .wmv files to play in VLC where previously they played in ALL my media players. Is there a simple fix for this?

Also, just found this by looking at the kaffeine debug messages, it was missing a codec, ffmpeg..

apt-get install libxine1-ffmpeg gives me:

libxine1-ffmpeg: Depends: libxine1-bin (= 1.1.11.1-1ubuntu3) but 1.1.11.1-1ubuntu3.1 is to be installed

Any help here?

---

### Post by Partyboi2 on 2008-08-18
Have you tried forcing the earlier version of libxine1-bin? Open up synaptic package manager and do a search for libxine1-bin then highlight it and select "package" then "Force Version" then select the 1.1.11.1-1ubuntu3 version.

---

### Post by Milambar on 2008-08-22
LOL, I did that... And it wanted to remove:
kaffiene
kde
gnome-desktop
mozilla
..
..
etc

So I aborted it. I guess Im going to be stuck with broken media-players until the maintainers resolve this dependency.



-UPDATE- I found the solution here: 
[http://ubuntuforums.org/showthread.php?p=5642968#post5642968](http://ubuntuforums.org/showthread.php?p=5642968#post5642968)

Ironic that google found that for me, when ubuntuforums own search function didn't. :)

---

