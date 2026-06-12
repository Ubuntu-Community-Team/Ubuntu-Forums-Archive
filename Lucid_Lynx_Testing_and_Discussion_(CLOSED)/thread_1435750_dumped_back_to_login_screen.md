---
title: "dumped back to login screen"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vkimball on 2010-03-21
Three times now with Lucid Beta 1 AMD64 when waiting for a Firefox screen to display I've been dumped back to the Ubuntu login screen.

I'm not really sure how to begin troubleshooting or how to report the issue.

---

### Post by quixote on 2010-03-22
That's a symptom of the X Windowing system crashing, ie the GUI.  That could be either because your graphics isn't very well configured for your system, or it could be that you're visiting a site that has problems.  That can happen on some sites with flash implemented in a weird way.  If it always happens on the same site(s), then that's probably what it is.  You could try installing Adblock, Flashblock, or Noscript to block the flash or other scripts, and see if the problem stops.

---

### Post by vkimball on 2010-03-23
Thanks, I'll do some more digging on it.

(Didn't seem like it was happening just at particular sites though.)

---

### Post by jrothwell97 on 2010-03-23
I've also been getting this on i386 with both Nouveau and the proprietary drivers, but suspiciously it's only been occurring in Firefox. In Chromium and Midori, everything's fine and dandy.

---

