---
title: "how to restore user accounts after clean install?"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by smilingfrog on 2009-12-14
I just upgraded from 9.04 to 9.10 on my desktop.
I did a clean install onto a new partition, and everything is up and running. I keep my /home folder on a separate partition.
However, I have two users in my home folder, and I can no longer access the second user. I tried adding the user via system tools, but it tells me that the /home/user folder is taken, and to add a different name.

How do I regain access to this folder so I can log onto it?

---

### Post by fancypiper on 2009-12-14
Move the user directory to another name such as old.user, create the user, move the user directory back and make sure the new user owns that directory.
```
sudo chown -R <user>.<user> /home/<user>
```

---

### Post by darkod on 2009-12-14
Adding a user with existing home folder:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308767](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308767)

---

### Post by smilingfrog on 2009-12-14
Thanks for the help.
What is you want to keep the username and password from a previous installation, and you don't want to create a new user. Is there anyway of importing this?

---

### Post by darkod on 2009-12-14
> **smilingfrog said:**
> Thanks for the help.
What is you want to keep the username and password from a previous installation, and you don't want to create a new user. Is there anyway of importing this?

I'm not sure I understand. You're creating the same username as it was, and nothing is stopping you setting the same password. That's the only procedure I know to assign old users to existing home folders after clean install.

---

