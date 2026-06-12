---
title: "Lucid-&quot;Preload&quot; is it OK in Lucid?"
date: 2010-02-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-12
"Preload is an adaptive readahead daemon. It monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times."

[http://sourceforge.net/projects/preload/](http://sourceforge.net/projects/preload/)

---

### Post by psyke83 on 2010-02-12
That's been available in the repositories for quite some time. I've used it in the past, but noticed no significant difference in application load time.

There was also another project that was supposed to be superior, but it seems to have fizzled out.

[http://code.google.com/p/prefetch/](http://code.google.com/p/prefetch/)
[https://wiki.ubuntu.com/DesktopTeam/Specs/Prefetch](https://wiki.ubuntu.com/DesktopTeam/Specs/Prefetch)

P.S. I filed this bug some time ago: [https://bugs.launchpad.net/ubuntu/+source/preload/+bug/96583](https://bugs.launchpad.net/ubuntu/+source/preload/+bug/96583)

Even though Karmic/Lucid now use ureadahead instead of readahead, there may be a similar conflict with preload that may increase boot time.

---

