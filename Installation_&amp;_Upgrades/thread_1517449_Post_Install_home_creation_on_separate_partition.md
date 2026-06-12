---
title: "Post Install /home creation on separate partition"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by coolboarderguy on 2010-06-25
DOH, looks like I missed defining a /home dir during installation. It's been a while ;-) I have a spare partition now that I'd really love to use. Can you specify this still, or is it only allowed during an install? Thanks.

---

### Post by kalistona on 2010-06-25
**you** do not define at the install because [B]it is defined when you install !
can you defined it after ?[/B] i do not think so but if you want, you can re-install and, when a place for home on g parted is asked or done **...you can choose with the mouse how many **[COLOR=Blue]go[/COLOR]** you give it** (at least [COLOR=Blue]1 go[/COLOR] for home).
best is built swap and home and free space with gparted[COLOR=Red] before [/COLOR]and install iso on.
that is not for beginners, but you can try several times, the fourth should be perfect !
try again...

---

### Post by lechien73 on 2010-06-25
If you mean that you want to move your /home directory to another partition after installation, then yes - you can:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

This gives detailed instructions on how to move your home partition to another drive.

---

### Post by coolboarderguy on 2010-06-30
> **lechien73 said:**
> If you mean that you want to move your /home directory to another partition after installation, then yes - you can:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

This gives detailed instructions on how to move your home partition to another drive.

Fantastic stuff, worked a treat!!! Thanks.

---

