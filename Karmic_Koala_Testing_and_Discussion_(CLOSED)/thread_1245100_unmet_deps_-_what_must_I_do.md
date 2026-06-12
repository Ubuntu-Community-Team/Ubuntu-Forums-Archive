---
title: "unmet deps - what must I do?"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-20
From time to time on upgrading I get these or those unmet deps. I see two alternatives:

1. Report new bugs to bother maintainers

2. Do nothing: maintainers do know all current issues (at this current testing phase), and my reports will just eat their time.

What is the right way?

---

### Post by slakkie on 2009-08-20
Report the bug, if the devs are not aware it will become an issue later on. So make them aware.

---

### Post by qamelian on 2009-08-20
It's also possible that waiting a day or two will correct the problem, as it may simply be that updated dependencies haven't been packaged yet.

---

### Post by ilna on 2009-08-20
Aha, the rule may be like this: at case the issue isn't a showstopper, just wait a couple of day for "autocureing" before reporting.

---

### Post by 23meg on 2009-08-20
> **ilna said:**
> Aha, the rule may be like this: at case the issue isn't a showstopper, just wait a couple of day for "autocureing" before reporting.

Especially in the early stages of the development cycle, such as before the [Debian import freeze]("https://wiki.ubuntu.com/DebianImportFreeze").

It's also a good idea to keep an eye on [the build queue]("https://launchpad.net/ubuntu/+builds") and the [Karmic-changes mailing list]("https://lists.ubuntu.com/archives/karmic-changes/") or [the equivalent RSS feed]("http://feeds.ubuntu-nl.org/KarmicChanges") to see if the missing dependency is on its way.

---

### Post by ilna on 2009-08-20
**23meg**,

Excellent, thanks! Probably RSS is the most handy.

---

