---
title: "Root access granted in recovery mode"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Saprissa on 2010-04-27
When evaluating the RC for Lucid today, I encountered an error with plymouth.

When I booted to recovery mode from grub, and dropped to a shell environment I had root access without being prompted to enter a password.  Is this normal?

Started x and I had access to everything.

This doesn't seem right, but I am not super experienced.

Can anyone confirm and if so, file a bug report?

I'm online all day if I can provide more information.

---

### Post by int on 2010-04-27
it's normal..

You have to put one password to the grub.

[http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

---

### Post by Saprissa on 2010-04-27
> **int said:**
> it's normal..

You have to put one password to the grub.

[http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)

Okay.  Good to know.

:)

---

### Post by aysiu on 2010-04-27
You actually don't have to put a password on Grub... or a root password.

Physical access is root access.

The same can be done on any Mac (hold down Cmd-S during bootup, and you get a root prompt).

This allows you to recover Ubuntu easily (free up space if your hard drive is completely full, reset your user password if you forgot it).

---

### Post by VMC on 2010-04-27
> **aysiu said:**
> You actually don't have to put a password on Grub... or a root password.

Physical access is root access.

The same can be done on any Mac (hold down Cmd-S during bootup, and you get a root prompt).

This allows you to recover Ubuntu easily (free up space if your hard drive is completely full, reset your user password if you forgot it).

Exactly. This topic comes up in one form or another. Usually its Keyring security. Which is false security. If someone has physical access to my computer, they can do pretty much anything.

---

### Post by StuartN on 2010-04-27
I notice a slight inconsistency in user permissions - the first user, created during installation, is a member of sambashare but not a member of fuse. Subsequent users are created as members of fuse but not sambashare.

In the Users and Groups application these are rights to Mount user-space filesystems (FUSE) and Share files with the local network.

---

### Post by aysiu on 2010-04-27
> **StuartN said:**
> I notice a slight inconsistency in user permissions - the first user, created during installation, is a member of sambashare but not a member of fuse. Subsequent users are created as members of fuse but not sambashare.

In the Users and Groups application these are rights to Mount user-space filesystems (FUSE) and Share files with the local network. Sounds like a bug report in the making.

---

