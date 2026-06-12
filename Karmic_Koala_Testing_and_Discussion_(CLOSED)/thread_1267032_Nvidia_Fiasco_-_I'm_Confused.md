---
title: "Nvidia Fiasco - I'm Confused"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by alligoodw on 2009-09-15
After reading all the posts, it's apparent that something went horribly wrong with a recent update that occurred a few days ago; I happen to be amongst those effected.  

**My current situation is as follows**:  I'm booting into Karmic via the "NV" workaround that many have employed. My resolution is very low but it's workable. I am confused though.  Should I be using the **Envy** program that I've always used for Nvidia drivers, or should I be using the drivers found under the MAIN Menu in Karmic? I can't think of what you call those drivers in Ubuntu (I'm using Windows right now).  

My question is, is which set of Nvidia drivers should I be using?

---

### Post by gradinaruvasile on 2009-09-15
> **alligoodw said:**
> After reading all the posts, it's apparent that something went horribly wrong with a recent update that occurred a few days ago; I happen to be amongst those effected.  

**My current situation is as follows**:  I'm booting into Karmic via the "NV" workaround that many have employed. My resolution is very low but it's workable. I am confused though.  Should I be using the **Envy** program that I've always used for Nvidia drivers, or should I be using the drivers found under the MAIN Menu in Karmic? I can't think of what you call those drivers in Ubuntu (I'm using Windows right now).  

My question is, is which set of Nvidia drivers should I be using?

From Nvidia's site... Those work usually.

---

### Post by cyberkilla on 2009-09-15
An update to libc6 (or something like that) caused the NVidia drivers to break, making infinite loops as X started.

I had this issue this morning, as did a few others.

The fixed package is in the repository now, so it's worth getting everything updated.

FYI, the mirror server I was using was out of date. If you want the most recent stuff, it looks like you'll be best served to select the main server.

This is, of course, assuming your problem only just appeared.

---

### Post by psyke83 on 2009-09-15
> **gradinaruvasile said:**
> From Nvidia's site... Those work usually.

That's not the right answer for someone who needs to ask that question. If you manually install the drivers from NVIDIA's site, you are bypassing Ubuntu's package management, and each kernel upgrade will cause the driver to break.

Quite simply, you should use the official packages in our repository. The "Restricted Drivers Manager" is a convenient front-end to install the correct driver version (as NVIDIA supports a different range of cards based on the driver version). However, all the integration is based within the actual Ubuntu packages (for instance, using DKMS to automatically compile the NVIDIA kernel module when a kernel is installed).

By the way, I don't think that Envy/EnvyNG is used anymore. If I recall correctly, the same author maintains the official Ubuntu driver packages.

---

### Post by xebian on 2009-09-15
> **cyberkilla said:**
> An update to libc6 (or something like that) caused the NVidia drivers to break, making infinite loops as X started.

I had this issue this morning, as did a few others.

The fixed package is in the repository now, so it's worth getting everything updated.

FYI, the mirror server I was using was out of date. If you want the most recent stuff, it looks like you'll be best served to select the main server.

This is, of course, assuming your problem only just appeared.

I think something else is broken because I update daily and not had an issue at all.  The issue also seems not to be global, only a few does.

BTW I used direct NV dirvers not from the repo so it may have helped.

---

### Post by alligoodw on 2009-09-15
I've resolved this problem.  The problem was resolved in additional updates. Now I've got to fix the problem with the NetWorkManager not working.

---

