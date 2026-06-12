---
title: "the switch to g++-4.2 in 8.04 was a dumb idea"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by s|k on 2008-03-31
All string constants can no longer be implicitly cast to char *, which means thousands of lines of warnings and with -Werror set, that's a lot of errors to fix on our source code.

I don't know where I'm supposed to bitch about this, I remember there use to be beta forums. But anyways. The first thing I did after seeing this mess was install g++-4.1 and symlinking to it.

---

