---
title: "reuse existing /home on seperate partition"
date: 2014-02-22
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2014-02-22
Installing 64 bit 13.10
I formated out the partition where the old OS was.
Installed set to /
Reboot and get my new 13.10 with a new home.

How do I reuse the old /home on the other partition?
So I wiped the os partition again and waiting for an answer.

If I click the desired partition, I get no option to use it for /home
I have done this before. I thought the old /home partition would give an option to use it as /home?
pic

---

### Post by sdowney717 on 2014-02-22
ok, I found it, you have to select the journaling system first, then you can set the mount point.

---

### Post by oldfred on 2014-02-25
Just be sure not to tick the format option. 
But you do have to mount or choose to use the existing /home as part of the install.

---

