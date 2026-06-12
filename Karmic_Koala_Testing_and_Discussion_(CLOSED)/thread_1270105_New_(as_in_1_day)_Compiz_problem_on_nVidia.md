---
title: "New (as in 1 day) Compiz problem on nVidia"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by forumache on 2009-09-19
Could you please check:

1 - when you see your desktop (no other windows open)
2 - press on Clock/Date/Weather applet
3 - Calendar will appear
4 - click again on Clock/Date/Weather applet
5 - Calendar will disappear
6 - A SHADOW WILL REMAIN => BUG!

Remember, you have to see it on an empy desktop, so minimize Firefox before trying ;)

If you confirm, I'll rise a bug. If one is already open and you know about it, please respond with its number.

This is the latest Compiz, since yesterday and the changelog is:
compiz (1:0.8.3+git20090917-0ubuntu1) karmic; urgency=low

  * New git snapshot of the 0.8 stable branch:
    - fix assert failure when core is loaded twice
  * debian/patches/029_default_options:
    - revert 'set Unredirect Fullscreen windows to "false"' change, 
      it causes problems on nvidia system
  
 -- Michael Vogt <michael.vogt@ubuntu.com>  Thu, 17 Sep 2009 18:12:02 +0200

Many thanks.

---

### Post by steeleyuk on 2009-09-19
I can confirm.

Just add, that it does not happen using Metacity compositing, so definitely a compiz issue.

---

### Post by alexmurray on 2009-09-19
Yep I've been seeing this for a while (since when I installed Alpha 4) so should definitely file a bug - is it this bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/152264](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/152264) ? Although I never noticed this in Jaunty so perhaps is something new.

---

### Post by GeorgeVita on 2009-09-19
Same problem exists on EeePC 1000H, Ubuntu 9.10 fully updated.

---

### Post by patasenko on 2009-09-19
Yup same here, goes away, when application is run. With intel graphics.

---

### Post by cyberkilla on 2009-09-19
I can confirm this too, but I've been experiencing the issue for more than one day:)

---

### Post by barisurum on 2009-09-19
I confirm the issue with an ATI X1950XT with open source radeon driver. Please post the adress of the bug report you rise so I can add this ati info.

---

### Post by forumache on 2009-09-19
Somebody was faster than me. It seems that the problem is at least 6 days old, I noticed it only yesterday.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/428783](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/428783)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/427921](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/427921)

It seems to me that they are about the same thing, one of them will be marked as duplicate of the other.

Please subscribe to the bugs in order to show developers that you are affected too.

Thanks everyone for confirming this bug!

---

### Post by orlox on 2009-09-19
Also can confirm it. Although this bug is old (as in at least three weeks) for me.
I thought on filing a bug, but I use the calendar applet so little that I forgot about it.

---

### Post by Darkshade on 2009-09-19
It's been like this since alpha 1 on my machine.

---

