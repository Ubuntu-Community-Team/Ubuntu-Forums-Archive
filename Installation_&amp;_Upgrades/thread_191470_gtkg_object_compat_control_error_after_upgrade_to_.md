---
title: "gtk/g_object_compat_control error after upgrade to dapper"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by dkuhlman on 2006-06-07
I am running Kubuntu.  I upgraded from breezy to dapper.  After doing so, I get the following error messages when I run gtk applications:

~ [1] gedit
gedit: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_object_compat_control
~ [2] evince
evince: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_object_compat_control

I've done searches and I have tried a number of things, but none of them fix this problem.

Does anyone have a suggestion?

I've attached some notes on some of the things that I have tried, just in case they offer a clue.

Thanks for help.

Dave

---

### Post by dkuhlman on 2006-06-07
Answering my own questions ...

I found that my problem was that, some time ago, I had built gtk+ from source.  So, I had gtk+ libraries, built from out-of-date source, in /usr/local/lib.    I have now removed those old libraries.  Now, my system is picking up the up-to-date Ubuntu libraries from /usr/lib, I believe.  And now gtk applications like gedit, evince, epiphany, etc. are working.

So, my lesson for today, if you build libraries from source, you either need to keep them up-to-date, or remove them.

Oh, and kubuntu/dapper is running great now.

Dave

---

