---
title: "Increased overall memory consumtion"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yurx cherio on 2010-03-28
Beta feels solid. I had less hiccups then /w Jaunty final release.

One thing bugs me though. I noticed that for some reason the same set up on the same computer eats more memory then Karmic. In fact my new install runs less services on start-up then Karmic while taking 200K more. Not a huge loss on a 4Gb machine but unpleasant. I am suspecting that it may be additions to libc that inflate each program in memory.

Has anyone else experienced the same "effect"? Not that it will hold me from switching to Lucid but this behavior is a bit disappointing. :icon_frown:

---

### Post by Longinus00 on 2010-03-28
See if it goes away on reboot, ureadahead currently has a giant memory hole
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by yurx cherio on 2010-03-28
It is consistent so far every time I reboot. Consistently and measurably higher then I am used to in Karmic. My 64-bit Karmic also runs a few more services including PostgreSQL & Infobright DB servers and it takes 200K less then Lucid after reboot.

I do have ureadahead installed. Would you recommend to uninstall it for now?

---

### Post by Rob2687 on 2010-03-28
200K as in 200 Kilobytes?

---

### Post by yurx cherio on 2010-03-28
I know, ridiculous right? :D 200KB would be negligible.
My mistake, the difference is ~200MB.

Another curious thing is that memory reported by free is not the same as total consumed by all programs "ps -A -orss".
Available memory reported by free (used - cached) is >1200MB while the total of "ps -A -orss" is ~700MB.

---

