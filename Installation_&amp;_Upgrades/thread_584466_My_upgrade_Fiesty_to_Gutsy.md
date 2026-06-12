---
title: "My upgrade: Fiesty to Gutsy"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by wmcbrine on 2007-10-21
Yesterday, I upgraded from 7.04 to 7.10. It was my smoothest Ubuntu upgrade yet... but still a mess.

First, it couldn't find my /home partition, although everything appeared correct (and unchanged from the working Fiesty configuration) in /etc/fstab, etc. Every few seconds, I'd get an error message on the console: "device-mapper: table: 254:3: linear: dm-linear: Device lookup failed". Eventually I found the answer here: remove the evms package. That got my /home back.

Next, I found that Firefox was missing all its plugins, except for Totem. After much poking around, I figured out that the plugin directory had been changed to /usr/lib/firefox/plugins, with no links made to the old plugins (in /usr/lib/mozilla/plugins... also /usr/lib/mozilla-firefox/plugins). I haven't been able to find a thread about that here yet, although there must be. (?) If not, I hope this message helps someone.

Other than that, it's pretty nice so far. But I'm having a hard time getting used to the subpixel rendering, even though I always use ClearType in Windows. If I could tweak it to be somehow sharper, that would be good. I'd also consider returning to my old settings, if I could figure out what they were. :confused: I tried "Best Contrast", but I'm not sure that's quite right, either.

Edit: Oh, I guess I should've posted this in the sticky.

---

### Post by hugmenot on 2007-10-22
If you want &#8220;sharper&#8221;, look [here]("http://ubuntuforums.org/showthread.php?t=555964")

Glad to help, de gustibus non est disputandum.

---

### Post by hugmenot on 2007-10-22
To be more specific: [here]("http://ubuntuforums.org/showpost.php?p=3483916&postcount=63")

---

