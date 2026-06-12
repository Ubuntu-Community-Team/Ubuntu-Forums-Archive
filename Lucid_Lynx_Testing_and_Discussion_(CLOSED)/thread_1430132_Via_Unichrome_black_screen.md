---
title: "Via Unichrome black screen"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brimondyl on 2010-03-15
Like the post says.. If I type blindly I can login, I've tried F2 and F7 but no help it stays black. Any ideas? isnt there a safe graphics mode besides nomodetest (because that does nothing)

---

### Post by davidryderuk on 2010-03-15
Do you mean the "xforcevesa" option? 

Also, in case you haven't found it yet, there seems to be a bug report on this particular issue: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518623)

---

### Post by NCLI on 2010-03-15
Sounds a lot like [my bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507196"). Adding nomodeset to the list of GRUB startup commands should let you through.

---

### Post by brimondyl on 2010-03-23
nomodeset does nothing.... Plug in monitor to laptop and that works.

NCLI exactly the same as yours

---

