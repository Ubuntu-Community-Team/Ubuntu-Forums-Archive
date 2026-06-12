---
title: "[SOLVED] touchpad issues"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caro on 2008-10-23
Upgraded my Dell Inspiron 1505 to Intrepid yesterday.  No real problems so far but my touchpad settings have returned to default.  System > Preferences > Touchpad won't run, so I'm at a loss to change them - particularly turning off the "tap to click" feature which I hate.  Anyone know how to fix this or if it will be fixed in the final release?

---

### Post by jbg7474 on 2008-10-23
I'm having the same problem on a Dell D620--I also upgraded from hardy last night.

---

### Post by derrick81787 on 2008-10-24
> **caro said:**
> Upgraded my Dell Inspiron 1505 to Intrepid yesterday.  No real problems so far but my touchpad settings have returned to default.  System > Preferences > Touchpad won't run, so I'm at a loss to change them - particularly turning off the "tap to click" feature which I hate.  Anyone know how to fix this or if it will be fixed in the final release?

I don't know why your touchpad preferences won't open, but I've disabled tapping on my Dell another way.  Basically, you can run xinput at login to do it.

Here's the thread about the issue, and I have a post saying how I solved it.
[http://ubuntuforums.org/showthread.php?t=949976](http://ubuntuforums.org/showthread.php?t=949976)

---

### Post by wgrant on 2008-10-24
As the release notes say, InputDevice sections in xorg.conf are now largely ignored. Tap-to-click and scrolling can be easily turned off in System->Preferences->Mouse->Touchpad, and you can get System->Preferences->Touchpad working again by following [these instructions](https://help.ubuntu.com/community/SynapticsTouchpad#Ubuntu%208.10%20and%20later).

---

### Post by caro on 2008-10-24
Thanks wgrant.  I'll give it a try when I get home tonight.  I knew there had to be an easy way to fix that.

---

