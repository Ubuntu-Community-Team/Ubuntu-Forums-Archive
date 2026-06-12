---
title: "memory usage up in Karmic -- why?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by Ben Branch on 2010-01-09
On 9.04, when the system is booted and I log in, but before any apps are
started (such as firefox or thunderbird), the various memory monitors (gkrellm, top, system monitor) agreed that I was using 18% of my RAM.
After upgrading to 9.10, it's up to 24%. I've been able to turn off a few daemons (such as bluetooth) but to no material effect. This is not a critical issue but I'm disappointed at the jump ... any ideas why this has happened, and is there anything I can do to tune it/make it better?

Thanks,
Ben

---

### Post by mikewhatever on 2010-01-10
Look under Startup Programs, there quite a few entries that can be safely disabled.

---

### Post by Ben Branch on 2010-01-10
OMCB (One More Cold Boot) and the problem seems to have gone away!!

---

