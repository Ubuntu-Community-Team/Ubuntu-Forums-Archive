---
title: "Error message when doing updates..."
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by deanplays on 2010-03-29
Hello,

I'm really hoping someone can lend me their expertise.  I've recently started using Ubuntu and love it!  However, I was recently trying to do the ubuntu updates (equivolent to windows updates), and I got his with these errors:

E: dpkg was interrupted, you mush manually run 'sudo dpkg --configure -a' to correct the problem.

E:-cache->open()failed, please report

Has anyone run across this error message, and if so, how to fix it?  I'm not a programmer and just want to get the updates on my OS.  I'd sure appreciate anyone's help.

Thanks again!  :D

---

### Post by the yawner on 2010-03-29
Just open up a terminal and type the following:
```

sudo dpkg --configure -a

```
Then enter your password. I suppose, this happened because a previous update/installation was interrupted.

---

### Post by deanplays on 2010-03-29
Hey Yawner!!!

Thanks SOOOOO much buddy.  It worked!!!  You're the best.  I really appreciate it.

:popcorn:

---

### Post by krainey2106 on 2010-03-30
I have had the same problem, but the ¨$sudo dpkg --configure -a¨ does not solve the problem.  In the terminal I get an endless stream of:

Found linux image: /boot/vmlinuz-2.6.31-15generic-pae

Is there any way I can fix this short of reinstalling 9.10?

---

