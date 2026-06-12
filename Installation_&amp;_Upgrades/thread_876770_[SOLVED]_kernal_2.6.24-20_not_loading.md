---
title: "[SOLVED] kernal 2.6.24-20 not loading"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by soloman498 on 2008-08-01
When I start my computer kernal 2.6.24-20 generic says it is starting up but after 5 minutes it has not loaded.I then restart my computer and use kernal 2.6.24-19 and it loads straight away.any help would be appreciated:confused:

---

### Post by Sef on 2008-08-01
> When I start my computer kernal 2.6.24-20 generic says it is starting up but after 5 minutes it has not loaded.I then restart my computer and use kernal 2.6.24-19 and it loads straight away.any help would be appreciated

-20 is buggy on your system.  Stick with -19.  If I locate the way to change it, so -19 is the default kernel, I will post it.

---

### Post by Malac on 2008-08-01
> **Sef said:**
> -20 is buggy on your system.  Stick with -19.  If I locate the way to change it, so -19 is the default kernel, I will post it.
You can edit the /boot/grub/menu.lst file and add savedefault to the -19 kernel or just change this
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
```

But frankly -20 is in the proposed repo and if you don't know what you are doing this should not be activated.
Change it in Software Sources by unticking the hardy proposed check box.

Hope this helps.

---

### Post by abn91c on 2008-08-01
install startup-manager from the repositories, it will let you set up which kernel you want to use to run ubuntu

---

