---
title: "Root Password????"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by PCalitrack on 2006-08-07
I just successfully installed Ubunut on a dual-boot system. However, I realized that the installed never asked for a root password... only my user password. Now, when I type su, I have no clue what my password is for the superuser/root. Any help? I imagine this is a common thing.

---

### Post by sethmahoney on 2006-08-07
> **PCalitrack said:**
> I just successfully installed Ubunut on a dual-boot system. However, I realized that the installed never asked for a root password... only my user password. Now, when I type su, I have no clue what my password is for the superuser/root. Any help? I imagine this is a common thing.

Yeah, it trips a lot of users up. Ubuntu doesn't by default use a root account, so sudo/su/gksudo just uses your user password.

---

### Post by Talisker on 2006-08-07
I have the same problem....

wenn I use the terminal and try to login as su - it asks for my password. After entering my user password the shell tells me "su: Authentication failure
Sorry."

How do I log in as root?

Thanks

---

### Post by aysiu on 2006-08-07
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Talisker on 2006-08-07
Perfect, I was looking for that. That explains it...:o 

Thanks!

---

### Post by randell6564 on 2006-08-07
Hi!

Well when I do a 'sudo' yada,yada, I just enter my user password and that works. But when I want to log in as root, i have a different password that i use.

Strange.

---

### Post by aysiu on 2006-08-07
> **randell6564 said:**
> Hi!

Well when I do a 'sudo' yada,yada, I just enter my user password and that works. But when I want to log in as root, i have a different password that i use.

Strange.
That's the way it's supposed to work, because you're not really supposed to log in as root.

*sudo* enables users who belong to the *admin* group to temporarily assume root privileges--it does not log them in as root.

---

### Post by randell6564 on 2006-08-07
> **aysiu said:**
> That's the way it's supposed to work, because you're not really supposed to log in as root.

*sudo* enables users who belong to the *admin* group to temporarily assume root privileges--it does not log them in as root.

Yeah, thats what I thought, but i thought that was what the op was having an issue with.  My bad!  I got 'su' mixed up with 'sudo'  (either too much wine or not enough! lol!)

---

### Post by randell6564 on 2006-08-07
> **aysiu said:**
> That's the way it's supposed to work, because you're not really supposed to log in as root.

*sudo* enables users who belong to the *admin* group to temporarily assume root privileges--it does not log them in as root.

Yeah, thats what I thought, but i thought that was what the op was having an issue with.  My bad!  I got 'su' mixed up with 'sudo'  (either too much wine or not enough! lol!)

---

