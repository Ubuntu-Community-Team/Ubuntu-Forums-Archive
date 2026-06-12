---
title: "How do I*get rid of password requests to mount usb drives?"
date: 2009-07-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tawmas on 2009-07-08
Hi people!

It's some time now that I'm being requested a password to mount USB drives. So my basic question is:*how do I*go about getting rid of the password prompt? I tried granting myself a bunch of policykit permissions related to removable media and disk mounting, but to no avail.

Also, is this by design or just a temporary glitch?

---

### Post by wayne_cat on 2009-07-08
so you already did this:

[https://answers.launchpad.net/ubuntu/+question/30501](https://answers.launchpad.net/ubuntu/+question/30501)

and the problem is still there? ... maybe this helps:

System>>preferences>>Startup Applications>> Uncheck - PolicyKit authentication agent

---

### Post by tawmas on 2009-07-08
> **wayne_cat said:**
> so you already did this:

[https://answers.launchpad.net/ubuntu/+question/30501](https://answers.launchpad.net/ubuntu/+question/30501)

and the problem is still there? ...

I didn't try that. Actually, I'm not really sure it's related to what I'm trying to achieve, that is automount enabled and no password prompt.

Secondarily, I'm also trying to understand if it's a bug or meant behaviour (not that would make that less of a bug, just a tougher one to get rid of).

---

### Post by dinxter on 2009-07-08
sounds like [this bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/386699") on devicekit-disks, i get it too

---

### Post by xebian on 2009-07-08
I don't see this problem but it could be your devicekit as dinxter said above as I don't have devicekit installed.  BTW I use KDE

---

### Post by tawmas on 2009-07-09
> **dinxter said:**
> sounds like [this bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/386699") on devicekit-disks, i get it too

Thank you, I subscribed to that bug. Hope it will get squashed soon!

---

