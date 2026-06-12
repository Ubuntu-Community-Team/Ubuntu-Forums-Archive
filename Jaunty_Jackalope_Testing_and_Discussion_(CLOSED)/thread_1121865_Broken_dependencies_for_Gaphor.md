---
title: "Broken dependencies for Gaphor"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nkteam on 2009-04-10
I'm using Ubuntu 9.04 beta.

When I tried to start gaphor, I get:

```
Traceback (most recent call last):
  File "/usr/bin/gaphor", line 5, in ?
    from pkg_resources import load_entry_point
ImportError: No module named pkg_resources

```

This bug (broken python dependencies) is reported on:
[https://bugs.launchpad.net/ubuntu/+source/gaphor/+bug/30344](https://bugs.launchpad.net/ubuntu/+source/gaphor/+bug/30344)

and fix is supposed to be released long time ago, but it's still there in Ubuntu 9.04.

How to correct this?

---

