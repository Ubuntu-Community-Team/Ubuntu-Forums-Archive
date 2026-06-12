---
title: "Boot goes to disk check, hangs at 74%"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rallg on 2010-04-07
My dual-boot system has Lucid updates as of two days ago. Everything was OK. That is, there was no problem after the most recent updates on this computer.

Today, lucid does a disk check at boot. Everything looks normal, the way it would usually do when boot does a disk check. Graphics OK. But when the check gets to 74%, it hangs. This is repeatable.

Any advice? Presumably I can do something in recovery mode?

---

### Post by QLee on 2010-04-07
[QUOTE=Rallg]
Any advice? Presumably I can do something in recovery mode?[/QUOTE]

See if anything in this thread:
[http://ubuntuforums.org/showthread.php?t=1444879&highlight=disk+check&page=1](http://ubuntuforums.org/showthread.php?t=1444879&highlight=disk+check&page=1)

or on this launchpad bug:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/554079](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/554079)

can assist you with your problem or explain what you are seeing.

---

### Post by Rallg on 2010-04-07
Thanks, QLee. The problem was solved by using info in the first link you provided.

---

