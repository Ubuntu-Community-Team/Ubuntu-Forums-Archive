---
title: "Problem with installing programmes"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by christopher.mountford on 2009-12-19
I have recently run into a problem with installing software to my computer, recently i had to wipe my computer due to a duel boot partitioning problem so i decided to just install Ubuntu and forget about XP but ever since i re-installed Ubuntu on a clean system it has been refusing to allow me to install from the software centre and synaptics manager, every time i try to install a new programme it only gets up to 3% then pops up with a "package dependencies could not be resolved" message. anyone have any ideas on how to solve this problem? any help would be greatly appreciated

---

### Post by lloyd_b on 2009-12-19
> **christopher.mountford said:**
> I have recently run into a problem with installing software to my computer, recently i had to wipe my computer due to a duel boot partitioning problem so i decided to just install Ubuntu and forget about XP but ever since i re-installed Ubuntu on a clean system it has been refusing to allow me to install from the software centre and synaptics manager, every time i try to install a new programme it only gets up to 3% then pops up with a "package dependencies could not be resolved" message. anyone have any ideas on how to solve this problem? any help would be greatly appreciated

Try opening a terminal window, and running "sudo apt-get dist-upgrade".  This may resolve the problem, and if it doesn't it should provide some helpful information as to exactly *what* dependency is causing the problems.

Lloyd B.

---

### Post by christopher.mountford on 2009-12-21
Cant say its worked, but thanks for the help anyway.

---

### Post by christopher.mountford on 2009-12-21
Sorry I take that back it appears it has worked after all ^^ thank you very much I really appreciate the help.

---

