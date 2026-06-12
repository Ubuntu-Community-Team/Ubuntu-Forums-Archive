---
title: "How do I modify my GRUB menu ?"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rick Abraham on 2009-09-15
Hi I recently upgraded from Ubuntu 9.04 to 9.10 Karmic Koala.
When my PC restarted after the upgrade it wouldnt boot and it gave me a black screen.
I restarted the PC again and went into the GRUB menu and I noticed that there are 2 different kernel's there.
I selected the second kernel on the list 2.6.28-15 and the PC booted up fine into 9.10.
I dont know why this has happened.
But is it possible to delete the kernel that doesnt work from the GRUB menu, due to that kernel is first on the list and the PC seems to boot that one automatically.
Here is what my GRUB menu looks like.

Ubuntu Karmic (development branch) kernel 2.6.31-9 generic
Ubuntu Karmic (development branch) kernel 2.6.31-9 (recovery ->
Ubuntu Karmic (development branch) kernel 2.6.28-15 generic
Ubuntu Karmic (development branch) kernel 2.6.28-15 (recovery ->

Any help would be great.

---

### Post by overdrank on 2009-09-15
Hi and you can edit your menu list but since you are using 9.10 Karmic Koala I am moving the thread to Karmic Koala Testing and Discussion :)

---

### Post by VMC on 2009-09-15
> **Rick Abraham said:**
> Hi I recently upgraded from Ubuntu 9.04 to 9.10 Karmic Koala.
When my PC restarted after the upgrade it wouldnt boot and it gave me a black screen.
I restarted the PC again and went into the GRUB menu and I noticed that there are 2 different kernel's there.
I selected the second kernel on the list 2.6.28-15 and the PC booted up fine into 9.10.
I dont know why this has happened.
But is it possible to delete the kernel that doesnt work from the GRUB menu, due to that kernel is first on the list and the PC seems to boot that one automatically.
Here is what my GRUB menu looks like.

Ubuntu Karmic (development branch) kernel 2.6.31-9 generic
Ubuntu Karmic (development branch) kernel 2.6.31-9 (recovery ->
Ubuntu Karmic (development branch) kernel 2.6.28-15 generic
Ubuntu Karmic (development branch) kernel 2.6.28-15 (recovery ->

Any help would be great.

I would use the newer kernel. The problem may be that you unfortunately upgrade during this time we had a lot of upgrade trouble.

Can you get into recovery mode?

---

### Post by abouzar on 2009-09-15
You can check the following link: 
[http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html](http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html)

> **Rick Abraham said:**
> Hi I recently upgraded from Ubuntu 9.04 to 9.10 Karmic Koala.
When my PC restarted after the upgrade it wouldnt boot and it gave me a black screen.
I restarted the PC again and went into the GRUB menu and I noticed that there are 2 different kernel's there.
I selected the second kernel on the list 2.6.28-15 and the PC booted up fine into 9.10.
I dont know why this has happened.
But is it possible to delete the kernel that doesnt work from the GRUB menu, due to that kernel is first on the list and the PC seems to boot that one automatically.
Here is what my GRUB menu looks like.

Ubuntu Karmic (development branch) kernel 2.6.31-9 generic
Ubuntu Karmic (development branch) kernel 2.6.31-9 (recovery ->
Ubuntu Karmic (development branch) kernel 2.6.28-15 generic
Ubuntu Karmic (development branch) kernel 2.6.28-15 (recovery ->

Any help would be great.

---

