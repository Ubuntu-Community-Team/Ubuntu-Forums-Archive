---
title: "Daily Build, zsync?"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SpinningAround on 2010-04-12
I don't understand what *.iso.zync is for or how to use it. Let say I want to test a daily build how do I do?

---

### Post by ratcheer on 2010-04-12
Ok, to use zsync you have to already have a copy of the image you want to sync up to. For example, if you downloaded the Daily Live CD last week, and you want to make it current as of now, run this command (or, make it a script) while in the directory where your base image is located:

```

zsync http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.iso.zsync

```

It takes a few minutes, but much less than downloading the full iso, again.

Tim

---

