---
title: "latest Updates, admin password not accepted in session"
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-07-13
I can log in normally at GDM with my password, but if attempt to open synaptic or BUM, the system says wrong password.

Password is accepted in the terminal with 'sudo' however.

Anyone else ?

---

### Post by wayne_cat on 2009-07-13
edit: sorry ... wrong thread

---

### Post by Regenweald on 2009-07-13
Seems like my problem is the exact opposite of Zika's. I'll wait for more feedback.

---

### Post by nhasian on 2009-07-13
I too can log in successfully with my password, but i'm not able to to do anything that requires sudo privileges like update-manager, plugging in a USB hard disk, even shutting down the computer.

i'm not sure which package would cause this error but there is a bug about it:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/398934](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/398934)

---

### Post by Regenweald on 2009-07-13
I believe an update to gnome-keyring just fixed it. If I'm wrong let me know.

---

### Post by Slug71 on 2009-07-13
Yep, seems fixed.

---

### Post by dino99 on 2009-07-14
work properly now  ):P

---

