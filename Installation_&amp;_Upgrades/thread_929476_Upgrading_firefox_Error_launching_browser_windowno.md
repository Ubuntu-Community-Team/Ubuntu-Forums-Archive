---
title: "Upgrading firefox: Error launching browser window:no XBL binding for browser"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by sean4u on 2008-09-25
Upgraded firefox from the 'Updates available' prompt today and got a dialogue on restarting firefox that said:

> Error launching browser window:no XBL binding for browser

I had epiphany (among others!) installed, so I searched and found an old thread here that suggested reinstalling firefox. Other forums suggested deleting firefox's settings (WTF?!). Yet others suggested '--safe-mode' and removing extensions.

I had a sneaking suspicion nothing was that badly wrong, so I opened an xterm and had a look to see if firefox was still running in any way:
```

ps -ef | grep firefox

```
There was a process still running so I kill'd it, and starting firefox in the usual way JustWorked(TM). Thought I'd better post before anybody starts taking a sledgehammer to their nuts.

---

### Post by LlamaCaeruleus on 2008-09-26
Thanks a lot. Had the same problem. Without your post i probably would have done a lot more damage...

---

### Post by actan on 2009-06-19
Thanks!
Thank you ..
Thanks Google help me find your post ..

:p

---

