---
title: "PREEMPT #1 in /etc/motd ???"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by Paul Bramscher on 2006-06-09
I did a clean install to Dapper Drake 6.06 last night and everything went pretty well.  But I noticed that the /etc/motd message (and "uname -a" command) produces this:

Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

What's the "#1 PREEMPT"?  Did the US mirror I downloaded the ISO from mistakenly provide me with a release candidate instead of the final release?  Or am I ok?  Is there any way to verify?  Thanks.

-Paul Bramscher

---

### Post by glotz on 2006-06-09
I've got that too. No clue. Not the US mirror.

---

### Post by jobezone on 2006-06-09
I think PREEMP means [this]("http://en.wikipedia.org/wiki/Preemption_%28computing%29"). Perhaps ubuntu's kernel has this feature enabled/patched in.

---

