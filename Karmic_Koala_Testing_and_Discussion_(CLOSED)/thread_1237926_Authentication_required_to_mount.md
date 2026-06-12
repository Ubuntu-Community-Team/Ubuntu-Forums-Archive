---
title: "Authentication required to mount"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2009-08-11
I'm getting this whenever I login. It seems to want my password to mount one of my drives. Previously this would all have been done automatically, so I'm not sure what's changed.

---

### Post by kingborel on 2009-08-11
You should search the forums and LP, there are numerous threads and bug reports about this already. It's being worked on.

---

### Post by Enigmatic on 2009-08-11
A search didn't return anything, but good to know.

---

### Post by wayne_cat on 2009-08-11
> **Enigmatic said:**
> A search didn't return anything, but good to know.

subscribe to one of these bug reports:

[https://bugs.edge.launchpad.net/ubuntu/+source/devicekit-disks/+bug/396448](https://bugs.edge.launchpad.net/ubuntu/+source/devicekit-disks/+bug/396448)

[https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122](https://bugs.edge.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/395122)

---

### Post by bacardiandwatermelon on 2009-08-12
Use pysdm to manage your drives and it should stop asking for authentication..

---

### Post by Paqman on 2009-08-12
> **bacardiandwatermelon said:**
> Use pysdm to manage your drives and it should stop asking for authentication..

Nope, tried that one myself.

---

### Post by bacardiandwatermelon on 2009-08-12
Did you set any user can mount drive in the assistant?

---

### Post by Paqman on 2009-08-12
The bug is such that you'll get the authentication prompt even for drives that aren't supposed to be automounted.

---

