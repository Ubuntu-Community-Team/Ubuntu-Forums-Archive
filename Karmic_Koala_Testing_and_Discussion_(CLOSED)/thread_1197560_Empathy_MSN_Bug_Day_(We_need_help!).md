---
title: "Empathy MSN Bug Day (We need help!)"
date: 2009-06-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by castrojo on 2009-06-26
Ok everyone, those of you on MSN have no doubt complained about the state of MSN Support in Empathy. Empathy depends on something called telepathy-butterfly for it's MSN Support. Not many of us have MSN accounts so we need bugs reported, bugs triaged, and general "kick the tires" of the thing for us to be able to help upstream figure out the problems.

Normally we announce these much earlier but we wanted to squeeze one in before GUADEC.

Here is the triaging info: [https://wiki.ubuntu.com/UbuntuBugDay/20090630](https://wiki.ubuntu.com/UbuntuBugDay/20090630)
Announcement: [https://lists.ubuntu.com/archives/ubuntu-bugsquad/2009-June/001502.html](https://lists.ubuntu.com/archives/ubuntu-bugsquad/2009-June/001502.html)

You should be using the Telepathy in Karmic or the Telepathy PPA if you're on Jaunty: [https://launchpad.net/~telepathy/+archive/ppa](https://launchpad.net/~telepathy/+archive/ppa)

Feel feel to leave comments, ask questions, but most importantly, report bugs!

---

### Post by andrewabc on 2009-06-26
I think I'm going to test it on jaunty, as I am guessing http msn will not work. It didn't back in early 2009 when I was looking for a chat client to connect to http msn (pidgin didn't work until jaunty release).

installed PPA empathy, and of course it won't connect. There doesn't appear to be any http connection mode possible!? I imported my pigdin account (which connects)

How is this going to be default IM when there is no http connection possible?

EDIT, found the bug:
[add support for the http method (MSN over HTTP)](https://bugs.launchpad.net/ubuntu/+source/telepathy-butterfly/+bug/392195)

Do I somehow confirm the bug (change it from new to confirmed?)

---

