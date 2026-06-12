---
title: "chroot"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-08
Anyone know how to change the software sources or change the server in chroot?

---

### Post by taavikko on 2009-10-08
> **Sashin said:**
> Anyone know how to change the software sources or change the server in chroot?

Edit "/etc/apt/sources.list"
To point to server you desire.
Main server is at: deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

---

### Post by Sashin on 2009-10-08
I can't use gksudo gedit in chroot.

---

### Post by taavikko on 2009-10-08
> **Sashin said:**
> I can't use gksudo gedit in chroot.

use nano "sudo nano <file>"
Ctrl+o saves
Ctrl+x exits editor

---

